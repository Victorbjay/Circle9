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
css: unocss
---

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
