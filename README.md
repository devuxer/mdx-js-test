# Minimal example for Create React App + craco + mdx-js

Steps to create your own project:

1. `npx create-react-app mdx-js-test` (replace `mdx-js-test` with your project's name)
2. `npm install @mdx-js/loader @mdx-js/mdx craco @jackwilsdon/craco-use-babelrc`
3. `./craco.config.js`:
   ```
   module.exports = {
     webpack: {
       configure: webpackConfig => {
         const oneOfRules = webpackConfig.module.rules.find(x => !!x.oneOf).oneOf;
         oneOfRules.unshift({
           test: /\.mdx?$/,
           use: ["babel-loader", "@mdx-js/loader"]
         });
         webpackConfig.node.fs = "empty";
         return webpackConfig;
       }
     }
   };
   ```
4. `./src/index.js`:

   ```
   import React from "react";
   import ReactDOM from "react-dom";
   import Hello from "./hello.mdx";
   import "./index.css";
   import * as serviceWorker from "./serviceWorker";

   ReactDOM.render(<Hello />, document.getElementById("root"));

   // If you want your app to work offline and load faster, you can change
   // unregister() to register() below. Note this comes with some pitfalls.
   // Learn more about service workers: https://bit.ly/CRA-PWA
   serviceWorker.unregister();
   ```

5. `./src/hello.mdx`:

   ```
   # Hello, MDX!

   This is an example using webpack
   ```

6. `./.babelrc`:
   ```
   {
   "presets": [
       [
       "@babel/env",
       {
           "corejs": 2,
           "useBuiltIns": "usage"
       }
       ],
       "@babel/react"
   ],
   "plugins": ["macros"]
   }
   ```
7. `npm start`

You should see:

> # Hello, MDX!
>
> This is an exmaple using webpack
