### [[Previous Step|Step 7]]

# Custom Styling (src/styles.scss)

We will create a custom file for styling the solution.

```scss
/** Custom Styles Go Here */
```

# Main Entry (src/index.ts)

The main entry point of the project.

- Import the styles
- Render the application if the application element id is found
- Global Variable
    - Configuration - Used to install/uninstall the solution
    - render - Reference for the SPFx/Teams project
- Use "Installation Required" component to determine if an installation is required
    - Displays a modal dialog to execute the Configuration's installation through the GUI

```ts
import { InstallationRequired } from "dattatable";
import { App } from "./app";
import { Configuration } from "./cfg";
import { DataSource } from "./ds";
import Strings, { setContext } from "./strings";

// Styling
import "./styles.scss";

// Create the global variable for this solution
const GlobalVariable = {
    Configuration,
    render: (el, context?, sourceUrl?: string) => {
        // See if the SPFx page context exists
        if (context) {
            // Set the context
            setContext(context, sourceUrl);
        }

        // Initialize the application
        DataSource.init().then(
            // Success
            () => {
                // Create the application
                new App(el);
            },

            // Error
            () => {
                // See if an installation is required
                InstallationRequired.requiresInstall(Configuration).then(installFl => {
                    // See if an install is required
                    if (installFl) {
                        // Show the dialog
                        InstallationRequired.showDialog();
                    } else {
                        // Log
                        console.error("[" + Strings.ProjectName + "] Error initializing the solution.");
                    }
                });
            }
        );
    }
};

// Make is available in the DOM
window[Strings.GlobalVariable] = GlobalVariable;

// Get the element and render the app if it is found
let elApp = document.querySelector("#" + Strings.AppElementId) as HTMLElement;
if (elApp) {
    // Render the application
    GlobalVariable.render(elApp);
}
```

### [[Next Step|Step 9]]