---
---

# You can also start simply with 'default'

theme: seriph

# random image from a curated Unsplash collection by Anthony

# like them? see https://unsplash.com/collections/94734566/slidev

background: https://cover.sli.dev

# some information about your slides (markdown enabled)

title: Welcome to Our Slidev
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

# ogImage: https://cover.sli.dev

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

**1. Function Declaration**:

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

**2. Functions Expression**:

It is defined as a value and assigned to a variable, it can not be called before defining it.

```js
let greet = function (name) {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

**3. Arrow Function**:

This was introduced in ES6 and it can be defined without the function keyword and also assigned to a variable and the essential thing is
that the parameters and function body is seperated by "=>". it is very easy, short and handy to code with😊

```js {monaco-run}
let greet = (name) => {
  console.log(`Welcome back ${name}!!`);
};

greet("chioma"); //Output; Welcome back Chioma!!
```

---

## Callbacks Functions

A **Callback function** is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of action.

Callbacks pay a big factor in asynchronous functions, where one function has to wait for another function (like waiting for a file to load), it makes functions more reusable too. Callbacks allows you to reuse functions in flexible way.

```js
function display(value) {
  console.log(value);
}

function calTwoNum(num1, num2, callBack) {
  let sum = num1 + num2;
  callBack(sum);
}

calTwoNum(10, 8, display); //Output; 18.
```

Here, display is passed as a callback to show output after calculating.

---

# DOM

**DOM** (document object module) is the interface that allows javascript to interact with HTML and CSS.
**DOM** manipulation is the process of changing the structure or content of a web page using javascript or any programming language.

---

# Dom Manipulation

## Searching the DOM

Using query selector is a common practice in web development.It allows us find an element using it's CSS selector(class or id)

```js
let element = document.querySelector(".people");
// here, we are finding an element with the class name people and assigning it to a variable
```

other ways to search the DOM are getElementById, getElementByClassName, querySelectorAll

## Changing the DOM

### Adding Content

This allows you set the HTML content within an element using innerHTML

```js
let element = document.querySelector(".myElement");
element.innerHTML = "<p>This is an element</p>";
```

### Adding Elements

You can create new elemnts using document.create and add to the DOM using append,appendChild,insertBefore

```js
let element = document.querySelector(".myElement");
let newElement = document.createElement("div");
newElement.textContent = "This is a new element";
element.appendChild(newElement);
```

### Removing Elements

You can remove elements using element.remove()

### Updating Texts

You can update text of an element using the textContent property

---

# Promises

**WHAT IS A PROMISE?**

This is a neater way to handle asynchronous operations in java script.

**Why are promises a better alternative to callbacks?**

In a case where several callbacks would be needed, callbacks would eventually become inefficient, make code less readablw and can lead to 'callback hell'. Promises are very useful for such situations.

---

## POSSIBLE PROMISE STATES

Promises can be in three states:

- Pending: this is the initial state, the asynchronous operation has not completed yet. Like waiting for a friend to call you back.
- Resolved: the asynchronous operation completed successfully and thus the promise has a resulting value. Your friend called back and gave you an answer.
- Rejected: the asynchronous operation failed. Your friend never called you back.

  ***

## PROMISE EXAMPLE AND FORMAT

```js {monaco-run}
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

  ***

---
## API Calls

API’s (Application Programming Interface) allows communications between softwares.
In modern/recent times, this is done using the fetch method.
The fetch method helps us send and receive data from a server.

Here's an example of a simple fetch request in JavaScript:
```js
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(response => response.json())  // Convert response to JSON
  .then(user => {
    console.log(`User Name: ${user.name}`);
    console.log(`Email: ${user.email}`);
    console.log(`City: ${user.address.city}`);
  })
  .catch(error => console.error("Error fetching user data:", error));
---

# Steps to Make an API Call

1. Identify the API endpoint
  * An API endpoint is the URL where our request is sent.
  * It defines what data we're fetching, posting, or updating.
2. Use the fetch method  
  * The fetch() function is used in JavaScript to send HTTP requests.
  * It helps us retrieve data from an API or send new data to a server.
  ```js
  fetch('https://api.example.com/users')
  .then(response => response.json())
  .then(data => console.log(data));
  ```
3. Handle the response data
  * APIs return data, usually in JSON format.
  * We must extract and use this data within our application.
  ```js
  .then(response => response.json())
  .then(data => console.log("User info:", data));
  ```
4. Manage errors properly  
  * Sometimes, API calls fail due to bad requests or server issues.
  * Error handling ensures our app doesn't break when that happens.
  ```js
  .catch(error => console.error("Error fetching data:", error));
  ```
---

## API Call Methods
There are 4 main methods used in making API calls in JavaScript.
Using restaurant orders as  case point here:

### GET
Retrieves existing data from a server or site.

For example:
- We can search for restaurants. When we use the search bar, the app makes a GET request to fetch restaurant listings.

```js
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(response => response.json())  // Convert response to JSON
  .then(user => {
    console.log(`User Name: ${user.name}`);
    console.log(`Email: ${user.email}`);
    console.log(`City: ${user.address.city}`);
  })
  .catch(error => console.error("Error fetching user data:", error));
```
---

### POST
Sends data to a server to create new information.

- We can place an order: The app sends a POST request to the restaurant’s API with our order details
```js
fetch("https://reqres.in/api/users", {
    method: "POST",
    headers: {
        "Content-Type": "application/json",
        "x-api-key": "reqres-free-v1"
    },
    body: JSON.stringify({ name: "Victoria", job: "Developer"})
})
    .then (response => response.json())
    .then (data => console.log("User Created: ", data))
    .catch (error => console.error("Error creating user:", error))
```
---
### PUT/PATCH
Updates existing data on a server

- We can decide to  change our order: If we update our meal selection, the app sends a PUT request to modify our order.
(PUT replaces existing data while PATCH updates a part of it)
```js
fetch("https://reqres.in/api/users/2", {
    method: "PUT",
    headers: {
        "Content-Type": "application/json",
        "x-api-key": "reqres-free-v1"
    },
    body: JSON.stringify({ name: "Victoria", job: "Junior Developer"})
})
    .then (response => response.json())
    .then (data => console.log("User Created: ", data))
    .catch (error => console.error("Error creating user:", error))
```

---

### DELETE
This removes existing data from the system.


- We cancel our order → The app sends a DELETE request to remove our order from the system.


```js
fetch("https://reqres.in/api/users/2", {
    method: "DELETE",
    headers: {
        "Content-Type": "application/json",
        "x-api-key": "reqres-free-v1"
    },
})
    .then(response => {
        if (response.ok) console.log("User deleted successfully.");
        else throw new Error(`Error: ${response.status} - ${response.statusText}`);
    })
    .catch(error => console.error("DELETE Request Failed:", error));
```

---

## ERROR HANDLING
Error handling in Javascript is a way of controlling errors or bugs that might happen and stops is from breaking out of the script.


For example: if you were watching a TV and something happens to the network, error handling can prompts the TV to say “Slow Network” or “Network Disconnected” instead shutting down the TV.


One way of doing this is using the try…catch method.

---

### try...catch
There are 4 main parts when handling errors using the try…catch method


* try:
The try implies that a code should try running even though there are errors.
Without it, JS stops the entire process and throws and error in the console.


* catch:
The catch part of the statement, sees the error and catches it.
Without it, the entire program breaks.


* console.log:
This logs in the error with the details of the error.
Without it, we won’t see any useful information about what went wrong which makes debugging difficult.


* finally:
This is the last part that will always run no matter the error.
It is used to log a completion message after debugging.

---

### Example
```js
try {
    let userAge = prompt("Enter a number")
    let number = parseInt(userAge)


    if (isNaN(number)) {
        throw new Error ("Invalid input! Please enter a number")
    }
    console.log(`You entered: ${number}`)
} catch (error) {
    console.log(`Error caught: ${error.message}`)
} finally {
    console.log("Execution finished!")
}
```

---

## Custom Error Handling
A custom error in JavaScript allows us create specific error types tailored to unique situations instead of relying on generic JavaScript errors.


For example:
If we have a system where users enter their age, and we want to prevent unrealistic entries (like negative numbers or extremely high numbers). We can create a custom error class to handle this situation.


It is important because:
* It helps identify exactly where and why an error occurred.
* Instead of a vague error, users and developers see a specific message related to the issue.


---
### Example
```js
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

```js
// utils.js
export function greet(name) {
  return `Hello, ${name}`;
}

// main.js
import { greet } from "./utils.js";
console.log(greet("Alice"));
```

### CommonJS

```js
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

```js
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

```js
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

```js {monaco-run}
async function greet() {
  return "Hello!";
}

// Equivalent to:
function greet() {
  return Promise.resolve("Hello!");
}
```

Usage:

```js {monaco-run}
greet().then(console.log); // Logs: Hello!
```

---

## What is `await`?

You use `await` **inside an async function** to pause execution until a Promise resolves:

```js {monaco-run}
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

```js {monaco-run}
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

async function `getUserData()` — this is an asynchronous function.

`fetch(...)` — sends a network request to get user data (from a public API).

await `res.json()` — parses the response body as `JSON`.

All this is wrapped in a try `{ ... } catch { ... }` block to catch errors like:
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

## Thanks for Listening!

Got questions? Let’s discuss! 🙋‍♂️
