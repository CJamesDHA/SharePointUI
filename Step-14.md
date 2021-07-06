### [[Previous Step|Step 13]]

# Demo

## Trust Certificate

The following command **MUST** be run the first time: ```gulp trust-dev-cert```

## Build and Host the Solution

To build the solution, simply run ```gulp serve --nobrowser```. This will allow us to test the webpart in the local workbench. Reference the [SharePoint Documentation](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/build-a-hello-world-web-part#preview-the-web-part-in-sharepoint) for additional information on this.

## View WebPart

This solution uses the same list we created. If you uninstalled it, please re-install the list with the test data. Access the workbench by accessing ```https://[tenant].sharepoint.com/_layouts/15/workbench.aspx```.

### Add the WebPart

Click on the "+" button to add a webpart.

[[https://github.com/gunjandatta/sp-listwebpart/blob/master/images/addSPFxWebPart.png|alt=add spfx webpart]]

Select the "ListWebPart" and the table will be displayed.

[[https://github.com/gunjandatta/sp-listwebpart/blob/master/images/viewListTableSPFxWP.png|alt=view table]]

Clicking on "Edit" will display the edit form.

[[https://github.com/gunjandatta/sp-listwebpart/blob/master/images/editItemFormSPFx.png|alt=edit item form]]