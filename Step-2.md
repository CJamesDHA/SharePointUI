### [[Previous Step|Step 1]]

# Configure Project

We will go over the configuration files, which will be used to compile and bundle our solution into a single javascript file.

## Update the Project Configuration (./package.json)

We will update the project's configuration (package.json) file, which was created in the previous step. Find the "main" property and update it to the main index file we will create later on. Find the "scripts" property and define the build and prod commands, to execute webpack to bundle the solution. The build command will bundle the raw JS, so we can debug the code. The prod command will minify the output.

```
"main": "src/index.ts",
"scripts": {
    "all": "npm run build && npm run prod",
    "build": "webpack --mode=development",
    "prod": "webpack --mode=production"
}
```

## Create the Configuration Files

### TypeScript (./tsconfig.json)

```json
{
    "compilerOptions": {
        "target": "es5",
        "lib": [
            "dom",
            "es2015"
        ]
    },
    "include": [
        "src/**/*"
    ]
}
```

### WebPack (./webpack.config.js)

```js
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