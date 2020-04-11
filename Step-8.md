### [[Previous Step|Step 7]]

# Table (src/dashboard/table.ts)

- Initialization
  - Save the element to render the table to
  - Load the display form url from the list defined in the ```src/cfg.ts``` file
  - Render the table after the url has been retrieved
- Table
  - Display the ```Title``` field value as a button
  - Display the item's display form when the button is clicked
  - Display the ```ItemType``` and ```Status``` fields
- Methods
  - clear - Removes the table element
  - load - Loads the list display form
  - loadItems
    - If a filter value is specified then the list query for items where the ```Status``` matches
- Public Methods
  - applyFilter - Calls the render event passing the value from the filter component
  - search - Calls the datatables.net search method passing the value form the navbar search textbox
```ts
```

### [[Next Step|Step 9]]