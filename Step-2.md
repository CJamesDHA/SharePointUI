### [[Previous Step|Step 1]]

# Configure Project

We will go over the configuration files, which will be used to compile and bundle our solution into a single javascript file.

## Update the Project Configuration (./package.json)

We will update the project's configuration (package.json) file, which was created in the previous step. Find the "scripts" property and define the build and prod commands, to execute webpack to bundle the solution. The build command will bundle the raw JS, so we can debug the code. The prod command will minify the output.

```
"scripts": {
  "build": "webpack --mode=development",
  "prod": "webpack --mode=production"
}
```

## Create the Configuration Files

### TypeScript (./tsconfig.json)

Refer to [typescript's documentation](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) for an overview of the configuration file. In VS Code, create a file called ```tsconfig.json``` in the root folder.

```
{
    "compilerOptions": {
        "lib": [
            "dom",
            "es2015"
        ],
        "target": "es5"
    },
    "include": [
        "src/**/*"
    ]
}
```

### Webpack (./webpack.config.js)

Refer to [webpack's documentation](https://webpack.js.org/configuration/) for an overview of the configuration file. In VS Code, create a file called ```webpack.config.js``` in the root folder. To simplify the configuration and limit the 3rd party libraries, we will reference the distribution file of the gd-sprest-bs library and use the "externals" property to define the library references. This library contains Bootstrap (full css + js), gd-sprest, and jQuery.

```
var project = require("./package.json");
var path = require("path");

// Return the configuration
module.exports = (env, argv) => {
    var isDev = argv.mode !== "production";
    return {
        // Set the main source as the entry point
        entry: [
            path.resolve(__dirname, project.main)
        ],

        // Output location
        output: {
            path: path.resolve(__dirname, "dist"),
            filename: project.name + (isDev ? "" : ".min") + ".js"
        },

        // Resolve the file names
        resolve: {
            extensions: [".js", ".css", ".scss", ".ts"]
        },

        // Dev Server
        devServer: {
            inline: true,
            hot: true,
            open: true,
            publicPath: "/dist/"
        },

        // Loaders
        module: {
            rules: [
                // SASS to JavaScript
                {
                    // Target the sass and css files
                    test: /\.s?css$/,
                    // Define the compiler to use
                    use: [
                        // Create style nodes from the CommonJS code
                        { loader: "style-loader" },
                        // Translate css to CommonJS
                        { loader: "css-loader" },
                        // Compile sass to css
                        { loader: "sass-loader" }
                    ]
                },
                // Handle Image Files
                {
                    test: /\.(jpe?g|png|gif|svg|eot|woff|ttf)$/,
                    loader: "url-loader"
                },
                // TypeScript to JavaScript
                {
                    // Target TypeScript files
                    test: /\.tsx?$/,
                    exclude: /node_modules/,
                    use: [
                        // JavaScript (ES5) -> JavaScript (Current)
                        {
                            loader: "babel-loader",
                            options: { presets: ["@babel/preset-env"] }
                        },
                        // TypeScript -> JavaScript (ES5)
                        { loader: "ts-loader" }
                    ]
                }
            ]
        }
    };
}
```

### [[Next Step|Step 3]]