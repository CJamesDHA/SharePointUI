### [[Previous Step|Step 11]]

# Create SPFx Project

## Create the Project Folder

Create the project folder, and navigate to it in your console. Below is the command to create the project.

```
yo @microsoft/sharepoint
```

Enter the following options: _(Use default option if not displayed below)_

* Solution Name: **sp-dashboard**
* Target Baseline: **SharePoint Online only (latest)**
* Location of Files: **Use the current folder**
* Type of Solution: **WebPart**
* Name of Web Part: **Dashboard**
* WebPart Description: 
* Framework: **No JavaScript Framework**

## Create Clean-Up Script

The clean-up script will delete the SPFx package solution.

### ./clean.js

```js
const path = require("path");
const project = require("./package.json");
const fs = require("fs");

// Get the spfx package
const srcFile = path.join(__dirname, "dist/" + project.name + ".sppkg");

// See if it exists
if (fs.existsSync(srcFile)) {
    // Delete the file
    fs.unlinkSync(srcFile);

    // Log
    console.log("Deleted the SPFx package");
} else {
    // Log
    console.log("SPFx package doesn't exist");
}
```

## Update Build Process

### ./package.json

Update the main package.json build process to include the SPFx solution.

```json
{
    "scripts": {
        "all": "npm run clean && npm run build && npm run prod && npm run spfx",
        "build": "webpack --mode development",
        "clean": "node ./clean.js",
        "prod": "webpack --mode production",
        "spfx": "cd spfx && npm run package"
    },
}
```

### spfx/package.json

Update the SPFx package.json build process to include a package option.

```json
{
    "scripts": {
        "build": "gulp bundle",
        "clean": "gulp clean",
        "package": "gulp clean && gulp build --ship && gulp bundle --ship && gulp package-solution --ship",
        "test": "gulp test"
    },
}
```

## Update the SPFx Configuration

### spfx/config/package-solution.json

Update the location of the package.

```
"paths": {
  "zippedPackage": "../../dist/sp-dashboard.sppkg"
}
```

### [[Next Step|Step 13]]