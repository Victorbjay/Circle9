![image](https://github.com/user-attachments/assets/ac79a489-be1b-4234-86ba-75e5d4d94dff)---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# JavaScript Summary from Circle 9

_A Tinyuka Production_<br>
Presentation slides by:
<br>

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
    Press Space for next page <carbon:arrow-right />
  </div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Team Players

- Paul
- Wafaqah
- Tolu
- Victor
- Kaycee
- Gbolahan
- Iyin
- Victoria
- Ibrahim

---

# Table of Content

<Toc text-sm minDepth="1" maxDepth="2" />

---

# JavaScript Functions

Function is a block of reusable code that can perform a particular task, it can take in parameters and it's value(argument) also return a value, arrays and objects.

Below are codes examples of how functions are used to perform tasks:

```js {monaco-run}
function greetUser() {
  alert("you are welcome");
}

greetUser();
```

---

## Ways of declaring a function

## 1. Function Declaration:

It is the widely and default way of declaring a function and the exciting thing here is that it can be called before defining it.

```js {monaco-run}
//Remember: The 'name' is a parameter and it accepts a value called argument.
greet("chioma");

function greet(name) {
  console.log(`Welcome back ${name}!!`);
}
//Output; Welcome back Chioma!!
```

---

## 2. Functions Expression:

It is defined as a value and assigned to a variable, it can not be called before defining it.

```js
let greet = function (name) {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

## 3. Arrow Function:

This was introduced in ES6 and it can be defined without the function keyword and also assigned to a variable and the essential thing is
that the parameters and function body is seperated by "=>". it is very easy, short and handy to code with😊

```js {monaco-run}
let greet = (name) => {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

---

## Callbacks

A **Callback function** is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of action.

The execution may be immediate as in synchronous callback and it might happen later as in asynchronous callback. Callbacks allows you to reuse functions in flexible way.

```js {monaco-run}
function greet(name, callback) {
  console.log("Hi " + name);
  callback(); // calling the callback function
}

function sayBye() {
  console.log("Bye!");
}

greet("Alice", sayBye);
```

Here, sayBye is passed as a callback to greet

---
# Promises

## WHAT IS A PROMISE?

This is a neater way to handle asynchronous operations in java script.

## Why are promises a better alternative to callbacks?

In a case where several callbacks would be needed, callbacks would eventually become inefficient, make code less readablw and can lead to 'callback hell'. Promises are very useful for such situations.

---

## POSSIBLE PROMISE STATES
Promises can be in three states:
- Pending: this is the initial state, the asynchronous operation has not completed yet. Like waiting for a friend to call you back.
- Resolved: the asynchronous operation completed successfully and thus the promise has a resulting value. Your friend called back and gave you an answer.
- Rejected: the asynchronous operation failed. Your friend never called you back.

  ---
  
## PROMISE EXAMPLE AND FORMAT

```
const myPromise = new Promise((resolve, reject) => {
let success = true;

 if (success) {
resolve("Operation successful");
}
 else {
reject("Something went wrong"); }
}
);

myPromise
.then(result => console.log(result))     // If resolved
 .catch(error => console.error(error));   // If rejected 
```

- To invoke a promise the `new Promise` key word is used. It takes two parameters; `resolve` and `reject'. The resolve holds if the callback is successful and reject holds if it is not i.e there is an errror.

- The `.then' is used to handle successes. Each `.then()` returns a new promise, so you can chain multiple `.then() calls`.
- The `.catch()` handles errors. It catches errors that occur in the promise chain before it.

  ---


# JavaScript Bundlers 101

## What is a Bundler?

A **JavaScript bundler** takes many files and dependencies and combines them into one or a few optimized files that the browser can load efficiently.

## Why Use a Bundler?

- Fewer HTTP requests
- Easier code organization with modules
- Enables modern features like ES Modules, TypeScript, JSX
- Minifies and optimizes your code for production

---

## ES Modules vs CommonJS

### ES Module

```js {monaco-run}
// utils.js
export function greet(name) {
  return `Hello, ${name}`;
}

// main.js
import { greet } from "./utils.js";
console.log(greet("Alice"));
```

### CommonJS

```js {monaco-run}
// utils.js
function greet(name) {
  return `Hello, ${name}`;
}
module.exports = { greet };

// main.js
const { greet } = require("./utils.js");
console.log(greet("Bob"));
```

These code snippets demonstrate a common practice in JavaScript for organizing code into separate files and using modules to share functionality.

---

In essence:

`utils.js` creates a reusable function (greet) and makes it available to other files. `main.js` then `imports` this function and uses it to print a greeting. This modular approach helps keep code organized and makes it easier to manage larger projects.

# How Bundlers Work (Simplified)

1. Start from an entry file
2. Build a dependency graph
3. Combine all modules
4. Minify and optimize
5. Output to `/dist` folder

---

# Popular Bundlers

- **Webpack** – Powerful, customizable, but complex
- **Parcel** – Zero config, beginner friendly
- **Vite** – Lightning fast, ESM-based dev server
- **esbuild** – Super fast, minimal setup

---

# Webpack Example

```js {monaco-run}
// webpack.config.js
module.exports = {
  entry: "./src/index.js", // where your app starts
  output: {
    filename: "bundle.js", // the output bundle file name
    path: __dirname + "/dist", // the output folder (absolute path)
  },
  mode: "development", // or 'production'
};
```

_This is a basic Webpack configuration file_.

---

# Parcel Example

### File: src/utils.js

```js {monaco-run}
export function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}
```

### File: src/greet.js

```js {monaco-run}
import { capitalize } from "./utils.js";
export function greet(name) {
  return `Hello, ${capitalize(name)}!`;
}
```

### File: src/index.js

```js {monaco-run}
import { greet } from "./greet.js";
console.log(greet("world"));
```

---

## HTML Entry (index.html)

```html {monaco-run}
<!DOCTYPE html>
<html>
  <head>
    <title>Parcel App</title>
  </head>
  <body>
    <script src="./dist/bundle.js" defer></script>
  </body>
</html>
```

---

## Parcel Commands

```bash
npm install --save-dev parcel
npx parcel index.html
```

## Vite Quick Start

```bash
npm create vite@latest my-app
cd my-app
npm install
npm run dev
```

## esbuild Quick Start

```bash
npm install --save-dev esbuild
npx esbuild src/index.js --bundle --minify --outfile=dist/bundle.js
```

---

## Summary

- Use Parcel or Vite for easy, fast setups
- Use Webpack if you need advanced configuration
- Use esbuild for raw speed and simplicity

Happy bundling! 🎉
