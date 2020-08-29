### [[Previous Step|Step 4]]

# Dashboard

### Template (src/dashboard/template.html)

Set the dashboard template to include a navigation, filter and table element.

```html
<div>
    <div class="row">
        <div id="navigation" class="col"></div>
    </div>
    <div class="row">
        <div id="filter" class="col mb-4"></div>
    </div>
    <div class="row">
        <div id="table" class="col"></div>
    </div>
</div>
```

### Code (src/dashboard/index.ts)

- Initialization
  - Create the dashboard element using the html template
  - Render the dashboard
- Navigation
  - Pass the navigation element to the component
  - Define the onSearch event to pass the value to the table component
- Filter
  - Pass the filter element to the component
  - Define the onFilter event to pass the value to the table component
- Table
  - Pass the table element to the component

```ts
import { Filter } from "./filter";
import { Navigation } from "./navigation";
import { Table } from "./table";
import * as HTML from "./template.html";
import "./styles.css";

/**
 * Dashboard
 */
export class Dashboard {
    private _el: HTMLElement = null;

    /**
     * Renders the project.
     * @param el - The element to render the dashboard to.
     */
    constructor(elParent: HTMLElement) {
        // Create the element
        let el = document.createElement("div");
        el.innerHTML = HTML as any;
        this._el = el.firstChild as HTMLElement;

        // Append it to the parent element
        elParent.appendChild(this._el);

        // Render the dashboard
        this.render();
    }

    /**
     * Main render method
     * @param el - The element to render the dashboard to.
     */
    private render() {
        // Render the navigation
        new Navigation({
            el: this._el.querySelector("#navigation"),
            onSearch: value => {
                // Search the table
                table.search(value);
            }
        });

        // Render the filter
        new Filter({
            el: this._el.querySelector("#filter"),
            onFilter: value => {
                // Filter the table data
                table.filter(value);
            }
        });

        // Render the table
        let table = new Table(this._el.querySelector("#table"));
    }
}
```

### [[Next Step|Step 6]]