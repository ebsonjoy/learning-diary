# 📘 JavaScript - Scope

## 🔍 What is Scope?

Scope determines the **accessibility (visibility)** of variables in different parts of your code.

In JavaScript, scope answers: "Where can I use this variable?"

## 🧭 Types of Scope in JavaScript

| Scope Type         | Description                                                                  |
| ------------------ | ---------------------------------------------------------------------------- |
| **Global Scope**   | Variable accessible **anywhere** in the code                                 |
| **Function Scope** | Variables declared in a function are accessible **only inside** the function |
| **Block Scope**    | Variables declared with `let` and `const` inside `{}` are block scoped       |
| **Lexical Scope**  | Inner functions have access to outer function variables                      |

## 🌍 1. Global Scope

```js
let a = 10;

function show() {
  console.log(a); // ✅ Accessible
}

show();
console.log(a);   // ✅ Accessible

```
## 🔧 2. Function Scope

```js
function test() {
  let b = 20;
  console.log(b); // ✅ Inside function
}

test();
console.log(b);   // ❌ ReferenceError: b is not defined
```
## 📦 3. Block Scope (`let`, `const`)

```js
{
  let c = 30;
  const d = 40;
  console.log(c, d); // ✅ Inside block
}

console.log(c); // ❌ ReferenceError
console.log(d); // ❌ ReferenceError
// 🔴 var is not block-scoped. It's function-scoped.
```
## 🧠 4. Lexical Scope (Closures)

```js
function outer() {
  let outerVar = "📦 outer";

  function inner() {
    console.log(outerVar); // ✅ Has access due to lexical scope
  }

  inner();
}

outer();
```
## ✅ Advantages of Scope

- Protects variables from unwanted access.
- Reduces name conflicts.
- Enables closures and modular code.

## 🚫 Disadvantages

- May confuse beginners (especially closures).
- Global scope pollution can be risky.
## 📌 Summary

🔹 Global: Everywhere  
🔹 Function: Only in the function  
🔹 Block: Only inside `{}`  
🔹 Lexical: Inner functions can access outer ones
