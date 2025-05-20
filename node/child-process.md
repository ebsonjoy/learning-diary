# 📘 Node.js – Child Process

**Date:** 2025-05-19

---

## 🧠 What is a Child Process?

- Node.js is **single-threaded** by default.
- To handle **CPU-intensive tasks**, Node provides a way to create **child processes**.
- Child processes allow you to **run multiple operations in parallel** without blocking the main event loop.

- ✅ Run other programs or scripts
- ✅ Run Node.js files as separate processes
- ✅ Perform CPU-heavy tasks without blocking the main thread
- ✅ Use Inter-Process Communication (IPC) to talk between parent and child

---

## 🛠️ Four Main Methods in `child_process`

| Method       | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `exec()`     | Runs a command in a shell and buffers the output                           |
| `execFile()` | Similar to `exec()`, but directly runs a file (better performance)         |
| `spawn()`    | Launches a new process with a given command; best for streaming large data |
| `fork()`     | Special case of `spawn()` to run another Node.js script with IPC enabled   |

---

## 🧩 Child Process Module

## 1️⃣ `exec()`

Used for simple shell commands.

### ✅ Example: Run `ls` or `dir`

```js
const { exec } = require('child_process');

exec('ls', (error, stdout, stderr) => {
  if (error) {
    console.error(`Error: ${error.message}`);
    return;
  }
  if (stderr) {
    console.error(`Stderr: ${stderr}`);
    return;
  }
  console.log(`Output:\n${stdout}`);
});

📌 Use Case: Good for commands like git, ls, pwd, etc.

```
# 2️⃣ execFile()

Runs a file directly (no shell, safer and faster).

✅ Example: Run a shell or executable file

```js
const { execFile } = require('child_process');

execFile('node', ['-v'], (error, stdout) => {
  if (error) throw error;
  console.log(`Node version: ${stdout}`);
});

📌 Use Case: Run a file like python myscript.py or node script.js.
```

# 3️⃣ spawn()

More powerful — allows you to stream stdout/stderr in real time.

✅ Example: Run a command with output streaming

```js

const { spawn } = require('child_process');

const child = spawn('ping', ['google.com']);

child.stdout.on('data', (data) => {
  console.log(`stdout: ${data}`);
});

child.stderr.on('data', (data) => {
  console.error(`stderr: ${data}`);
});

child.on('exit', (code) => {
  console.log(`Child process exited with code ${code}`);
});

📌 Use Case: When output is large or continuous (like video processing, logs, etc.)

```

# 4️⃣ fork()

Designed specifically for Node.js scripts with IPC (parent-child communication).

✅ Example: Parent communicates with child Node file

```js

// 📁 parent.js
const { fork } = require('child_process');

const child = fork('child.js');

child.send({ msg: 'Hello from parent' });

child.on('message', (data) => {
  console.log('Parent received:', data);
});


//📁 child.js 
process.on('message', (data) => {
  console.log('Child received:', data);
  process.send({ reply: 'Hello from child' });
});

```

# 🔁 Summary Table

| Method       | Shell | IPC | Stream Output | Use Case                           |
| ------------ | ----- | --- | ------------- | ---------------------------------- |
| `exec()`     | ✅     | ❌   | ❌ (Buffered)  | Run shell commands                 |
| `execFile()` | ❌     | ❌   | ❌             | Run executable files               |
| `spawn()`    | ✅/❌   | ❌   | ✅             | Long-running tasks or large output |
| `fork()`     | ❌     | ✅   | ✅             | Run Node.js child scripts          |

# 🧠 Real-World Use Cases

| Task                                  | Method to Use |
| ------------------------------------- | ------------- |
| Run system commands (like `ls`)       | `exec()`      |
| Execute a Node.js worker script       | `fork()`      |
| Run a Python or Bash script           | `execFile()`  |
| Monitor real-time logs                | `spawn()`     |
| Offload CPU-heavy task (like hashing) | `fork()`      |


# ✅ Conclusion
- child_process gives Node.js the power of multiprocessing.

- Use fork() for Node.js files and communication between processes.

- Use spawn() or exec() when dealing with external system tasks or commands.