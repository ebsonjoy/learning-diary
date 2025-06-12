# ⚙️ Process vs Threads in Node.js

## 📘 What is a Process?

A **process** is an instance of a running program. In Node.js, when you run a script using `node app.js`, it starts a new process.

### 🔧 Key Points:
- Each process has its own **memory space**.
- It runs **independently** from other processes.
- Communication between processes happens through **inter-process communication (IPC)**.
- You can use the `child_process` module to spawn new processes.

### ✅ Example:
```js
const { fork } = require('child_process');
const child = fork('child.js');

```
## 📘 What is a Thread?
- A thread is a smaller unit of a process that runs in parallel. Threads share the same memory space.

- In Node.js, JavaScript code is single-threaded, but it uses libuv and a thread pool behind the scenes for I/O operations.

### 🔧 Key Points:
- Node.js main thread runs JavaScript code.

- Heavy tasks like file I/O, DNS lookups, and crypto use worker threads or libuv's thread pool.

- You can explicitly create threads using the worker_threads module.

## ✅ Example:
```js
const { Worker } = require('worker_threads');

new Worker('./worker.js');

```
## 🧩 Node.js Architecture

Node.js is single-threaded in terms of JavaScript execution but multi-threaded internally:

| Part              | Description                                      |
| ----------------- | ------------------------------------------------ |
| Event Loop        | Single-threaded, handles async callbacks         |
| libuv Thread Pool | Multi-threaded, handles file system, DNS, crypto |
| Worker Threads    | Optional multi-threaded JS execution             |
| Child Processes   | Separate memory, multiple Node.js processes      |


## 🔍 Differences Between Process and Thread in Node.js

| Feature         | Process                  | Thread                                      |
| --------------- | ------------------------ | ------------------------------------------- |
| Memory          | Separate memory          | Shared memory                               |
| Communication   | Slower (via IPC)         | Faster (shared context)                     |
| Overhead        | Higher                   | Lower                                       |
| Crashing effect | Only one process crashes | Thread crash can affect others              |
| Use in Node.js  | `child_process` module   | `worker_threads` module                     |
| Performance     | Good for CPU isolation   | Good for parallel execution in same process |


## 🧠 When to Use What?

| Scenario                              | Use                         |
| ------------------------------------- | --------------------------- |
| CPU-intensive operations              | `worker_threads`            |
| Running another Node.js script        | `child_process` or `fork()` |
| Parallel file I/O or background tasks | Thread pool (auto)          |
| Isolated execution with crash safety  | Process                     |

## 📦 Related Modules
- child_process: for creating new Node.js processes

- worker_threads: for running JS code in multiple threads

- cluster: for creating multiple Node.js processes that share the same port

## ⚙️ Summary
Concept	Description
- Process	An independent execution environment with its own memory and event loop.
- Thread	A lightweight unit of execution within a process, sharing memory.

In Node.js, use processes for full isolation and threads for parallel computation within the same app.