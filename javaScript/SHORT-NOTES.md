# Topics
- 1.Self-Invoking Functions in JavaScript
---

# 1.Self-Invoking Functions in JavaScript

## What is it?
A **self-invoking function** is a function that runs **automatically** when it is defined.

## Where is it used?
Used to **create a local scope** and **avoid polluting the global scope**.

## Syntax:
```js
(function () {
  // code runs automatically
  console.log("Self-invoked");
})();
---