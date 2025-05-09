---
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

# Async & Await in JavaScript

Introduction to async & await

---

# What are async and await?

They are tools to handle asynchronous code in JavaScript in a clean, readable way — instead of using callbacks or .then() chains with Promises.

Think of async/await as a way to write asynchronous code that looks like synchronous code.

# Key Concepts

async makes a function return a Promise.

await pauses the execution of the async function until the Promise resolves.

---

## What is Asynchronous Code?

JavaScript is **single-threaded** — it can only do one thing at a time.

But with **asynchronous code**, JS can:

- Start a long-running task (e.g. API call)
- Continue with other code
- Come back when the task is finished

This prevents the app from **freezing** while waiting.

---

## Why Use `async` and `await`?

✅ Makes asynchronous code look like normal synchronous code  
✅ Easier to read, write, and debug than `.then()` chains  
✅ Simplified error handling using `try/catch`

---

## What is `async`?

Adding `async` before a function:

- Automatically makes it return a **Promise**

```js
async function greet() {
  return "Hello!";
}

// Equivalent to:
function greet() {
  return Promise.resolve("Hello!");
}
```

Usage:

```js
greet().then(console.log); // Logs: Hello!
```

---

## What is `await`?

You use `await` **inside an async function** to pause execution until a Promise resolves:

```js
function wait(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function showMessage() {
  console.log("Waiting...");
  await wait(2000); // Wait 2 seconds
  console.log("Done waiting!");
}

showMessage();
```

---

## Error Handling with try/catch

```js
async function getUserData() {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/users/1");
    const user = await res.json();
    console.log(user);
  } catch (err) {
    console.error("Something went wrong:", err);
  }
}

getUserData();
```

async function getUserData() — this is an asynchronous function.

fetch(...) — sends a network request to get user data (from a public API).

await res.json() — parses the response body as JSON.

All this is wrapped in a try { ... } catch { ... } block to catch errors like:
No internet,
Bad API URL,
JSON parsing issues etc

If an error happens in any await line, the code jumps to the catch block.

---

## Sequential vs Parallel `await`s

### Sequential (steps depend on each other):

```js
const userRes = await fetch("/user");
const user = await userRes.json();
const postsRes = await fetch(`/posts?userId=${user.id}`);
```

### Parallel (independent steps):

```js
const [usersRes, postsRes] = await Promise.all([
  fetch("/users"),
  fetch("/posts"),
]);
```

---

## Summary

| Feature       | Description                           |
| ------------- | ------------------------------------- |
| `async`       | Makes a function return a Promise     |
| `await`       | Waits for the Promise to resolve      |
| `try/catch`   | Handles async errors cleanly          |
| `Promise.all` | Runs multiple async tasks in parallel |

---

---

# theme: default

# https://sli.dev/custom/highlighters.html

highlighter: shiki

# show line numbers in code blocks

lineNumbers: true

# some information about the slides, markdown enabled

info: |

## JavaScript Modules Presentation

A comprehensive guide to JavaScript modules, imports, and exports.

# persist drawings in exports and build

drawings:
persist: false

# page transition

transition: slide-left

# use UnoCSS

## css: unocss

# JavaScript Modules

Understanding imports and exports in modern JavaScript

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
This is the title slide for our JavaScript Modules presentation.

Key points to mention in the introduction:
- JavaScript modules help organize code into reusable pieces
- ES Modules (ESM) is the standard format since ES2015
- We'll cover both basic and advanced module patterns
-->

---

# Introduction to Modules

<v-clicks>

- Modules help organize code into separate files
- ES Modules (ESM) is the official standard format (since ES2015)
- Files with import/export statements are treated as modules
- Modules have their own scope (not global)
- Modules are executed only once, even when imported multiple times

</v-clicks>

---

Additional notes:

<v-clicks>

- Before modules, developers used patterns like IIFEs and the revealing module pattern
- CommonJS is another module format used primarily in Node.js
- ES Modules work in both browsers and Node.js
- Modules help prevent naming conflicts and global scope pollution

</v-clicks>

---

# Default Exports & Imports

Default exports are useful when a module primarily provides one main piece of functionality.
The name used when importing can be different from the name used when exporting.

## Default Export

```js
// math.js
export default function add(a, b) {
return a + b;
}

// Alternative syntax
function multiply(a, b) {
return a \* b;
}

export default multiply;
```

<p class="text-sm opacity-75">Only one default export per module</p>

---

## Default Import

```js
// app.js
import add from "./math.js";

console.log(add(2, 3)); // 5

// You can use any name when importing
import mathFunction from "./math.js";

console.log(mathFunction(2, 3)); // 5
```

<p class="text-sm opacity-75">Import name can be different from export name</p>

---

# Named Exports & Imports

Named exports are ideal when a module provides multiple related functions, variables, or classes.
When importing, you must use the exact same names as the exports, unless you use aliases.
Named exports make it clear what functionality is being imported.

#### Named Exports

```js
// utils.js
export function add(a, b) {
return a + b;
}

export function subtract(a, b) {
return a - b;
}

export const PI = 3.14159;

// Alternative syntax
const multiply = (a, b) => a \* b;
const divide = (a, b) => a / b;

export { multiply, divide };

```

---

## Named Imports

```js
// app.js
import { add, subtract, PI } from "./utils.js";

console.log(add(5, 3)); // 8
console.log(subtract(5, 3)); // 2
console.log(PI); // 3.14159

// Import with alias
import { add as sum, PI as pi } from "./utils.js";

console.log(sum(5, 3)); // 8
console.log(pi); // 3.14159
```

<p class="text-sm opacity-75">Names must match exports (unless aliased)</p>

---

# Mixing Default & Named Exports

You can combine default and named exports in a single module.
When importing both the default and named exports, the default import comes first.

## Mixed Exports

```js
// calculator.js
export default class Calculator {
add(a, b) {
return a + b;
}

subtract(a, b) {
return a - b;
}
}

export const PI = 3.14159;
export const E = 2.71828;

export function square(x) {
return x \* x;
}
```

---

## Mixed Imports

```js
// app.js
import Calculator, { PI, square } from "./calculator.js";

const calc = new Calculator();
console.log(calc.add(5, 3)); // 8
console.log(PI); // 3.14159
console.log(square(4)); // 16

// Alternative syntax
import Calculator from "./calculator.js";
import { PI, square } from "./calculator.js";
```

<p class="text-sm opacity-75">Default import comes before named imports</p>

---

# Namespace Imports

Import all exports from a module as properties of an object:

```js
// utils.js
export function add(a, b) { return a + b; }
export function subtract(a, b) { return a - b; }
export const PI = 3.14159;
export default function multiply(a, b) { return a \* b; }

// app.js
import \* as Utils from './utils.js';

console.log(Utils.add(5, 3)); // 8
console.log(Utils.subtract(5, 3)); // 2
console.log(Utils.PI); // 3.14159

// Note: Default export is available as 'default' property
console.log(Utils.default(5, 3)); // 15
```

<div class="bg-yellow-100 p-4 rounded-lg mt-4 text-yellow-800">
  <h3 class="font-bold">Important Note</h3>
  <p>
    When using namespace imports, the default export is available as the <code>default</code> property on the imported object.
  </p>
</div>

<!--
Namespace imports are useful when you want to import many exports from a module.
They help avoid cluttering your import statements with many named imports.
However, they can make it less clear which specific parts of a module are being used.
The default export is accessible via the 'default' property, which is often overlooked.
-->

---

# Re-exporting

Re-export allows you to export items that were imported from other modules:

```js
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// utils.js
export const formatNumber = (num) => num.toFixed(2);
export const randomInt = (min, max) => Math.floor(Math.random() \* (max - min + 1)) + min;

// index.js - Re-export everything
export _ from './math.js';
export _ from './utils.js';

// api.js - Re-export selectively
export { add, subtract } from './math.js';
export { formatNumber as format } from './utils.js';

// Re-export default
export { default } from './some-module.js';
export { default as MyClass } from './some-module.js';
```

<p class="opacity-75">Useful for creating a public API for your library or organizing large projects</p>

<!--
Re-exporting is a powerful feature for creating "barrel" files that aggregate exports from multiple modules.
This pattern is commonly used in libraries to provide a clean public API.
It allows you to reorganize your internal file structure without breaking external imports.
You can also rename exports during re-export, which is useful for resolving naming conflicts.
-->

---

# Dynamic Imports

Load modules on demand using the dynamic `import()` function:

```js
// Static import (always loaded)
import { add } from "./math.js";

// Dynamic import (loaded on demand)
async function loadMathModule() {
  try {
    // Returns a promise that resolves to the module object
    const mathModule = await import("./math.js");

    console.log(mathModule.add(5, 3)); // 8
    console.log(mathModule.subtract(5, 3)); // 2

    // Or with destructuring
    const { multiply, divide } = await import("./advanced-math.js");
    console.log(multiply(5, 3)); // 15
  } catch (error) {
    console.error("Error loading module:", error);
  }
}
```

## Benefits:

<v-clicks>

- Code splitting - reduce initial load time
- Conditional loading - load modules only when needed
- Works in browsers and Node.js

</v-clicks>

<!--
Dynamic imports are a key feature for optimizing application performance.
They allow you to load code only when it's needed, reducing initial bundle size.
This is especially important for web applications where load time affects user experience.
Dynamic imports return a Promise, so they work well with async/await syntax.
-->

---

# Best Practices

## Do's ✓

<v-clicks>

- Use named exports for multiple related items
- Use default exports for main functionality
- Keep modules focused on a single responsibility
- Use barrel files (index.js) to simplify imports
- Use dynamic imports for code splitting
- Prefer constants over mutable exports
- Document your public API exports
- Use consistent naming conventions

</v-clicks>

---

## Don'ts ✗

<v-clicks>

- Mix CommonJS and ES Modules in the same file
- Create circular dependencies between modules
- Export mutable variables
- Create modules with side effects
- Use namespace imports for everything
- Export too many things from a single module
- Use default exports for everything
- Rely on file extensions in import paths

</v-clicks>

---

# Module Resolution

## Node.js Resolution

```js
import { foo } from "module-name";
```

<v-clicks>

- Look in `node_modules/module-name`
- Check package.json's `main` field
- Look for index.js if no main
- Check parent directories

</v-clicks>

---

# Summary

This presentation covered the fundamentals of JavaScript modules, from basic syntax to advanced patterns.
Understanding modules is essential for writing maintainable JavaScript applications.
The module system continues to evolve, with new features being added to the language

<v-clicks>

- ES Modules are the standard way to organize JavaScript code
- Default exports are useful for a module's main functionality
- Named exports are ideal for exporting multiple related items
- Dynamic imports enable code splitting and conditional loading
- TypeScript extends module syntax with type-specific features
- Following best practices leads to maintainable, efficient code

</v-clicks>

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Thank you!
  </span>
</div>

---

# Learn More

[Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) · [GitHub](https://github.com/tc39/proposal-modules) · [Examples](https://github.com/mdn/js-examples/tree/master/modules)

---

## Thanks for Listening!

Got questions? Let’s discuss! 🙋‍♂️
