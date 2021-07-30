### [[Previous Step|Step 6]]

# Main Application (src/app.ts)

The main application class.

- Initialization
    - Sets the list name for the item form
    - Loads the list data
    - Loads the dashboard filters
    - Renders the application
- Render - Renders the dattatable dashboard
    - Configuration
        - hideHeader - Hides the header jumbotron
        - rows - The list data items
        - useModal - Flag to show the item forms in a modal and not a canvas slideout
        - filters - Allows for the status to be filtered
        - navigation - Ability to create an item
        - footer - Displays the version #
        - dtProps - The datatables.net properties
        - columns - The column information for the table

```ts
import { Dashboard, ItemForm } from "dattatable";
import { Components } from "gd-sprest-bs";
import * as jQuery from "jquery";
import { DataSource, IItem } from "./ds";
import Strings from "./strings";

/**
 * Main Application
 */
export class App {
    // Constructor
    constructor(el: HTMLElement) {
        // Set the list name
        ItemForm.ListName = Strings.Lists.Main;

        // Initialize the application
        DataSource.init().then(() => {
            // Render the dashboard
            this.render(el);
        });
    }

    // Renders the dashboard
    private render(el: HTMLElement) {
        // Create the dashboard
        let dashboard = new Dashboard({
            el,
            hideHeader: true,
            useModal: true,
            filters: {
                items: [{
                    header: "By Status",
                    items: DataSource.StatusFilters,
                    onFilter: (value: string) => {
                        // Filter the table
                        dashboard.filter(2, value);
                    }
                }]
            },
            navigation: {
                title: Strings.ProjectName,
                items: [
                    {
                        className: "btn-outline-light",
                        text: "Create Item",
                        isButton: true,
                        onClick: () => {
                            // Create an item
                            ItemForm.create({
                                onUpdate: () => {
                                    // Load the data
                                    DataSource.load().then(items => {
                                        // Refresh the table
                                        dashboard.refresh(items);
                                    });
                                }
                            });
                        }
                    }
                ]
            },
            footer: {
                itemsEnd: [
                    {
                        text: "v" + Strings.Version
                    }
                ]
            },
            table: {
                rows: DataSource.Items,
                dtProps: {
                    dom: 'rt<"row"<"col-sm-4"l><"col-sm-4"i><"col-sm-4"p>>',
                    columnDefs: [
                        {
                            "targets": 0,
                            "orderable": false,
                            "searchable": false
                        }
                    ],
                    // Add some classes to the dataTable elements
                    drawCallback: function () {
                        jQuery('.table', this._table).removeClass('no-footer');
                        jQuery('.table', this._table).addClass('tbl-footer');
                        jQuery('.table thead th', this._table).addClass('align-middle');
                        jQuery('.table tbody td', this._table).addClass('align-middle');
                        jQuery('.dataTables_info', this._table).addClass('text-center');
                        jQuery('.dataTables_length', this._table).addClass('pt-2');
                        jQuery('.dataTables_paginate', this._table).addClass('pt-03');
                    },
                    // Order by the 1st column by default; ascending
                    order: [[1, "asc"]]
                },
                columns: [
                    {
                        name: "",
                        title: "Title",
                        onRenderCell: (el, column, item: IItem) => {
                            // Render a buttons
                            Components.ButtonGroup({
                                el,
                                buttons: [
                                    {
                                        text: item.Title,
                                        type: Components.ButtonTypes.OutlinePrimary,
                                        onClick: () => {
                                            // Show the display form
                                            ItemForm.view({
                                                itemId: item.Id
                                            });
                                        }
                                    },
                                    {
                                        text: "Edit",
                                        type: Components.ButtonTypes.OutlineSuccess,
                                        onClick: () => {
                                            // Show the edit form
                                            ItemForm.edit({
                                                itemId: item.Id,
                                                onUpdate: () => {
                                                    // Refresh the data
                                                    DataSource.load().then(items => {
                                                        // Update the data
                                                        dashboard.refresh(items);
                                                    });
                                                }
                                            });
                                        }
                                    }
                                ]
                            });
                        }
                    },
                    {
                        name: "ItemType",
                        title: "Item Type"
                    },
                    {
                        name: "Status",
                        title: "Status"
                    }
                ]
            }
        });
    }
}
```

### [[Next Step|Step 8]]