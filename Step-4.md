### [[Previous Step|Step 3]]

# Static Variables (src/strings.ts)

This file contains the static data for the project, which is referenced by the other code. The `setContext` method is for SPFx/Teams solutions. The `context` information is used to update the REST API library, to ensure we can execute requests to it. The `sourceUrl` is optional, when the solution is not in the same web where the solution is deployed.

```ts
import { ContextInfo } from "gd-sprest-bs";

// Sets the context information
// This is for SPFx or Teams solutions
export const setContext = (context, sourceUrl?: string) => {
    // Set the context
    ContextInfo.setPageContext(context.pageContext);

    // Update the source url
    Strings.SourceUrl = sourceUrl || ContextInfo.webServerRelativeUrl;
}

/**
 * Global Constants
 */
const Strings = {
    AppElementId: "sp-dashboard",
    GlobalVariable: "SPDashboard",
    Lists: {
        Main: "Dashboard"
    },
    ProjectName: "SP Dashboard",
    ProjectDescription: "Created using the gd-sprest-bs library.",
    SolutionUrl: "/sites/dev/siteassets/sp-dashboard/index.html",
    SourceUrl: ContextInfo.webServerRelativeUrl,
    Version: "0.1"
};
export default Strings;
```

### [[Next Step|Step 5]]