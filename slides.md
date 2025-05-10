---
theme: seriph
title: Greetings/Introduction
background: https://cover.sli.dev
info: |
  ## Slidev Starter Template  
  Presentation slides for developers.  
  Learn more at [Sli.dev](https://sli.dev)
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
monaco: true
monacoTypesAdditionalPackages:
  - vue
---

# JavaScript Summary from Circle 9

_A Tinyuka Production_<br>
Presentation slides by:
<br>

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
    Press Space for next page <carbon:arrow-right />
  </div>

---

## Team Players

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

## Table of Content

<Toc text-sm minDepth="1" maxDepth="1" />

---

# JavaScript Functions

Function is a block of reusable code that can perform a particular task, it can take in parameters and it's value(argument) also return a value, arrays and objects.

Below are codes examples of how functions are used to perform tasks:

```ts {monaco-run}
function greetUser() {
  alert("you are welcome");
}

greetUser();
```

---

## Ways of declaring a function

**1. Function Declaration**:

It is the widely and default way of declaring a function and the exciting thing here is that it can be called before defining it.

```ts {monaco-run}
//Remember: The 'name' is a parameter and it accepts a value called argument.
greet("chioma");

function greet(name) {
  console.log(`Welcome back ${name}!!`);
}
//Output; Welcome back Chioma!!
```

---

**2. Functions Expression**:

It is defined as a value and assigned to a variable, it can not be called before defining it.

```ts {monaco-run}
let greet = function (name) {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

**3. Arrow Function**:

This was introduced in ES6 and it can be defined without the function keyword and also assigned to a variable and the essential thing is
that the parameters and function body is seperated by "=>". it is very easy, short and handy to code with😊

```ts {monaco-run}
let greet = (name) => {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

---

# Callbacks Functions

A **Callback function** is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of action.

Callbacks pay a big factor in asynchronous functions, where one function has to wait for another function (like waiting for a file to load), it makes functions more reusable too. Callbacks allows you to reuse functions in flexible way.

```ts {monaco-run}
function display(value) {
  console.log(value);
}

function calTwoNum(num1, num2, callBack) {
  let sum = num1 + num2;
  callBack(sum);
}

calTwoNum(10, 8, display); //Output; 18.
```

---

# DOM

**DOM** (document object model) is the interface that allows javascript to interact with HTML and CSS.
<br>

# Dom Manipulation

**DOM manipulation** is the process of changing the structure or content of a web page using javascript or any programming language.

**Searching the DOM**

Using query selector is a common practice in web development. It allows us find an element using it's CSS selector(class or id).

```ts
let element = document.querySelector(".people");
// here, we are finding an element with the class name people and assigning it to a variable
```

**Other ways to search the DOM are:** getElementById, getElementByClassName, querySelectorAll.

---

## Changing the DOM

### Adding Content

This allows you set the HTML content within an element using innerHTML

```ts
let element = document.querySelector(".myElement");
element.innerHTML = "<p>This is an element</p>";
```

## Adding Elements

You can create new elemnts using `document.create` and add to the DOM using `append`, `appendChild`, `insertBefore`

```ts {monaco}
let element = document.querySelector(".myElement");
let newElement = document.createElement("div");
newElement.textContent = "This is a new element";
element.appendChild(newElement);
```

You can remove elements using `element.remove()`

You can update text of an element using the `textContent` property

---

# Promises

**WHAT IS A PROMISE?**

This is a neater way to handle asynchronous operations in java script.

**Why are promises a better alternative to callbacks?**

In a case where several callbacks would be needed, callbacks would eventually become inefficient, make code less readable and can lead to 'callback hell'. Promises are very useful for such situations.

**Promises can be in three states**:

- Pending: this is the initial state, the asynchronous operation has not completed yet. Like waiting for a friend to call you back.
- Resolved: the asynchronous operation completed successfully and thus the promise has a resulting value. Your friend called back and gave you an answer.
- Rejected: the asynchronous operation failed. Your friend never called you back.

---

## PROMISE EXAMPLE AND FORMAT

```ts {monaco-run}
const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("Operation successful");
  } else {
    reject("Something went wrong");
  }
});

myPromise
  .then((result) => console.log(result)) // If resolved
  .catch((error) => console.error(error)); // If rejected
```

- To invoke a promise the `new Promise` key word is used. It takes two parameters; `resolve` and `reject'. The resolve holds if the callback is successful and reject holds if it is not i.e there is an errror.

- The `.then' is used to handle successes. Each `.then()`returns a new promise, so you can chain multiple`.then() calls`.
- The `.catch()` handles errors. It catches errors that occur in the promise chain before it.

---

# Async & Await in JavaScript

# What are async and await?

They are tools to handle asynchronous code in JavaScript in a clean, readable way — instead of using callbacks or .then() chains with Promises.

Think of async/await as a way to write asynchronous code that looks like synchronous code.

## Key Concepts

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

## Why Use `async` and `await`?

✅ Makes asynchronous code look like normal synchronous code  
✅ Easier to read, write, and debug than `.then()` chains  
✅ Simplified error handling using `try/catch`

---

## What is `async`?

Adding `async` before a function:

This automatically makes it return a **Promise**

```ts {monaco}
async function greet() {
  return "Hello!";
}

// Equivalent to:
function greet() {
  return Promise.resolve("Hello!");
}
```

Usage:

```ts {monaco}
greet().then(console.log); // Logs: Hello!
```

---

## What is `await`?

You use `await` **inside an async function** to pause execution until a Promise resolves:

```ts {monaco-run}
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

## Summary

| Feature       | Description                           |
| ------------- | ------------------------------------- |
| `async`       | Makes a function return a Promise     |
| `await`       | Waits for the Promise to resolve      |
| `try/catch`   | Handles async errors cleanly          |
| `Promise.all` | Runs multiple async tasks in parallel |

---

# ERROR HANDLING

Error handling in Javascript is a way of controlling errors or bugs that might happen and stops is from breaking out of the script.

For example: if you were watching a TV and something happens to the network, error handling can prompts the TV to say “Slow Network” or “Network Disconnected” instead shutting down the TV.

One way of doing this is using the `try…catch` method.

---

## try...catch

There are **4 main** parts when handling errors using the `try…catch` method

- **try**:
  The try implies that a code should try running even though there are errors.
  Without it, JS stops the entire process and throws and error in the console.

- **catch**:
  The catch part of the statement, sees the error and catches it.
  Without it, the entire program breaks.

- **console.log**:
  This logs in the error with the details of the error.
  Without it, we won’t see any useful information about what went wrong which makes debugging difficult.

- **finally**:
  This is the last part that will always run no matter the error.
  It is used to log a completion message after debugging.

---

## Example

```ts {monaco-run}
try {
  let userAge = prompt("Enter a number");
  let number = parseInt(userAge);

  if (isNaN(number)) {
    throw new Error("Invalid input! Please enter a number");
  }
  console.log(`You entered: ${number}`);
} catch (error) {
  console.log(`Error caught: ${error.message}`);
} finally {
  console.log("Execution finished!");
}
```

---

## Custom Error Handling

A custom error in JavaScript allows us create specific error types tailored to unique situations instead of relying on generic JavaScript errors.

_For example_:
If we have a system where users enter their age, and we want to prevent unrealistic entries (like negative numbers or extremely high numbers). We can create a custom error class to handle this situation.

_It is important because_:

- It helps identify exactly where and why an error occurred.
- Instead of a vague error, users and developers see a specific message related to the issue.

---

### Example

```ts {monaco-run}
// define the error type
class AgeError extends Error {
  constructor(message) {
    super(message);
    this.name = "AgeError";
  }
}
// we set a condition to ensure the error message is triggered when a user inputs what we don't want
function checkUserAge(age) {
  if (age < 0 || age > 120) {
    throw new AgeError("Invalid age! Please enter a realistic age.");
  }
  console.log(`Valid age entered: ${age}`);
}

// we see the error type we have assigned. This will trigger our custom AgeError
try {
  checkUserAge(500);
} catch (error) {
  console.log(`Error caught: ${error.name} - ${error.message}`);
}
```

---

# API Calls

API’s **(Application Programming Interface)** allows communications between softwares.
<br>
In modern/recent times, this is done using the fetch method.
The fetch method helps us send and receive data from a server.

Here's an example of a simple fetch request in JavaScript:

```ts {monaco-run}
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then((response) => response.json()) // Convert response to JSON
  .then((user) => {
    console.log(`User Name: ${user.name}`);
    console.log(`Email: ${user.email}`);
    console.log(`City: ${user.address.city}`);
  })
  .catch((error) => console.error("Error fetching user data:", error));
```

---

## Steps to Make an API Call

1. Identify the API endpoint

- An API endpoint is the URL where our request is sent.
- It defines what data we're fetching, posting, or updating.

  <br>

2. Use the fetch method

- The fetch() function is used in JavaScript to send HTTP requests.
- It helps us retrieve data from an API or send new data to a server.

```ts
fetch("https://api.example.com/users")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

---

3. Handle the response data

- APIs return data, usually in JSON format.
- We must extract and use this data within our application.

```ts
.then(response => response.json())
.then(data => console.log("User info:", data));
```

<br>

4. Manage errors properly

- Sometimes, API calls fail due to bad requests or server issues.
- Error handling ensures our app doesn't break when that happens.

```ts
.catch(error => console.error("Error fetching data:", error));
```

---

## API Call Methods

There are 4 main methods used in making API calls in JavaScript.
Using restaurant orders as case point here:

### GET

Retrieves existing data from a server or site.

For example:

- We can search for restaurants. When we use the search bar, the app makes a GET request to fetch restaurant listings.

```js {monaco-run}
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then((response) => response.json()) // Convert response to JSON
  .then((user) => {
    console.log(`User Name: ${user.name}`);
    console.log(`Email: ${user.email}`);
    console.log(`City: ${user.address.city}`);
  })
  .catch((error) => console.error("Error fetching user data:", error));
```

---

### POST

Sends data to a server to create new information.

- We can place an order:
  <br>
  The app sends a POST request to the restaurant’s API with our order details

```ts {monaco-run}
fetch("https://reqres.in/api/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "x-api-key": "reqres-free-v1",
  },
  body: JSON.stringify({ name: "Victoria", job: "Developer" }),
})
  .then((response) => response.json())
  .then((data) => console.log("User Created: ", data))
  .catch((error) => console.error("Error creating user:", error));
```

---

### PUT/PATCH

Updates existing data on a server

- We can decide to change our order:
  <br>
  If we update our meal selection, the app sends a PUT request to modify our order.
  (PUT replaces existing data while PATCH updates a part of it)

```ts {monaco-run}
fetch("https://reqres.in/api/users/2", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
    "x-api-key": "reqres-free-v1",
  },
  body: JSON.stringify({ name: "Victoria", job: "Junior Developer" }),
})
  .then((response) => response.json())
  .then((data) => console.log("User Created: ", data))
  .catch((error) => console.error("Error creating user:", error));
```

---

## DELETE

This removes existing data from the system.

- We cancel our order → The app sends a DELETE request to remove our order from the system.

```ts {monaco-run}
fetch("https://reqres.in/api/users/2", {
  method: "DELETE",
  headers: {
    "Content-Type": "application/json",
    "x-api-key": "reqres-free-v1",
  },
})
  .then((response) => {
    if (response.ok) console.log("User deleted successfully.");
    else throw new Error(`Error: ${response.status} - ${response.statusText}`);
  })
  .catch((error) => console.error("DELETE Request Failed:", error));
```

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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco}
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

```js {monaco-run}
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

---

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

## Best Practices

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

```js {monaco-run}
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

This section covered the fundamentals of JavaScript modules, from basic syntax to advanced patterns.
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

---

# Learn More

[Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) · [GitHub](https://github.com/tc39/proposal-modules) · [Examples](https://github.com/mdn/js-examples/tree/master/modules)

---

# JavaScript Bundlers

## What is a Bundler?

A **JavaScript bundler** takes many files and dependencies and combines them into one or a few optimized files that the browser can load efficiently.

## Why Use a Bundler?

- Fewer HTTP requests
- Easier code organization with modules
- Enables modern features like ES Modules, TypeScript, JSX
- Minifies and optimizes your code for production

---

## How Bundlers Work (Simplified)

1. Start from an entry file
2. Build a dependency graph
3. Combine all modules
4. Minify and optimize
5. Output to `/dist` folder

---

## Popular Bundlers

- **Webpack** – Powerful, customizable, but complex
- **Parcel** – Zero config, beginner friendly
- **Vite** – Lightning fast, ESM-based dev server
- **esbuild** – Super fast, minimal setup

## Webpack Example

```ts
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

## Parcel Example

### File: src/utils.js

```ts
export function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}
```

### File: src/greet.js

```ts {monaco}
import { capitalize } from "./utils.js";
export function greet(name) {
  return `Hello, ${capitalize(name)}!`;
}
```

### File: src/index.js

```ts
import { greet } from "./greet.js";
console.log(greet("world"));
```

## HTML Entry (index.html)

```html
<body>
  <script src="./dist/bundle.js" defer></script>
</body>
```

---

# EventListener

An EventListener is a function in programming (commonly in JavaScript) that waits for a specific event (like a click, key press, or mouse movement) to happen on an element—and then runs some code when it does.

🧠 Think of it like this:

_You're telling the browser:_
"Hey, when the user does this, run that."`

### For example

```ts {monaco}
// Click Event
document.getElementById("myButton").addEventListener("click", function () {
  alert("You clicked the button!");
});

// Mouseover Event
document.getElementById("nameInput").addEventListener("mouseover", function () {
  console.log("Mouse is over the input!");
});
```

---

## Bubbling and Capturing

#### Capturing and bubbling are two phases of how events propagate through the Document Object Model (DOM) in JavaScript when you interact with elements (like clicking, typing, etc.).

---

#### 📌 JavaScript Event Capturing

```ts {monaco run}
const first = document.querySelector(".firstdiv");
const second = document.querySelector(".seconddiv");
const third = document.querySelector(".thirddiv");

// Event Capturing: triggers from outermost to innermost
firstDiv.addEventListener(
  "click",
  () => {
    console.log("firstDiv clicked in capturing phase");
  },
  { capture: true }
);
secondDiv.addEventListener(
  "click",
  () => {
    console.log("secondDiv clicked in capturing phase");
  },
  { capture: true }
);
thirdDiv.addEventListener(
  "click",
  () => {
    console.log("thirdDiv clicked in capturing phase");
  },
  { capture: true }
);
```

---

### JavaScript Event Bubbling

```ts {monaco-run}
const first = document.querySelector(".firstdiv");
const second = document.querySelector(".seconddiv");
const third = document.querySelector(".thirddiv");

// Event Bubbling: triggers from innermost to outermost

firstDiv.addEventListener("click", () => {
  console.log("firstDiv clicked in bubbling phase");
});
secondDiv.addEventListener("click", () => {
  console.log("secondDiv clicked in bubbling phase");
});
thirdDiv.addEventListener("click", () => {
  console.log("thirdDiv clicked in bubbling phase");
});
```

---

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Common Event Listener Types</title>
    <style>
      table {
        width: 80%;
        border-collapse: collapse;
        margin: 20px auto;
        font-family: Arial, sans-serif;
      }
      th,
      td {
        border: 1px solid #444;
        padding: 10px;
        text-align: left;
      }
      th {
        background-color: #ddd;
      }
      caption {
        font-size: 1.5em;
        margin-bottom: 10px;
        font-weight: bold;
      }
    </style>
  </head>
  <body>
    <table>
      <caption>
        Common JavaScript Event Listener Types
      </caption>
      <thead>
        <tr>
          <th>Event Type</th>
          <th>Use</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>click</td>
          <td>
            Fires when a user clicks on an element, often used for buttons and
            links.
          </td>
        </tr>
        <tr>
          <td>dblclick</td>
          <td>Fires when a user double-clicks on an element.</td>
        </tr>
        <tr>
          <td>mouseover</td>
          <td>Fires when the user moves the mouse over an element.</td>
        </tr>
        <tr>
          <td>mouseout</td>
          <td>Fires when the user moves the mouse away from an element.</td>
        </tr>
        <tr>
          <td>keydown</td>
          <td>Fires when a key is pressed down.</td>
        </tr>
        <tr>
          <td>keyup</td>
          <td>Fires when a key is released.</td>
        </tr>
        <tr>
          <td>submit</td>
          <td>Fires when a form is submitted.</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

---

# THE END

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Thank you!
  </span>
</div>

---

---

---
