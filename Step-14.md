### [[Previous Step|Step 13]]

# Demo

## Trust Certificate

The following command **MUST** be run the first time: ```gulp trust-dev-cert```

## Build App Package

From the root of the project, run the ```npm run all``` command to build all solutions.

### Upload the App Package

[[wiki/imagesaddSPFxPackage.png|alt=add spfx package]]

Deploy the solution

[[wiki/imagesdeploySolution.png|alt=deploy solution]]

### Add App to Site

Go to the site we previously deployed the solution to access the site contents. Click on "Add" then select "App" from the menu. Select the SPFx solution we just deployed.

[[wiki/imagesaddAppToSite.png|alt=add app to site]]

### Add the WebPart

Click on the "+" button to add a webpart.

[[wiki/imagesaddSPFxWebPart.png|alt=add spfx webpart]]

Select the "Dashboard" and the solution will be displayed.

[[wiki/imagesviewSPFxWebPart.png|alt=view table]]

Save and publish the page. Click on the "Create" or "Edit" button to view the list form.

[[wiki/imageseditForm.png|alt=edit item form]]