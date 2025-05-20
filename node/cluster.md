# 🧵 Node.js - Cluster Module

**Date:** 2025-05-19

---

## 🧠 What is Cluster?

- Node.js runs on a **single thread** by default.
- The **Cluster module** allows you to **create child processes** (workers) that **share the same server port**.
- Each worker runs on its **own event loop and memory**, taking advantage of **multi-core systems**.

---

## 🛠 Why Use Clustering?

- To **scale** a Node.js app across **multiple CPU cores**.
- Improves **performance and reliability** for high-traffic applications.
- If one worker crashes, others keep running — improves **fault tolerance**.

---

## ⚙️ How It Works

1. Master process runs first.
2. Master forks **multiple worker processes** using `cluster.fork()`.
3. All workers can share the same server port.
4. Each worker is an independent process with its own memory.

---

## 📑 Cluster Architecture

               +------------------+
               |  Master Process  |
               +------------------+
                       |
       +---------------+---------------+
       |               |               |
+----------------+ +----------------+ +----------------+
| Worker Process | | Worker Process | | Worker Process |
+----------------+ +----------------+ +----------------+



---

## ✅ Real-Life Use Case
- Load balancing HTTP servers.

- CPU-intensive tasks like image processing.

- High-concurrency APIs (e.g., chat servers, analytics).


## 📈 Benefits
- Utilizes all CPU cores.

- Improved performance under heavy load.

- Crash isolation — if one worker fails, others continue.

## ⚠️ Limitations

| Issue                | Explanation                                                                                         |
| -------------------- | --------------------------------------------------------------------------------------------------- |
| **Shared state**     | Workers have separate memory — need inter-process communication for shared data.                    |
| **Complexity**       | Debugging and managing multiple processes is harder.                                                |
| **Session handling** | Sticky sessions or external session stores are needed for user state in load-balanced environments. |

## 🔌 Inter-Process Communication (IPC)
- Use worker.send() and process.on('message') to pass messages between master and workers.

// Master
worker.send({ msg: 'Hello Worker' });

// Worker
process.on('message', (msg) => {
  console.log(msg);
});

## 📌 Summary
- The Cluster module helps Node.js apps scale on multi-core systems.

- Each worker is a separate process that shares the server port.

- Essential for building scalable and fault-tolerant backend systems.

## 📌 Summary Table
| Term                 | Meaning                                          |
| -------------------- | ------------------------------------------------ |
| Master               | Main process that manages all workers            |
| Worker               | Child process that handles actual HTTP requests  |
| `fork()`             | Used by master to create new worker processes    |
| `os.cpus()`          | Returns number of logical CPU cores              |
| `cluster.isMaster`   | True if the current process is the master        |
| `cluster.on('exit')` | Used to detect when a worker dies and restart it |



## 🧑‍💻 Basic Implementation

```js
const cluster = require('cluster');
const http = require('http');
const os = require('os');

const numCPUs = os.cpus().length;

if (cluster.isMaster) {
  console.log(`Master ${process.pid} is running`);

  // Fork workers.
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  // Optional: Restart workers on exit
  cluster.on('exit', (worker) => {
    console.log(`Worker ${worker.process.pid} died`);
    cluster.fork();
  });
} else {
  // Workers can share the same HTTP server
  http.createServer((req, res) => {
    res.writeHead(200);
    res.end(`Handled by worker ${process.pid}`);
  }).listen(3000);

  console.log(`Worker ${process.pid} started`);
}
