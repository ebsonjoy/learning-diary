# 📦 Modules

In Node.js, modules are reusable blocks of code that encapsulate related logic — allowing you to organize your project into separate files.

## ✅ Why Use Modules?
- Code reusability

- Better maintainability

- Separation of concerns

- Avoid global namespace pollution

- Easily import/export logic

## 🔰 Types of Modules

| Type                    | Description                  | Example                          |
| ----------------------- | ---------------------------- | -------------------------------- |
| **Core Modules**        | Built-in Node.js modules     | `fs`, `http`, `path`, `os`, etc. |
| **Local Modules**       | Custom-created files/modules | Your own `.js` files             |
| **Third-Party Modules** | Installed via `npm`          | `express`, `mongoose`, etc.      |


## 🧠 How to Use Modules

### 🔸 1. Creating a Local Module (custom)
```js
// math.js

function add(a, b) {
  return a + b;
}
module.exports = { add };

// 📁 app.js

const math = require('./math');
console.log(math.add(5, 10)); // 15

```

### 🔸 2. Using Core Module (built-in)
```js
const os = require('os');
console.log(os.platform());   // win32, linux etc.

```

### 🔸 3. Using Third-Party Module
```js
// npm install lodash

const _ = require('lodash');
console.log(_.capitalize('hello')); // Hello

```

## 🆚 CommonJS vs ES6 Modules

| Feature         | CommonJS (`require`)           | ES Modules (`import`)            |
| --------------- | ------------------------------ | -------------------------------- |
| Syntax          | `require()` / `module.exports` | `import` / `export`              |
| Execution       | Synchronously                  | Asynchronously                   |
| File Extension  | `.js`                          | `.mjs` or `"type": "module"`     |
| Default in Node | Yes                            | From Node v12+ (optional config) |



