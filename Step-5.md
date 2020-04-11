### [[Previous Step|Step 4]]

# Dashboard

### Template (src/dashboard/index.html)

The dashboard will 

```html
<div class="row">
    <div id="navigation"></div>
    <div id="filter"></div>
    <div id="table"></div>
</div>
```

### Code (src/dashboard/index.ts)

```ts
/**
 * Global Constants
 */
export default {
    // The element id in assets/index.html
    AppElementId: "project-app",

    // Referenced by src/index.ts to set the global variable
    GlobalVariable: "MyProject",

    // Referenced as needed
    ProjectName: "Project",

    // Referenced as needed
    ProjectDescription: "Created using the gd-sprest-bs library.",

    // Referenced by the src/cfg.ts to set the content editor webpart link url
    SolutionUrl: "/sites/dev/siteassets/sprest-bs-starter/index.html"
}
```

#### AppElementId

This property must match the element id defined in the ```assets/index.html``` file.

#### SolutionUrl

This property must match the location the ```assets/index.html, dist/[project name].js``` files are stored in SharePoint. This is the ```ContentLink``` property of the content editor webpart installed by this solution.

### [[Next Step|Step 6]]