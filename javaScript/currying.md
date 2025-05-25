# 📘 JavaScript - Currying  

## 🔍 What is Currying?
Currying is a functional programming technique where a function is transformed into a sequence of functions, each taking one argument at a time.

### Instead of:
- f(a, b, c)
### You write:
- f(a)(b)(c)

## ✅ Why Use Currying?
- ✅ Break down a function into smaller, reusable parts

- ✅ Makes functions more flexible and composable

- ✅ Common in functional programming and frameworks like Redux

## 🧠 Real-Life Analogy:
Ordering food at a restaurant:

order("Burger")("Cheese")("Takeaway");

Each step adds an option and returns a new function until the full order is built.

## 💻 Implementation Example:
🔹 Normal Function:
```js
function add(a, b, c) {
  return a + b + c;
}
console.log(add(1, 2, 3)); // 6

// 🔹 Curried Version:

function curryAdd(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
console.log(curryAdd(1)(2)(3)); // 6
```

## ✨ More Elegant (Arrow Syntax):
```js
const curryAdd = a => b => c => a + b + c;
console.log(curryAdd(1)(2)(3)); // 6
```
## 🔄 Reusable Example:

```js
function multiply(a) {
  return function (b) {
    return a * b;
  };
}

const double = multiply(2);
console.log(double(5)); // 10
```
## 📦 Currying in Libraries
- Lodash: _.curry()

- Ramda: R.curry()
```js
import _ from "lodash";

const curriedSum = _.curry((a, b, c) => a + b + c);
console.log(curriedSum(1)(2)(3)); // 6
```

## ⚖️ Advantages
- ✅ Clean and readable function chaining

- ✅ Reusability

- ✅ Helps with functional programming

## ❌ Disadvantages
- ❌ Hard to read for beginners

- ❌ Can lead to deeply nested functions

