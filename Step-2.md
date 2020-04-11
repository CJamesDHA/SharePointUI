### [[Previous Step|Step 1]]

# Configure Project

### Update Project Name

Update the ```./package.json``` "name" property to the project name. This name will be referenced as the output file for the solution.

```js
{
  // Referenced by webpack.config.js as the output filename.
  "name": "sp-dashboard"
}
```

#### 2) Add Libraries

We will be using the following libraries:

- Datatables.net
   - datatables.net
   - datatables.net-dt
- url-loader
   - Required to bundle the css reference from datatables.net-dt

```
npm i --save datatables.net datatables.net-dt
npm i --save-dev url-loader
```

### [[Next Step|Step 3]]