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

# Circle 9

Presentation slides by Victor Okpe

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

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

```js
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

```js
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

```html
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
