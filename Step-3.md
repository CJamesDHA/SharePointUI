### [[Previous Step|Step 2]]

# SharePoint Assets

### Configuration (src/cfg.ts)

We will use the SharePoint Configuration helper class to create a list for the dashboard to store data in.

- Fields
  - Item Type - A required choice field with a defaulted value.
  - Status - A required choice field, that is not displayed in the new form.
- Views
  - Update the default view to include the custom fields.
- Methods
  - addToPage - Adds a content editor library and configures it to point to the dashboard solution.

```ts
import { Helper, SPTypes } from "gd-sprest-bs";
import Strings from "./strings";

/**
 * SharePoint Assets
 */
export const Configuration = Helper.SPConfig({
    ListCfg: [
        {
            ListInformation: {
                Title: Strings.Lists.Main,
                BaseTemplate: SPTypes.ListTemplateType.GenericList
            },
            CustomFields: [
                {
                    name: "ItemType",
                    title: "Item Type",
                    type: Helper.SPCfgFieldType.Choice,
                    defaultValue: "Type 3",
                    required: true,
                    choices: [
                        "Type 1", "Type 2", "Type 3", "Type 4", "Type 5"
                    ]
                } as Helper.IFieldInfoChoice,
                {
                    name: "Status",
                    title: "Status",
                    type: Helper.SPCfgFieldType.Choice,
                    defaultValue: "Draft",
                    required: true,
                    showInNewForm: false,
                    choices: [
                        "Draft", "Submitted", "Rejected", "Pending Approval",
                        "Approved", "Archived"
                    ]
                }
            ],
            ViewInformation: [
                {
                    ViewName: "All Items",
                    ViewFields: [
                        "LinkTitle", "ItemType", "Status"
                    ]
                }
            ]
        }
    ]
});

// Adds the solution to a classic page
Configuration["addToPage"] = (pageUrl: string) => {
    // Add a content editor webpart to the page
    Helper.addContentEditorWebPart(pageUrl, {
        contentLink: Strings.SolutionUrl,
        description: Strings.ProjectDescription,
        frameType: "None",
        title: Strings.ProjectName
    }).then(
        // Success
        () => {
            // Load
            console.log("[" + Strings.ProjectName + "] Successfully added the solution to the page.", pageUrl);
        },

        // Error
        ex => {
            // Load
            console.log("[" + Strings.ProjectName + "] Error adding the solution to the page.", ex);
        }
    );
}
```

### [[Next Step|Step 4]]