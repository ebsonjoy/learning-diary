# 📘 JavaScript - Promise

## 🧠 What is a Promise?

A **Promise** is an object that represents the eventual **completion (or failure)** of an asynchronous operation.

➡️ It’s like a placeholder for a value that is not yet known but will be known in the future.

✅ Promises provide a cleaner way to handle async code compared to callbacks.

## 📌 Promise States

1. ⏳ pending   → Initial state, operation not completed
2. ✅ fulfilled → Operation completed successfully
3. ❌ rejected  → Operation failed

Once a promise is settled (fulfilled or rejected), it cannot change.

## 📦 Basic Syntax

```js
const myPromise = new Promise((resolve, reject) => {
  // Do some async task
  let success = true;

  if (success) {
    resolve("🎉 Task successful");
  } else {
    reject("❌ Task failed");
  }
});

myPromise
  .then((result) => console.log(result))  // On success
  .catch((error) => console.error(error)) // On failure
  .finally(() => console.log("🔚 Done"));
```
## 🧪 Real Example: Simulate API Call

```js
function fetchUser() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true;

      if (success) resolve("👤 User data received");
      else reject("❌ Failed to fetch user");
    }, 2000);
  });
}

fetchUser()
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

## 🔁 Promise Chaining

Promise chaining allows you to perform **sequential async tasks**.

Example:
```js
fetchUser()
  .then(user => {
    console.log("✔ User fetched:", user);
    return fetchPosts();
  })
  .then(posts => {
    console.log("✔ Posts fetched:", posts);
  })
  .catch(err => console.error("❌ Error:", err));
```
## 🧩 Promise.all([])

Waits for **all promises to complete** or any one to reject.
```js
Promise.all([p1, p2, p3])
  .then(([r1, r2, r3]) => console.log("✅ All resolved:", r1, r2, r3))
  .catch(err => console.error("❌ One failed:", err));
```
## 🧩 Promise.race([])

Returns the result of the **first promise to settle** (either resolve or reject).
```js
Promise.race([p1, p2])
  .then(result => console.log("🏁 Winner:", result))
  .catch(err => console.error("❌ Failed:", err));
```

## 🟡 Promise.race()

▶️ Returns a promise that settles as soon as the **first** promise in the iterable settles (fulfilled or rejected).

```js
const fast = new Promise((res) => setTimeout(() => res("🚀 Fast done!"), 100));
const slow = new Promise((res) => setTimeout(() => res("🐢 Slow done!"), 1000));

//Example 1

Promise.race([fast, slow])
  .then((result) => console.log(result)); // 🚀 Fast done!

// Example 2: (with rejection)

const fastFail = new Promise((_, rej) => setTimeout(() => rej("❌ Fast failed!"), 100));
const slowSuccess = new Promise((res) => setTimeout(() => res("✅ Slow success!"), 500));

Promise.race([fastFail, slowSuccess])
  .then((res) => console.log(res))
  .catch((err) => console.error(err)); // ❌ Fast failed!

```
## 🟠 Promise.allSettled()

▶️ Returns a promise that **always resolves** after **all** promises settle, regardless of success or failure.
```js
//  Example 1:
const p1 = Promise.resolve("✅ A resolved");
const p2 = Promise.reject("❌ B rejected");
const p3 = Promise.resolve("✅ C resolved");

Promise.allSettled([p1, p2, p3])
  .then((results) => console.log(results));
// Output:
[
  { status: 'fulfilled', value: '✅ A resolved' },
  { status: 'rejected', reason: '❌ B rejected' },
  { status: 'fulfilled', value: '✅ C resolved' }
]
//  Example 2: Check Results Individually
Promise.allSettled([
  Promise.resolve("🎉 OK"),
  Promise.reject("⚠️ Error")
]).then(results => {
  results.forEach((result, idx) => {
    if (result.status === "fulfilled") {
      console.log(`Promise ${idx + 1}: ✅ ${result.value}`);
    } else {
      console.log(`Promise ${idx + 1}: ❌ ${result.reason}`);
    }
  });
});

## ✅ Advantages:
✔ Avoids callback hell
✔ Easy to chain async tasks
✔ Clean syntax with then/catch/finally

## ❌ Disadvantages:
✘ Can still be hard to read with too many `.then()`
✘ Error handling must be carefully done

➡️ Solution: Use `async/await` for cleaner syntax

## 📍 Summary:

🔹 A Promise handles async operations in a structured way.
🔹 Has 3 states: pending, fulfilled, rejected.
🔹 Supports chaining, combining, and racing async tasks.
🔹 Replaced callbacks in modern JS for better readability.
