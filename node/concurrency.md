# 📘 Concurrency in Node.js

## 🔍 What is Concurrency?

➡️ Concurrency is the ability of a system to deal with **multiple tasks at once**, by switching between them efficiently.

💡 In Node.js:
• Node.js is **single-threaded** (uses one main thread)
• But it can still handle many operations concurrently using:
  - **Event loop**
  - **Callback queue**
  - **Worker threads**
  - **Async APIs**

## 📦 How Node.js Handles Concurrency?

1️⃣ Non-blocking I/O
   ➤ Node.js delegates I/O (like file read, DB access) to the OS
   ➤ While I/O waits, Node continues processing other tasks

2️⃣ Event Loop
   ➤ Handles callbacks from completed async operations

3️⃣ Thread Pool (via libuv)
   ➤ Used internally for expensive tasks (e.g., file system, DNS)

## 🧪 Real-Life Example

➡️ File upload and email sending:
   - Uploading image to server (I/O)
   - Sending confirmation email
   - Both run **without blocking** other tasks


## ⚙️ Example Code
```js
const fs = require("fs");

console.log("Start");

fs.readFile("data.txt", "utf8", (err, data) => {
  if (err) return;
  console.log("File content:", data);
});

console.log("End");

🧠 Output:

Start
End
File content: [data from file]

✅ Shows how Node handles file read concurrently without blocking.

```
## 🔧 Internals – What’s Behind the Scenes?

| Layer             | Role                                   |
|------------------|----------------------------------------|
| Event Loop        | Controls execution of callbacks        |
| Callback Queue    | Stores tasks waiting for execution     |
| Thread Pool       | Used by libuv for heavy I/O operations |
| Microtasks Queue  | For promises, nextTick, etc.           |


## 🧵 Concurrency vs Parallelism in Node.js

| Feature        | Concurrency (✔ Node.js) | Parallelism (❌ Node.js core) |
|----------------|-------------------------|-------------------------------|
| Tasks at once  | Many, interleaved       | Many, at the same time        |
| Threads        | Single thread           | Multi-threaded                |
| Blocking?      | Avoided via async       | N/A                           |

👉 Node.js achieves concurrency using **non-blocking** techniques,
not true parallelism (unless using Worker Threads or clustering).


## 🧠 When Node.js Struggles?

❌ CPU-heavy tasks (e.g., image processing, encryption)
✅ Solution: Use `worker_threads`, `child_process`, or clustering


## 📊 Summary

✔ Node.js handles many tasks concurrently using event loop & non-blocking I/O  
✔ It is ideal for I/O-heavy applications  
✔ Not great for CPU-bound tasks unless additional threads/processes are used  


