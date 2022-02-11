### [[Previous Step|Step 12]]

# Copy Assets

## spfx/src/webparts/Dashboard/DashboardWebPart.ts

### Reference the Library

We will reference the classic solution's library.

```
// Reference the solution
import "../../../../dist/sp-dashboard.min.js";
declare var SPDashboard;
```

#### Render Method

* Load Data - Load the list data.
  * Set Page Context - In order for the $REST library to execute successfully, the page context will need to be set.
  * Set the Source Url - We will manually set the location of where the solution is deployed.
* Render the Table - After loading the data, render the table.

```
public render(): void {
    // Render the application
    SPDashboard.render(this.domElement, this.context, "/sites/dev");
}
```

### [[Next Step|Step 14]]