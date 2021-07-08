### [[Previous Step|Step 9]]

# Demo

Now that we have built the solution, we'll demo it in SharePoint Online. These solutions are designed to work in SP 2013 and SharePoint Online Classic Pages only. For modern pages, you will need to use a SPFx project. Make sure you view the site in "Classic Mode".

## Copy Assets

Copy the ```assets\index.html``` & ```sp-dashboard.js``` files to the site assets 'sp-dashboard' sub-folder.

## Install the Solution

### Load the Library

Press F-12 to access the browser's console. Type the following into the console:

```
var s = document.createElement("script"); s.src = "/sites/dev/siteassets/sp-dashboard/sp-dashboard.js"; document.head.appendChild(s);
```

This will load our library and make the ```SPDashboard``` global variable available.

### Create the List

Create the list and test data.

```
SPDashboard.Configuration.install();
```
_Note - Wait for the list installation to complete, before generating the test data._

_Note - If you are using IE, the 'Promise' library will need to be included. Reference the [webpack configuration](https://gunjandatta.github.io/dev/webpack) documentation for additional details._

![wiki/images/installSolution.png|alt=install solution]

## Add WebPart to Page

Create a blank webpart page, edit it and add this webpart to it.

![wiki/images/addWebPart.png|alt=add webpart]

After the page refreshes, edit the configuration and select the test list we created.

![wiki/images/wpConfiguration.png|alt=webpart configuration]

Save the webpart, wait for the page to refresh and close the page to view the list data.

![wiki/images/viewListTable.png|alt=view list table]

## Uninstall the solution

To uninstall the solution, simply run the following command below. This will remove the SharePoint assets (list for this example).

```
WPList.Configuration.uninstall();
```

### [[Next Step|Step 11]]