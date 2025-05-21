# 🔄1. Difference Between Child Process and Cluster in Node.js

## 📌 1. Overview

| Feature             | Child Process                             | Cluster                                    |
|---------------------|--------------------------------------------|--------------------------------------------|
| Purpose             | Run any script in a separate process       | Scale Node.js servers using multiple CPUs   |
| Module              | require('child_process')                   | require('cluster')                          |
| Use Case            | Background tasks, running shell/Python/etc | High-traffic Node apps, HTTP server scaling |
| Communication       | Manual (stdin/stdout/send)                 | Built-in master ↔ workers messaging         |
| Load Balancing      | ❌ No                                       | ✅ Yes (Round Robin / OS scheduling)        |
| Codebase Sharing    | ❌ Can run different scripts                | ✅ Same Node app across workers             |


## 📊 2. Key Differences Summary

| Property               | child_process               | cluster                     |
|------------------------|-----------------------------|-----------------------------|
| Run Shell Commands     | ✅                          | ❌                          |
| Run Node.js Servers    | ✅                          | ✅                          |
| Built-in Load Balancer | ❌                          | ✅                          |
| Used for Parallel Jobs | ✅ (flexible jobs)           | ❌ (used only for server)    |
| Share Same App Code    | ❌                          | ✅                          |


## 💡 3. Real Life Use

Use `child_process` to:
  - Run a Python script for data processing
  - Perform image compression in background
  - Run OS commands like `ffmpeg`, `ls`, etc.

Use `cluster` to:
  - Handle 1000s of HTTP requests per second
  - Utilize all CPU cores efficiently
  - Improve scalability of a Node.js server


---


# 🌐2. HTTP vs HTTPS

## 🔹 What is HTTP?

- HTTP (HyperText Transfer Protocol) is the protocol used to transfer data over the web.
- Works on port 80 by default.
- Communication is in plain text (not secure).
- Used for websites without encryption.

## 🔹 What is HTTPS?

- HTTPS (HTTP Secure) is HTTP + SSL/TLS encryption.
- Works on port 443 by default.
- Encrypts data between client and server.
- Used for secure websites (online banking, e-commerce, etc).

## ⚙️ How HTTPS Works?

1. Client requests HTTPS connection.
2. Server sends SSL/TLS certificate.
3. Client verifies certificate authority (CA).
4. Client and server establish encrypted connection.
5. Data exchanged securely.

## 📊 Key Differences

| Feature         | HTTP                         | HTTPS                        |
|-----------------|------------------------------|------------------------------|
| Security        | No encryption (plain text)   | Encrypted (SSL/TLS)           |
| Port            | 80                           | 443                          |
| URL Prefix      | http://                     | https://                    |
| Data Integrity  | No                          | Yes                         |
| Performance     | Slightly faster              | Slight overhead due to encryption |
| SEO Ranking     | Lower                       | Higher (preferred by Google) |

## ✅ Advantages of HTTPS

- Data privacy and security.
- Prevents man-in-the-middle attacks.
- Builds user trust.
- Required for PCI compliance (credit card info).
- Better SEO rankings.

## ⚠️ Disadvantages of HTTPS

- Slightly slower due to encryption overhead.
- Requires SSL certificates (can be free or paid).
- More setup complexity.

## 🔧 Real Life Example

- Online banking sites use HTTPS to protect user data.
- E-commerce websites use HTTPS to secure payment info.
- Social media platforms use HTTPS to protect user accounts.

---

# ⚙️3. Macrotasks vs Microtasks in Node.js

## 🔍 What are Tasks in Node.js Event Loop?

- Node.js runs JavaScript code using an event loop.
- Tasks are units of work scheduled to run.
- Tasks are categorized into:
    • Macrotasks (Tasks)
    • Microtasks (Jobs)

## 📝 Macrotasks (Tasks):

- Examples: setTimeout, setInterval, setImmediate, I/O operations, timers.
- Macrotasks are scheduled in different phases of the event loop.
- After executing a macrotask, Node.js processes all microtasks before moving to the next macrotask.
- Macrotasks have lower priority than microtasks.

## 📝 Microtasks (Jobs):

- Examples: Promises (.then, .catch, .finally), process.nextTick(), queueMicrotask().
- Microtasks run immediately after the currently executing script or macrotask.
- Microtasks have higher priority and run before the next macrotask.
- They help to perform operations that need to happen ASAP after the current code.


## 📊 Task Flow Summary

1. Execute current script (synchronous code).
2. Run all microtasks queue until empty.
3. Pick and execute one macrotask.
4. Repeat steps 2 and 3.


## 🔄 Visual Flow:

[ Script Execution ]
        ↓
[ Microtasks (Promises, nextTick) ] → run all
        ↓
[ One Macrotask (setTimeout, I/O, setImmediate) ]
        ↓
[ Microtasks ] → run all
        ↓
[ Next Macrotask ]

## 💡 Examples:
```js
setTimeout(() => console.log('Macrotask: setTimeout'), 0);

Promise.resolve().then(() => console.log('Microtask: Promise.then'));

process.nextTick(() => console.log('Microtask: process.nextTick'));

console.log('Synchronous: main script');

// Output order:
// Synchronous: main script
// Microtask: process.nextTick
// Microtask: Promise.then
// Macrotask: setTimeout

```

## 🔑 Key Points:

- process.nextTick() runs before other microtasks.
- Microtasks run after every macrotask and script.
- Macrotasks include timers and I/O callbacks.
- Understanding task priority helps prevent unexpected async behavior.


## 📌 Why It Matters?

- Helps write efficient async code.
- Avoids blocking event loop.
- Ensures timely execution of promises & callbacks.

---

# 🔐4. Authentication vs Authorization

## 🧾 Definitions

👉 Authentication:
   - Process of **verifying identity**.
   - Confirms **who the user is**.
   - Usually involves login credentials (username/password, OTP, biometrics).
   - Example: "Are you the real user?"

👉 Authorization:
   - Process of **verifying access**.
   - Confirms **what resources a user can access**.
   - Happens **after authentication**.
   - Example: "Now that you are authenticated, what are you allowed to do?"

## 🔄 Flow Summary:

[ User Login Form ]
        ↓
🔐 Authentication (verify user credentials)
        ↓
✅ Authenticated → Issue token/session
        ↓
🔓 Authorization (check access rights using role/permissions)
        ↓
📄 Allow/deny access to specific routes/pages/resources


## 🧠 Real-Life Analogy:

🪪 Authentication → Showing your ID at a security gate.
🔑 Authorization → Being allowed into specific rooms based on your ID.


## 🔍 Key Differences:

| Feature           | Authentication                   | Authorization                    |
|------------------|-----------------------------------|----------------------------------|
| Purpose          | Verify identity                   | Verify access level              |
| Happens when?    | Before authorization              | After authentication             |
| Based on         | Credentials (password, token)     | Permissions, roles               |
| Example          | Login with email & password       | Can access admin panel or not    |
| Output           | Logged-in user                    | Access granted/denied            |

## 🛠️ Implementation Examples in Web App (Node.js):

🧾 Authentication:
   - Check user credentials from DB
   - Issue JWT or session cookie
   - Store token in client

🔓 Authorization:
   - Use middleware to check token
   - Check user role (admin, user, moderator)
   - Allow or restrict access to specific API routes


## ✔️ Advantages:

✅ Authentication:
   - Ensures only real users access the system.
   - Helps track user actions.

✅ Authorization:
   - Keeps data secure and private.
   - Allows role-based access control.

❌ Common Mistakes:
   - Skipping authorization after authentication.
   - Hardcoding permissions (bad practice).

---

# 🧵5. Concurrency vs Parallelism

## 📘 Definitions:

🔄 Concurrency:
   - The ability of a system to **handle multiple tasks at once**, by switching between them.
   - Tasks start, run, and complete in **overlapping time periods**.
   - Think of it as **multitasking**, even on a single core CPU.

⚡ Parallelism:
   - The ability to **execute multiple tasks simultaneously**, at the **same exact time**.
   - Requires **multiple processors or cores**.
   - Think of it as **true simultaneous execution**.


## 🧠 Real-Life Analogy:

🍽️ Concurrency:
   - A single waiter handles multiple tables by moving between them quickly.
   - Only one table served at a time, but all get served.

🍽️ Parallelism:
   - Multiple waiters serve multiple tables at the same time.
   - True simultaneous service.


## 🧵 Concurrency (Example - JavaScript / Node.js):
   - Node.js handles multiple requests using an event loop (non-blocking I/O).
   - Even with a single-threaded model, it can handle many connections concurrently.

## ⚙️ Parallelism (Example - Node.js with Worker Threads / Cluster):
   - Worker threads or clustering allows real parallel execution using multiple cores.

## 📊 Comparison Table:

| Feature           | Concurrency                         | Parallelism                         |
|------------------|-------------------------------------|-------------------------------------|
| Definition        | Tasks are executed one after another, but appear simultaneous | Tasks are executed truly at the same time |
| Hardware Needs    | Can work on single core             | Needs multi-core processors         |
| Example           | Node.js event loop, async/await     | Worker Threads, Clustering          |
| Best For          | I/O-bound tasks                     | CPU-bound tasks                     |
| Execution         | Interleaving tasks                  | Simultaneous task execution         |

## 🛠️ Where It Matters in Node.js:

✅ Concurrency:
   - Handled through event loop, async/await, Promises, non-blocking I/O.

✅ Parallelism:
   - Handled using modules like:
     - `cluster`
     - `worker_threads`
     - `child_process`


## ✅ Advantages:

🔄 Concurrency:
   - Efficient use of resources.
   - Great for handling many users (web servers, APIs).

⚡ Parallelism:
   - Reduces time for heavy CPU computations.
   - Ideal for number crunching, image processing, etc.

❌ Disadvantages:

🔄 Concurrency:
   - Harder to debug due to switching contexts.
   - Race conditions if not handled properly.

⚡ Parallelism:
   - More memory and CPU usage.
   - Needs synchronization between threads or processes.



# 🗂️6. localStorage vs sessionStorage

## 🔍 What are they?

➡️ Both are part of the Web Storage API.
➡️ They allow storing key-value pairs in the browser.
➡️ Data is stored in **string format only**.

## 📦 localStorage

• Stores data with **no expiration** time.
• Data persists even after the browser/tab is closed and reopened.
• Shared across all tabs/windows of the same origin.

🧪 Example:
localStorage.setItem("user", "Ebson");
localStorage.getItem("user");     // "Ebson"
localStorage.removeItem("user");  // Removes item
localStorage.clear();             // Clears all data

## 📦 sessionStorage

• Stores data for **only one session** (until tab/window is closed).
• Not shared across tabs/windows.
• Useful for temporary/session-based data.

🧪 Example:
sessionStorage.setItem("cart", "5 items");
sessionStorage.getItem("cart");     // "5 items"
sessionStorage.removeItem("cart");
sessionStorage.clear();

# 📘7. npm vs npx

## 🔍 What is npm?

📦 npm = Node Package Manager  
➡️ Used to install, update, and manage packages/modules for Node.js

🛠️ Common npm commands:

- $ npm init               # Create package.json
- $ npm install lodash     # Install a package locally
- $ npm install -g nodemon # Install globally
- $ npm uninstall axios    # Remove a package
- $ npm update             # Update all packages

📁 Local packages → Stored in ./node_modules
📁 Global packages → Stored in system path


## 🔍 What is npx?

⚡ npx = Node Package Executor  
➡️ Runs npm packages **without installing them** permanently

🧪 Example:

- $ npx create-react-app myapp
✅ Runs the package temporarily, no need to install globally

💡 Good for:
• Running CLI tools once
• Avoiding global pollution
• Always using the latest version

## 🆚 npm vs npx

| Feature         | npm                           | npx                                 |
|----------------|-------------------------------|--------------------------------------|
| Role            | Installs and manages packages | Executes a package directly          |
| Installs?       | Yes                           | No (runs & deletes after use)        |
| Scope           | Local or global               | Temporary use                        |
| Use Case        | Installing dependencies       | Running CLI tools/scripts easily     |

## 📦 Real Life Example

### 🎯 With npm (needs global install):
- $ npm install -g create-react-app
- $ create-react-app myapp

### 🎯 With npx (no install needed):
- $ npx create-react-app myapp

✅ Faster and cleaner with npx

## 🧠 Summary

✔ Use `npm` to install/manage packages  
✔ Use `npx` to run one-time or CLI tools  
✔ `npx` saves time, avoids global clutter  

