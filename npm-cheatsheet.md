# NPM Package Cheatsheet

An opinionated (but fairly general) guide to important NPM packages to install when setting up a CRUD app using React and Express.

_Unless otherwise noted, each package can be installed as such: `npm install NAME`_

## Table of Contents

[Back End](#Back-End)

- [Express Setup](#Express-Setup)
- [OPTIONAL Express Packages](#OPTIONAL-Express-Packages)

- [Database Setup](#Database-Setup)
  - [PostgreSQL](#PostgreSQL)
  - [MongoDB](#PostgreSQL)

[Front End](#Front-End)

- [React Setup](#React-Setup)
  - [Webpack](#Webpack)
  - [OPTIONAL for Webpack](#optional-for-webpack)
  - [React](#React)
  - [OPTIONAL for React](#React)
- [Redux Setup](#redux-setup)
- [OPTIONAL for Redux](#optional-for-redux)

## Back End

### Express Setup

- [**express**](https://expressjs.com/)
- [**cookie-parser**](https://www.npmjs.com/package/cookie-parser)
  - Parses cookie header and populates req.cookies with an object keyed by the cookie names.
- [**nodemon**](https://www.npmjs.com/package/nodemon) _(dev dependency)_
  - Restarts server after any changes are made, unlike the standard `node` command, which does not respond to changes made after running.
  - Use in your `start` script like so: `nodemon server.js`
  - Not strictly necessary, but will greatly improve your efficiency as a developer.
- [**bcrypt** ](https://www.npmjs.com/package/bcrypt)
  - Popular authentication tool for hashing and verifying passwords (and other information)
  - Feel free to use other authentication solutions like [Passport.js](https://www.npmjs.com/package/passport)
- Note: [body-parser](https://www.npmjs.com/package/body-parser) is deprecated. The [`json`](http://expressjs.com/en/api.html#express.json) and [`url-encoded`](http://expressjs.com/en/5x/api.html#express.urlencoded) functionality can be performed with native Express methods:
  ```javascript
  app.use(express.urlencoded({ extended: true }));
  app.use(express.json());
  ```

#### OPTIONAL Express Packages

- [**concurrently**](https://www.npmjs.com/package/concurrently)
  - Used to run multiple npm commands simultaneously.
  - Not necessary in UNIX-like environment (e.g. Macs), which can chain commands with & (run all commands in parallel) or && (waits for the previous command to finish before running)
- [**dotenv**](https://www.npmjs.com/package/dotenv)
  - Loads environmental variables from a .env file into process.env
  - Useful for keeping private info (e.g. API keys) out of public repos
  - Usage example:
    - Store an API key as a variable in `.env`.
    - Add `.env` to your `.gitignore` file so the file isn’t added to your repo.
    - With dotenv installed, you can access that API key variable by referencing `process.env`, e.g. `process.env.VARIABLE`

### Database Setup

#### PostgreSQL

- [**node-postgres**](https://node-postgres.com/)
  - **Note: install with `npm install pg`!**
  - Lets node.js (and Express) interact with a PostgreSQL database

#### MongoDB

- [**mongoose**](https://mongoosejs.com/)
  - Robust wrapper for MongoDB that handles validation, casting, and business logic boilerplate.
  - One of Mongoose's central features is its ability to create schemas for MongoDB collections.

## Front End

### React Setup

You can ignore this section if you're using `create-react-app`!

#### Webpack

Install all webpack-related packages as _dev dependencies_.

- [**webpack**](https://webpack.js.org/)
- [**webpack-cli**](https://www.npmjs.com/package/webpack-cli)
  - Webpack's official CLI (command line interface), providing access to many convenient commands, such as creating a new webpack configuration or migrating a project from one version to another.
- [**webpack-dev-server**](https://www.npmjs.com/package/webpack-dev-server)
  - Provides a development server for webpack, complete with live reloading
  - Recommended NPM script: `"start:dev": "webpack-dev-server"`
- [**@babel/core**](https://babeljs.io/docs/en/next/babel-core.html)
  - Babel compiler core
- [**@babel/preset-env**](https://babeljs.io/docs/en/next/babel-preset-env.html)
  - A smart preset that lets you use the lastest JavaScript features without worrying about which syntax transforms and browser polyfills your target environments require.
- [**@babel/preset-react**](https://babeljs.io/docs/en/next/babel-preset-react.html)
  - A Babel preset for all React plugins
- [**babel-loader**](https://www.npmjs.com/package/babel-loader)
  - Lets you transpile files using Babel & Webpack
- [**css-loader**](https://www.npmjs.com/package/css-loader)
  - Interprets `@import` and `url()` in CSS files
- [**style-loader**](https://www.npmjs.com/package/style-loader)
  - Injects CSS into the DOM

#### OPTIONAL for Webpack

- [sass-loader](https://www.npmjs.com/package/sass-loader)
  - Loads Sass/SCSS files and compiles them to CSS.
  - Only necessary if you're using Sass... which you should probably use.

#### React

- [**react**](https://reactjs.org/)
- [**react-dom**](https://www.npmjs.com/package/react-dom)
  - Serves as the entry point to the DOM and service renderers for React. Should be paired with the generic `react` package above.

#### OPTIONAL for React

- [**react-router-dom**](https://www.npmjs.com/package/react-router-dom)
  - Performs client-side routing without the need to contact the server.
  - Lets you use React Router in a web setting (`react-router-native` is also available for React Native).
  - Read more on the [official site](https://reacttraining.com/react-router/).
- node-sass
  - Natively and automatically compiles .scss files to CSS.
  - Lets you directly use .scss files in React, which is awesome.

### Redux Setup

- [**redux**](https://redux.js.org/)
- [**react-redux**](https://react-redux.js.org/)
  - Note that it's necessary to also install the React-specific version of Redux, since Redux can be used with a variety of frameworks — and even Vanilla JS.

### OPTIONAL for Redux

_Note:_ Both Thunk and Saga are used to let Redux perform asynchronous actions. You can choose one or the other, although Thunk is by far the more popular option.

**For Redux Thunk:**

- [**redux-thunk**](https://www.npmjs.com/package/redux-thunk)

  - [An in-depth introduction to thunks in Redux](http://stackoverflow.com/questions/35411423/how-to-dispatch-a-redux-action-with-a-timeout/35415559#35415559)

**For Redux Saga:**

- [**redux-saga**](https://redux-saga.js.org/)

  - From the [official site](https://redux-saga.js.org/): "You might've used `redux-thunk` before to handle your data fetching. Contrary to redux thunk, you don't end up in callback hell, you can test your asynchronous flows easily and your actions stay pure."

_These packages may be required for Redux saga to function properly:_

- [**regenerator-runtime**](https://www.npmjs.com/package/regenerator-runtime)
  - Standalone runtime for [Regenerator](https://github.com/facebook/regenerator)-compiled generator and `async` functions
- [**core-js**](https://www.npmjs.com/package/core-js)
  - Modular standard library for JavaScript
