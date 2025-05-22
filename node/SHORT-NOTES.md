# Node.js Notes

## 1. What is Node.js?
Node.js is a JavaScript runtime built on Chrome's V8 engine. It allows you to run JavaScript on the server side. Node.js uses a non-blocking, event-driven architecture, which makes it efficient and suitable for scalable network applications.

---

## 2. process.nextTick()
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
## 3. API Versioning
- API versioning is a strategy to manage changes in your API without breaking existing client applications. Common versioning methods include:
- URL-based: /api/v1/users
- Header-based: Accept: application/vnd.myapp.v1+json
- Query param: /api/users?version=1
---
## 4. app.all()
- app.all() in Express is used to handle all HTTP methods (GET, POST, PUT, DELETE, etc.) for a specific route. It’s helpful for logging, authentication, or pre-checks.

```js
app.all('/api', (req, res, next) => {
  console.log('Middleware for all methods');
  next();
});
```
---
## 5. OPTIONS
- The OPTIONS method is used to describe the communication options for the target resource. It is often used in CORS (Cross-Origin Resource Sharing) to check what HTTP methods and headers are allowed before the actual request.

```js
app.options('/api', (req, res) => {
  res.set('Allow', 'GET,POST,OPTIONS');
  res.sendStatus(200);
});
```
---
## 6. REPL in Node.js

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

## 7. app.use() in Express.js

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