### [[Previous Step|Step 6]]

# Filter (src/dashboard/filter.ts)

- Initialization
  - Save the properties
  - Render the filter
- Card
  - Reference the [Bootstrap documentation](https://getbootstrap.com/docs/4.4/components/card/) for details of the card component.
  - Render within a card to give an outline to the filter
- Checkbox
  - Reference the [Bootstrap documentation](https://getbootstrap.com/docs/4.4/components/forms/#checkboxes-and-radios) for details of the checkbox component.
  - Set the "Inline" property to render them as a row
  - Create items for each choice defined in the ```src/cfg.ts``` file for the ```Status``` field
  - Set the type to be a ```Switch```
  - Set the ```onChange``` event to call this filter's change event in its properties

```ts
import { Components } from "gd-sprest-bs";

// Filter Properties
export interface IFilterProps {
    el: HTMLElement;
    onChange: (value: string) => void;
}

/**
 * Filter
 */
export class Filter {
    private _props: IFilterProps = null;

    // Constructor
    constructor(props: IFilterProps) {
        // Save the parameters
        this._props = props;

        // Render the filter
        this.render();
    }

    // Render the filter
    private render() {
        // Render a card
        Components.Card({
            el: this._props.el,
            body: [
                {
                    onRender: (el) => {
                        // Render checkboxes
                        Components.CheckboxGroup({
                            el,
                            isInline: true,
                            type: Components.CheckboxGroupTypes.Switch,
                            items: [
                                { label: "Draft" },
                                { label: "Submitted" },
                                { label: "Rejected" },
                                { label: "Pending Approval" },
                                { label: "Approved" },
                                { label: "Archived" }
                            ],
                            onChange: (item: Components.ICheckboxGroupItem) => {
                                // Call the change event
                                this._props.onChange(item ? item.label : "");
                            }
                        });
                    }
                }
            ]
        });
    }
}
```

### [[Next Step|Step 8]]