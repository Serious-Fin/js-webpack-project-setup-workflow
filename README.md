# Full JavaScript project setup using WebPack
## Initial setup
Enambe npm in current terminal instance
```
nvm use node
```
Initialize webpack in an empty directory
```
npm init -y
```
Install webpack and webpack-cli locally
```
npm install webpack webpack-cli --save-dev
```
Create a .gitignore file and add ```node_modules/``` folder to it
```
touch .gitignore
```
Create a src/ and dict/ directories with:
* index.js in src/
* index.html in dist/ with a simple boilerplate
* webpack.config.js in root

In the webpack.config.js file add the following configuration:
```
const path = require('path');

module.exports = {
  entry: {
    index: './src/index.js'
  },
  output: {
    filename: '[name].bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

In package.json add the following line under "scripts":
```
"build": "webpack",
"watch": "webpack --watch"
```

In ```webpack.config.js``` add the follwoing line to ```module.exports```:
```
mode: 'development',
```

Now run ```npm run build``` or ```npm run watch``` to build you application.

**Now would be the perfect time to setup a git repository and push the initial setup.**

## Adding CSS support

Install the following module via provided console command:
```
npm install --save-dev style-loader css-loader
```

Update ```webpack.config.js``` file to look like this:
```
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'bundle.js',
     path: path.resolve(__dirname, 'dist'),
   },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
 };
```

To use css just add a ```style.css``` file to ```src/``` directory and import it to a JavaScript file via ```import './style.css'```

## Using **HtmlWebpackPlugin** to manage JavaScript modules 
This plugin automatically adds all of the JS modules to HTML template on build
Run the following command in the console:
```
npm install --save-dev html-webpack-plugin
```
Add the following code to ```webpack.config.js -> module.exports```:
```
plugins: [
    new HtmlWebpackPlugin({
      title: 'Output Management',
      template: './src/index.html',
      filename: 'index.html',
    }),
  ],
```
And this to the root of the ```webpack.config.js``` file:
```
const HtmlWebpackPlugin = require('html-webpack-plugin');
```
Add a 'template' as ```./src/index.html``` for the HtmlWebpackPlugin to use.

To remove clutter from ```dist/``` folder add te following to ```webpack.config.js -> module.exports -> output```:
```
clean: true,
```
