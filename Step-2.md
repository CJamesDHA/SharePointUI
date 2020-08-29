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
   - datatables.net-bs4
- url-loader
   - Required to bundle the css reference from datatables.net-dt

Run the following commands to install the libraries.

```
npm i --save datatables.net datatables.net-bs4
npm i --save-dev url-loader
```

### WebPack Configuration

The datatables.net-bs4 css file will require the url-loader in order to bundle the images into the output file. Add the following to the module rules array.

```js
// Handle Image Files
{
  test: /\.(jpe?g|png|gif|svg)$/,
  use: "url-loader"
}
```

### Update Global Variables (src/strings.ts)

The last file to update is the global constants. We will be referencing them in later code files.

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

_The solution url must match your environment._

### [[Next Step|Step 3]]