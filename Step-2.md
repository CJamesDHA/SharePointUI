### [[Previous Step|Step 1]]

# Configure Project

### Package Configuration (package.json)

#### 1) Update the Project Name

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