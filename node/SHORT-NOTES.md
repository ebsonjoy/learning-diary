# Topics
1. What is Node.js?
2. process.nextTick()
3. API Versioning
4. app.all()
5. OPTIONS
6. REPL in Node.js
7. app.use() in Express.js
8. package-lock.json
9. Rate Limiting
10. Content Negotiation
11. Morgan
12. HTTP OPTIONS Method
13. Error-First Callback
14. Query Params vs Path Params
15. CORS (Cross-Origin Resource Sharing)
16. Preflight Request

## 1.What is Node.js?
Node.js is a JavaScript runtime built on Chrome's V8 engine. It allows you to run JavaScript on the server side. Node.js uses a non-blocking, event-driven architecture, which makes it efficient and suitable for scalable network applications.

---

## 2.process.nextTick()
`process.nextTick()` is used to schedule a callback function to be invoked in the next iteration of the event loop, **before** any I/O tasks. It's useful for deferring execution without waiting for external resources.

```js
console.log('Start');
process.nextTick(() => {
  console.log('Next Tick Callback');
});
console.log('End');

O/P

Start
End
Next Tick Callback

```
## 3.API Versioning
- API versioning is a strategy to manage changes in your API without breaking existing client applications. Common versioning methods include:
- URL-based: /api/v1/users
- Header-based: Accept: application/vnd.myapp.v1+json
- Query param: /api/users?version=1
---
## 4.app.all()
- app.all() in Express is used to handle all HTTP methods (GET, POST, PUT, DELETE, etc.) for a specific route. It’s helpful for logging, authentication, or pre-checks.

```js
app.all('/api', (req, res, next) => {
  console.log('Middleware for all methods');
  next();
});
```
---
## 5.OPTIONS
- The OPTIONS method is used to describe the communication options for the target resource. It is often used in CORS (Cross-Origin Resource Sharing) to check what HTTP methods and headers are allowed before the actual request.

```js
app.options('/api', (req, res) => {
  res.set('Allow', 'GET,POST,OPTIONS');
  res.sendStatus(200);
});
```
---
## 6.REPL in Node.js

REPL stands for **Read-Eval-Print Loop**. It's a built-in Node.js environment used to quickly run and test JavaScript code directly from the terminal.

### REPL Components:
- **Read**: Reads user input.
- **Eval**: Evaluates the input.
- **Print**: Prints the result.
- **Loop**: Repeats the process.

### How to Start:
Open terminal and type:
```bash
node
> 2 + 3
5
> const name = 'Ebson';
> name
'Ebson'
```
### REPL Commands:
- help – Show all commands

- exit – Exit REPL

- clear – Clear the current context

- save filename – Save REPL session to a file

- load filename – Load code from a file into REPL

---

## 7.app.use() in Express.js

`app.use()` is a method in Express.js used to **register middleware**. Middleware functions are functions that have access to the request (`req`), response (`res`), and the next middleware function (`next`).

### Purpose:
- Execute code for every request
- Modify request/response objects
- End the request-response cycle
- Call the next middleware in the stack

### Syntax:
```js
app.use([path], callback)
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```
---

# 8.package-lock.json

## What is it?
`package-lock.json` is a file **automatically created by npm** when you run `npm install`.

It records the **exact versions** of every installed package (and their dependencies).


## Why is it used?
- To **lock** the installed package versions.
- Ensures that **everyone installs the same versions** in every environment (dev, test, prod).
- Helps avoid bugs caused by version differences.


## Key Points:
- It works with `package.json`, but provides **more detailed version info**.
- It should be **committed to Git** (version control).
- If you delete it and run `npm install`, versions might change (based on semver ranges in `package.json`).


## Example:
You have this in `package.json`:
```json
"axios": "^1.4.0"
// But package-lock.json might lock it to:
"version": "1.4.2"
// So even if a new version 1.5.0 comes out, you will still get 1.4.2.
```
## Summary:
- ✅ Tracks exact versions of installed packages

- ✅ Makes installs consistent across machines

- 🚫 Do not edit manually

---

# 9.Rate Limiting

## What is it?
**Rate limiting** is a technique used to **control how many requests** a user or client can make to a server **within a specific time period**.


## Why is it used?
- ✅ To **prevent abuse** (e.g., spamming or DDoS attacks)
- ✅ To **protect server resources**
- ✅ To **improve performance** and **fair usage**


## Where is it used?
- APIs
- Login endpoints
- Form submissions
- Any server route that needs protection


## Example:
Allow **100 requests per user per 15 minutes**. If the limit is reached, block or delay further requests.


## In Express (with middleware):
```js
const rateLimit = require("express-rate-limit");

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100 // limit each IP to 100 requests
});

app.use(limiter);

```
## Summary:
- ✅ Limits request count per user/IP

- 🛡️ Improves security and stability

- ⚙️ Common in API development

---

# 10.Content Negotiation

## What is it?
**Content negotiation** is a process where the **server selects the best response format** (like JSON, HTML, XML, etc.) based on what the **client requests**.


## Why is it used?
- To **serve different formats** of data depending on client needs.
- Useful for APIs that support multiple response types (e.g., JSON, XML).


## How does it work?
The client sends an `Accept` header in the request.

### Example:
```http
GET /user HTTP/1.1
Accept: application/json

// The server checks the Accept header and responds accordingly.
```
## Example in Express:

```js
app.get('/data', (req, res) => {
  res.format({
    'text/plain': () => res.send('Plain text'),
    'text/html': () => res.send('<h1>HTML</h1>'),
    'application/json': () => res.json({ message: 'JSON' })
  });
});
```
## Summary:
- 🧠 Server chooses response format based on client's request.

- 📄 Controlled by the Accept header.

- 📦 Common in REST APIs for supporting multiple data types.

---

# 11.Morgan

## What is Morgan?
**Morgan** is a **middleware for Node.js and Express** used for **logging HTTP requests** in the terminal.


## Why is it used?
- ✅ To monitor incoming requests
- ✅ Helps with **debugging and development**
- ✅ Shows useful info like method, URL, status code, and response time


## How to install:
```js
// npm install morgan
// How to use in Express:

const express = require('express');
const morgan = require('morgan');
const app = express();

app.use(morgan('dev')); // logs request details
```
## Common formats:

- 'dev': colored, concise output (used in development)

- 'combined': standard Apache-style logs

- 'tiny': minimal output

## Summary:
- 📋 Logs all HTTP requests

- 🛠 Useful in development and debugging

- 🔧 Easy to plug into Express apps

---

# 12.HTTP OPTIONS Method

## What is it?
**HTTP OPTIONS** is an HTTP method used to **check what HTTP methods** (like GET, POST, PUT, etc.) are **allowed by the server** on a specific resource (URL).


## Why is it used?
- ✅ To know which operations are supported on a resource
- ✅ Often used in **CORS (Cross-Origin Resource Sharing)** preflight requests
- ✅ Helps browsers **verify permissions** before making actual requests


## Example:
```http
OPTIONS /api/user HTTP/1.1
Host: example.com

// Server response:

HTTP/1.1 204 No Content
Allow: GET, POST, PUT

```
## In Express (handling OPTIONS request):

```js
app.options('/api/user', (req, res) => {
  res.set('Allow', 'GET, POST, PUT');
  res.sendStatus(204);
});
```
## Summary:
- 🧪 Checks allowed HTTP methods on a route

- 🔐 Commonly used in CORS preflight checks

- 📡 Does not return data, only metadata about the API

---

# 13.Error-First Callback

## What is it?
An **error-first callback** is a function pattern in Node.js where the **first argument is always an error**, and the second is the **result/data**.

---

## Why is it used?
- ✅ To handle **errors and results** in asynchronous functions
- ✅ Follows a standard way in Node.js for **error handling**

---

## Syntax:
```js
function callback(err, result) {
  if (err) {
    // handle the error
  } else {
    // use the result
  }
}
```
---
# 14.Query Params vs Path Params

## What are they?
Both are used to **send data in URLs**, but they are used in **different ways**.

---

## 📌 Path Params:
- Part of the **URL path**
- Used to **identify a specific resource**
- Defined using `:paramName`

### Example:
```js
// Express route
app.get('/user/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});

// URL: /user/123 → id = 123

```

## 📌 Query Params:
- Part of the URL after the ?

- Used to filter or sort data

- Not required

### Example:

```js
// Express route
app.get('/search', (req, res) => {
  const keyword = req.query.q;
  res.send(`Searching for: ${keyword}`);
});

// URL: /search?q=watch → q = watch

```

## 🔍 Summary:

| Feature        | Path Params       | Query Params         |
| -------------- | ----------------- | -------------------- |
| Format         | `/user/:id`       | `/search?q=watch`    |
| Usage          | Identify resource | Filter, sort, search |
| Access in code | `req.params`      | `req.query`          |

---

# 15.CORS (Cross-Origin Resource Sharing)

## What is CORS?
**CORS** is a **security feature** in browsers that controls whether a web page can **make requests to a different domain** than the one it was loaded from.


## Why is it used?
- ✅ To **protect users** from unwanted cross-origin requests
- ✅ To allow **safe communication** between frontend and backend on different domains


## Common Example:
- Frontend: `http://localhost:3000`
- Backend: `http://localhost:5000`

By default, the browser **blocks the request** unless the backend allows it using CORS headers.


## How to enable CORS in Express:
```js
const cors = require('cors');
app.use(cors());

// You can also allow only specific origins:

app.use(cors({
  origin: 'http://localhost:3000'
}));

```
## Summary:
- 🌐 Allows or blocks requests between different origins

- 🔒 Controlled by the browser

- ✅ Must be enabled on the server

---


# 16.Preflight Request

## What is it?
A **preflight request** is an automatic HTTP request sent by the **browser before the actual request**, to **check if the server allows the real request**.


## When does it happen?
- When using **non-simple HTTP methods** like `PUT`, `DELETE`, or `PATCH`
- When sending **custom headers**
- When sending **non-plain data** (like JSON)


## How it works:
1. Browser sends a `OPTIONS` request first
2. Server responds with allowed methods, headers, and origin
3. If allowed, browser sends the **real request**


## Example (browser sends):
```http
OPTIONS /api/data HTTP/1.1
Origin: http://localhost:3000
Access-Control-Request-Method: PUT

// Server responds:

HTTP/1.1 204 No Content
Access-Control-Allow-Origin: http://localhost:3000
Access-Control-Allow-Methods: PUT

```
## Why is it used?

- 🔐 To protect servers from unauthorized cross-origin requests

- ✅ Ensures CORS rules are followed before sending sensitive data

## Summary:
- 🚦 Pre-check done using OPTIONS before sending real request

- 🛡️ Triggered by complex cross-origin requests

- ✅ Helps browsers enforce CORS securely

---

