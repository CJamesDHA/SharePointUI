### [[Previous Step|Step 14]]

# Deploy to Teams

To enable the solution to be made available in Teams, simply update the manifest file.

## spfx/src/webparts/listWebPart/DashboardWebPart.manifest.json

Update the `supportedHosts` property to include `TeamsTab`.

```json
{
  "supportedHosts": ["SharePointWebPart", "TeamsTab"],
}
```

### Deployment Options: TeamsTab vs TeamsPersonalApp

A `TeamsTab` will allow the user to add the tab to inside a Team channel. A `TeamsPersonalApp` will allow the user to add the app to the main sidebar.

### Skip Feature Deployment (spfx/config/package-solution.json)

To deploy a solution to Teams, you must set the `skipFeatureDeployment` option to `true`. This will allow the solution to be deployed at the tenant level, which is required to sync to Teams. If you do not set this option, then the `Sync to Teams` option will not be available.

### Increment the Version (spfx/config/package-solution.json)

Increment the `version` number from `0.0.0.1` to `0.0.0.2`. Since the solution is already deployed to the app catalog, we will need to increment the version in order to upgrade the existing solution in the app catalog.

### Rebuild the Package

From the root of the project, run the ```npm run all``` command to build all solutions.

### Upload the App Package

Upload the new package and re-deploy the solution.

![update spfx package](/gunjandatta/sp-dashboard/wiki/images/updateSPFxPackage.png)

![deploy to tenant](/gunjandatta/sp-dashboard/wiki/images/deployToTenant.png)

### Sync to Teams

Select the app package and click on the `Files` ribbon tab. Click on the `Sync to Teams` option to make the app available in Teams.

![sync to teams](/gunjandatta/sp-dashboard/wiki/images/syncToTeams.png)

### Deploy to Teams

Access the Teams app or in the web browser. Click on the `...` ellipsis and select `More apps`.

![sync to teams](/gunjandatta/sp-dashboard/wiki/images/teamsMoreApps.png)

This may take a little time, but refresh after a couple minutes if you do not see the `Build for your org` option under `Apps`.

![built for your org](/gunjandatta/sp-dashboard/wiki/images/teamsBuiltForYourOrg.png)

Once you see your app deployed, click on it to view the app information. Next, click on the `Add to a team` option to add it to an existing team channel.

![add to team](/gunjandatta/sp-dashboard/wiki/images/addToTeam.png)

Search for the target team channel to deploy the app to. Click on `Set up a tab` to complete the request.

![add to team](/gunjandatta/sp-dashboard/wiki/images/selectATeam.png)

Lastly, view the tab to confirm the dashboard app is available in the selected team channel.

![view in teams](/gunjandatta/sp-dashboard/wiki/images/viewInTeams.png)