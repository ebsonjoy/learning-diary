# 📘 JavaScript - async/await

## 🧠 What is async/await?

`async` and `await` are keywords introduced in ES2017 that make it easier to work with **Promises** in JavaScript.

✅ It helps write **asynchronous code** in a **synchronous-looking style**.
✅ It avoids callback hell and makes code more readable and maintainable.

## 🧩 async Keyword

🔹 Declares a function that always returns a Promise.
🔹 You can use `await` inside this function.

## 📌 Example:
```js
async function getData() {
  return "Hello";
}
getData().then(console.log); // Output: Hello
```
## ⏳ await Keyword

- Can only be used inside `async` functions.
- It waits for a Promise to resolve.

## 📌 Example:
```js
function delay() {
  return new Promise(resolve => {
    setTimeout(() => resolve("✅ Done!"), 2000);
  });
}

async function run() {
  console.log("⏳ Waiting...");
  const result = await delay();
  console.log(result);
}

run();
// Output:
// ⏳ Waiting...
// (after 2 seconds)
// ✅ Done!
```
## ❗ Error Handling in async/await

Use try-catch for handling errors.

📌 Example:
```js
async function fetchUser() {
  try {
    const res = await fetch('https://invalid-url.com');
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error("❌ Error:", err.message);
  }
}
```
## 📌 Real-Life Analogy:

🔸 `await` is like telling JavaScript:
   "Hold on here, wait for this task to finish before going to the next line."

🔸 Like waiting at a red light before proceeding.

## 📦 Real Use Case:
```js
async function getUserData() {
  const user = await getUserFromDB();     // async DB call
  const posts = await getPosts(user.id);  // async API call
  return { user, posts };
}
```
## ✅ Advantages:
✔ Clean, readable code
✔ Avoids .then() chaining
✔ Easy to manage multiple async operations

## ❌ Disadvantages:
✘ Can't be used at the top level in older JS versions
✘ Error handling can still be missed

## 📍 Summary:

🔹 async functions return Promises
🔹 await waits for Promise resolution
🔹 Use try/catch for error handling
🔹 Makes async code easy to read and write
