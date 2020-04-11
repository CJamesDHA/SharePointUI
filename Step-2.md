### [[Previous Step|Step 1]]

# Configure Project

### Update Project Name

Update the ```./package.json``` "name" property to the project name. This name will be referenced as the output file for the solution.

```js
{
  // Referenced by webpack.config.js as the output filename.
  "name": "sp-dashboard"
}
```

### Add Libraries

We will be using the following libraries:

- Datatables.net
   - datatables.net
   - datatables.net-dt
- url-loader
   - Required to bundle the css reference from datatables.net-dt

```
npm i --save datatables.net datatables.net-dt
npm i --save-dev url-loader
```

### Update Global Variables (src/strings.ts)

```ts
/**
 * Global Constants
 */
export default {
    AppElementId: "sp-dashboard",
    GlobalVariable: "SPDashboard",
    Lists: {
        Main: "Dashboard"
    },
    ProjectName: "SP Dashboard",
    ProjectDescription: "A basic dashboard.",
    SolutionUrl: "/sites/dev/siteassets/sp-dashboard/index.html"
}
```

### [[Next Step|Step 3]]