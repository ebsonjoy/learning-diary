# 📘 JavaScript – Hoisting  

## 🧠 What is Hoisting?
Hoisting is a JavaScript mechanism where variable and function declarations are moved to the top of their containing scope (either the global scope or a function scope) during the compile phase, before the code is actually executed.

This means you can refer to variables or functions before they are defined in the code — but only under certain rules.

## ⚙️ How Hoisting Works (Behind the Scenes)
- When JavaScript code runs, it goes through two phases:

1.Compilation Phase (before execution):

 - All variable and function declarations are stored in memory.

 - JavaScript "hoists" declarations to the top of their scope.

 - var, let, const, and function are handled differently.

2.Execution Phase:

 - Code is run line by line using the memory set up earlier.


## 🔍 Variable Hoisting

### ✅ With var
- Declarations are hoisted and initialized as undefined.

```js
console.log(x); // undefined
var x = 5;

// 🧠 Internally:

var x;         // hoisted
console.log(x); // undefined
x = 5;         // assignment happens here
```
## ❌ With let and const

- Declarations are hoisted but not initialized.

- They are in a Temporal Dead Zone (TDZ) from the start of the scope to the line where the variable is declared.

### Accessing them in the TDZ causes a ReferenceError.

```js
console.log(a); // ❌ ReferenceError
let a = 10;

console.log(b); // ❌ ReferenceError
const b = 20;

// 🧠 TDZ: JavaScript knows about a and b during compilation but doesn’t allow access until declaration.

```

## 📌 Function Hoisting

### ✅ Function Declarations
- Functions declared using the function keyword are hoisted along with their body.
```js
sayHi(); // Hello

function sayHi() {
  console.log("Hello");
}
// 🧠 JavaScript places the whole function in memory during compile time.
```
## ❌ Function Expressions

// Functions assigned to variables (especially with var) are not hoisted as functions — only the variable is hoisted, not the function definition.
```js
greet(); // ❌ TypeError: greet is not a function

var greet = function () {
  console.log("Hi");
};
// 🧠 Internally:

var greet;       // hoisted as undefined
greet();         // greet is undefined, cannot call
greet = function() { ... }; // assigned later

// ✅ Arrow functions follow the same rule as function expressions.

```
## 🔄 Summary Table

| Type                                   | Hoisted              | Initialized   | Temporal Dead Zone (TDZ)           | Usable Before Declaration    |
| -------------------------------------- | -------------------- | ------------- | ---------------------------------- | ---------------------------- |
| `var`                                  | ✅ Yes                | ✅ `undefined` | ❌ No                               | ✅ (value is `undefined`)     |
| `let`                                  | ✅ Yes                | ❌ No          | ✅ Yes                              | ❌ ReferenceError             |
| `const`                                | ✅ Yes                | ❌ No          | ✅ Yes                              | ❌ ReferenceError             |
| `function`                             | ✅ Yes                | ✅ Yes         | ❌ No                               | ✅                            |
| `function expression / arrow function` | ✅ (as variable only) | ❌ No          | ❌ (if `var`), ✅ (if `let`/`const`) | ❌ TypeError / ReferenceError |


## ✅ Advantages of Hoisting

- Allows flexible placement of function declarations

- Avoids undefined variable errors in some cases

## ❌ Disadvantages / Pitfalls

- Can confuse beginners if variables are used before declarations

- May lead to bugs when using var, especially inside loops and conditions

- let and const behave differently than var, which can be unintuitive

## 📦 Real-Life Example

// Imagine you're writing code that initializes settings:

```js

function setup() {
  if (!configLoaded) {
    loadConfig();
  }

  var configLoaded = true;

  function loadConfig() {
    console.log("Config Loaded");
  }
}

setup(); // Nothing happens because configLoaded is undefined
// 🧠 Due to hoisting, configLoaded becomes undefined, not true.
```


