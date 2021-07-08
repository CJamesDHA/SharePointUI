# Create Project

We will be using [Node Package Manage](https://www.npmjs.com/) to manage our libraries.

### Create the project

Create the project folder, and navigate to it in your console. Below is the command to create the project. We will use "--y" to auto-select the default options.

```
npm init --y
```

![[wiki/images/createProject.png|alt=create project]]

### Download Libraries

Open the project in VS Code. Press ctrl+` to display the terminal, which will be used to install the libraries using npm.

#### Required for Solution

Below are a list of libraries required to render the dashboard solution.

* [dattatable](https://github.com/gunjandatta/dattatable)
    * [gd-sprest-bs](https://gunjandatta.github.io/extras/bs)
    * [moment](https://momentjs.com/)
* [datatables.net](https://datatables.net/)
    * [datatables.net-bs5](https://datatables.net/examples/styling/bootstrap5.html)
    * [jquery](https://jquery.com/)

```
npm i --save dattatable gd-sprest-bs moment datatables.net datatables.net-bs5 jquery
```
_The 'i' is for "install"_
_The '--save' will update the package.json file's "dependencies" property._

![[wiki/images/installDependencies.png|alt=install dependencies]]

#### Required for Packaging Solution

We will be using [webpack](https://webpack.js.org/) and [babel](https://babeljs.io/) to compile and bundle the solution. Below are a list of libraries required to bundle and package the solutions.

* [@babel/core](https://babeljs.io)
    * [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env)
* [webpack](https://webpack.js.org/)
    * [babel-loader](https://www.npmjs.com/package/babel-loader)
    * [css-loader](https://www.npmjs.com/package/css-loader)
    * [html-loader](https://www.npmjs.com/package/html-loader)
    * [node-sass](https://www.npmjs.com/package/node-sass)
    * [sass-loader](https://www.npmjs.com/package/sass-loader)
    * [style-loader](https://www.npmjs.com/package/style-loader)
    * [ts-loader](https://www.npmjs.com/package/ts-loader)
    * [webpack-cli](https://webpack.js.org/api/cli/)

```
npm i --save-dev @babel/core @babel/preset-env webpack webpack-cli babel-loader css-loader html-loader sass-loader style-loader ts-loader
```
_The '--save-dev' will update the package.json file's "devDependencies" property._

![[wiki/images/installDevDependencies.png|alt=install babel]]

### [[Next Step|Step 2]]