### [[Previous Step|Step 3]]

# Main File

- We will need to configure the datatables.net library
   - Reference [this blog post](https://dattabase.com/blog/typescript-and-datatables.net) for additional details
- Define the global variable for this solution to make the configuration available
- Get the element referenced in ```assets/index.html``` and render the dashboard to it

### Main Source (src/index.ts)

```ts
import { Configuration } from "./cfg";
import { Dashboard } from "./dashboard";
import Strings from "./strings";

// Ensure the data tables plugin is configured
import * as DataTable from "datatables.net";
import { jQuery } from "gd-sprest-bs";
import "datatables.net-dt/css/jquery.dataTables.min.css";

// See if jQuery is defined in the DataTable lib
if (DataTable.prototype.constructor.$ == undefined) {
    // Set the reference
    DataTable.prototype.constructor.$ = jQuery;
} else {
    // Update this jQuery reference for this library
    window["$REST"].jQuery = DataTable.prototype.constructor.$;
}

// Create the global variable for this solution
window[Strings.GlobalVariable] = {
    Configuration
}

// Get the main element to render the solution to
let el = document.getElementById(Strings.AppElementId);
if (el) {
    // Initialize the dashboard
    new Dashboard(el);
} else {
    // Log
    console.log("[" + Strings.ProjectName + "] Error finding the element with id '" + Strings.AppElementId + "'");
}
```

### [[Next Step|Step 5]]