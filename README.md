# JavaScript project setup using WebPack

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
Create a .gitignore file and add node modules file to it
```
touch .gitignore
node_modules/
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
"build": "webpack"
"watch": "webpack --watch"
```

Now run ```npm run build``` or ```npm run watch``` to build you application.
