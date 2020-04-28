# Setting up project using Webpack and Babel

Easy setup for projects that involve newer versions of JavaScript using Webpack and Babel.

## First

Create a package.json file for installations

```bash
npm init
```

## Installation

Install node modules as dev dependencies

```bash
npm install --save-dev webpack webpack-dev-server webpack-cli @babel/preset-env @babel/core babel-loader
```

## Scripts

In the "scripts" object in the package.json file, add these.
"build" will compile and bundle your ES-whatever down to ES5
```bash
"build": "webpack",
"start": "webpack-dev-server --output-public-path=/dist/"
```

## Webpack Config

Create a webpack.config.js file in the root directory and put this in:

```bash
const path = require("path");

module.exports = {
    entry: {
        app: "./src/index.js"
    },
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    },
    mode: "development",
    module: {
        rules: [{
            test: /\.js?$/,
            exclude: /node_modules/,
            loader: "babel-loader",
            query: {
                presets: ["@babel/preset-env"]
            }
        }]
    }
}
```

## File Creations

After making a webpack config file, create a directory called src and then a file named "index.js" in the src folder.

Create an HTML file in the root directory and in the script tags, make sure to use file in the dist folder for production.

```bash
<script src="./dist/bundle.js"></script>
```

## Making it work

Now just run: 
```bash
npm start
```
And it should compile successfully, and you can see your results at http://localhost:8080/ 