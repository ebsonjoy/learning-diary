# 📘 JavaScript - Callback

## 🧠 What is a Callback?

A **callback** is a **function passed as an argument** to another function.
It is **executed after some operation has been completed**, typically used for async tasks like I/O, API calls, timers, etc.

✅ JavaScript uses callbacks to handle asynchronous operations.

##
🧪 Syntax Example:
```js
function greet(name, callback) {
  console.log("👋 Hello " + name);
  callback();
}

function sayBye() {
  console.log("👋 Bye!");
}

greet("Ebson", sayBye);

// Output:
// 👋 Hello Ebson
// 👋 Bye!
```
## ⏱ Real Asynchronous Callback:
```js
setTimeout(function () {
  console.log("⏰ Executed after 2 seconds");
}, 2000);
```
## 🧩 Use Case: Reading a file (Node.js example)
```js
const fs = require('fs');

fs.readFile('file.txt', 'utf8', function(err, data) {
  if (err) {
    return console.log("❌ Error:", err);
  }
  console.log("📄 File content:", data);
});
```
## 🌀 Callback Hell (Pyramid of Doom)

When many callbacks are nested, it becomes hard to read and maintain.

📌 Example:
```js
login(user, (err, token) => {
  getProfile(token, (err, profile) => {
    getPosts(profile.id, (err, posts) => {
      console.log(posts);
    });
  });
});
```
➡️ Solution: Use Promises or async/await

## 🧠 Synchronous vs Asynchronous Callbacks

🔹 Synchronous: Runs immediately
   Example: Array methods
   [1,2,3].forEach(function(n) {
     console.log(n);  // 1 2 3
   });

🔹 Asynchronous: Runs after a task finishes
   Example: setTimeout, fs.readFile

## ✅ Advantages:
✔ Great for async operations
✔ Simple logic for small tasks
✔ Powerful with functions as first-class citizens

## ❌ Disadvantages:
✘ Hard to read when deeply nested
✘ Difficult to debug and maintain
✘ Can lead to callback hell

## 📍 Summary:

🔹 A callback is a function passed into another function.
🔹 Used heavily for async operations.
🔹 Too many nested callbacks → Callback Hell.
🔹 Replaced by Promises and async/await for modern JS.
