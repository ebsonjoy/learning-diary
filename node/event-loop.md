# 📘 Node.js - Event Loop

## 🔄 What is Event Loop?

The **event loop** is the **heart of Node.js's asynchronous behavior**.

🧠 It allows Node.js to perform **non-blocking I/O operations** — even though JavaScript is single-threaded — by **offloading operations** to the system kernel or thread pool, and then **picking up their results** via callbacks.

💡 Node.js uses the event loop to handle:
- File system operations
- HTTP requests
- Timers
- Callbacks

## ⚙️ How Event Loop Works:

1️⃣ Call Stack: JS code runs line-by-line in the call stack.

2️⃣ Web APIs: async functions (setTimeout, fs.readFile, etc.) are offloaded to the OS or libuv.

3️⃣ Callback Queue / Task Queue:
   - Once async tasks are done, their callbacks are pushed here.

4️⃣ Event Loop:
   - Keeps checking: Is the call stack empty?
   - If yes, it takes one callback from the queue and pushes it to the stack.

🔁 This cycle continues — it’s the “event loop”.

## 🔄 Event Loop Phases (Simplified):

1. timers           → executes callbacks from setTimeout and setInterval
2. pending callbacks → handles some system operations
3. idle, prepare    → only internal
4. poll             → fetch new I/O events
5. check            → executes setImmediate()
6. close callbacks  → e.g., socket.on('close', ...)

⚠️ Between phases: microtasks are executed (like `process.nextTick`, `Promise.then`)

## 📌 Example:

```js

console.log("Start");

setTimeout(() => {
  console.log("Timeout Callback");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise Callback");
});

console.log("End");

🟢 Output:
Start
End
Promise Callback
Timeout Callback

🧠 Why?
- `Promise.then()` (microtask) is run before `setTimeout()` (macrotask)
```
## 🔍 Microtasks vs Macrotasks:

Microtasks:
- `process.nextTick()`
- `Promise.then()`
- `queueMicrotask()`

Macrotasks:
- `setTimeout`
- `setInterval`
- `setImmediate`
- I/O callbacks

🔁 Microtasks run after each phase, before moving to the next phase.

## 🎯 Real-Life Use Case:

✔ Efficiently handle I/O (e.g., API, DB)
✔ Multiple clients handled with one thread
✔ Fast, responsive apps without blocking

## ✅ Advantages:
✔ Non-blocking architecture
✔ Scalable and efficient
✔ Ideal for I/O-heavy apps

❌ Disadvantages:
❗ CPU-heavy tasks block the loop
❗ One mistake (infinite loop, sync blocking) affects everything

## 📦 Summary:

🔸 Event loop keeps Node.js non-blocking
🔸 Works with callback queues and microtasks
🔸 Core of async programming in Node.js
