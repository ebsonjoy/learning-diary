# 📦 Node.js Middleware
🗓️ Date: 2025-05-19

# 🔍 What is Middleware?

- Middleware is a function that has access to:
    - req (request)
    - res (response)
    - next (function to pass control to the next middleware)

- It sits between the raw request and the final route handler.
- Used mainly in Express.js.

Syntax:
    (req, res, next) => { ...next() }

# ✅ Definition of Middleware

Middleware in Express.js is a function that executes during the request-response cycle. It has access to the request (req), the response (res), and the next() function, which passes control to the next middleware or route handler.

# 🎯 Why Use Middleware?

✅ Code reusability (modular)
✅ DRY principle (Don't Repeat Yourself)
✅ Handle repetitive tasks like:
   - Logging
   - Authentication
   - Validation
   - Error handling
✅ Pre-process requests before reaching routes

# 📚 Types of Middleware

| Type                 | Description & Example Usage                 |
|----------------------|---------------------------------------------|
| Application-level    | Specific to your app (e.g., logging)        |
| Router-level         | Works only on a specific route              |
| Built-in             | Provided by Express (like express.json())   |
| Third-party          | External like `cors`, `morgan`, `helmet`   |
| Error-handling       | Used to handle errors in a centralized way  |
| Custom               | You create them based on your logic         |

# 🛠️ Application-Level Middleware Example

```js
const express = require('express');
const app = express();

// Custom logger middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();  // Go to next middleware or route
});

app.get('/', (req, res) => {
  res.send('Hello Middleware!');
});

app.listen(3000);

```

# 🧭 Router-Level Middleware Example
```js
const router = express.Router();

router.use((req, res, next) => {
  console.log('Router-level middleware triggered');
  next();
});

router.get('/user', (req, res) => {
  res.send('User Route');
});

app.use('/api', router);

```

# 🧪 Built-in Middleware Example
```js
app.use(express.json()); // Parses JSON request bodies
```

# 🌍 Third-party Middleware Example
```js
const cors = require('cors');
const morgan = require('morgan');

app.use(cors());      // Enable CORS
app.use(morgan('dev')); // HTTP logger
```
# 🛑 Error Handling Middleware
```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
# 🏘️ Real-life Use Cases

- Auth middleware to check if user is logged in
- Rate limiter to block abusive requests
- Sanitize inputs to prevent XSS
- Log request details to a file (logging)
- Enable CORS on an API

# ✅ Advantages

- Modular and reusable
- Improves code organization
- Easy to maintain and debug
- Centralized error handling

# ⚠️ Disadvantages

- Middleware order matters (can cause bugs)
- Improper `next()` can break request flow
- Too many middlewares = harder to trace issues


