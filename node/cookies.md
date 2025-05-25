# 🍪 Cookies in Node.js

## 📌 What is a Cookie?

A **cookie** is a small piece of data stored on the client side (browser) and sent to the server with every HTTP request. It's commonly used for:

- Storing user session data
- Remembering user preferences
- Keeping users logged in

---

## 🧠 How Cookies Work

1. Server sends a cookie using the `Set-Cookie` header.
2. Browser stores the cookie.
3. On every future request, the browser sends the cookie back to the server.

---

## 🚀 How to Use Cookies in Node.js (with Express)

### ✅ Step 1: Install `cookie-parser`

```js
//npm install cookie-parser

//✅ Step 2: Setup in app.js or server.js

const express = require('express');
const cookieParser = require('cookie-parser');
const app = express();

app.use(cookieParser());

// 🍪 Set a Cookie

app.get('/set-cookie', (req, res) => {
  res.cookie('username', 'Ebson');
  res.send('Cookie set');
});


// This sets a cookie named username with value Ebson.

// 🔍 Read/Get a Cookie

app.get('/get-cookie', (req, res) => {
  const user = req.cookies.username;
  res.send(`Hello ${user}`);
});

// ❌ Clear a Cookie

app.get('/clear-cookie', (req, res) => {
  res.clearCookie('username');
  res.send('Cookie cleared');
});
```

## ⚙️ Cookie Options
```js
res.cookie('token', 'abc123', {
  maxAge: 1000 * 60 * 60, // 1 hour
  httpOnly: true,         // not accessible from client-side JS
  secure: true,           // only sent over HTTPS
});
```
| Option     | Description                                          |
| ---------- | ---------------------------------------------------- |
| `maxAge`   | Expiration time in milliseconds                      |
| `httpOnly` | Hides the cookie from JavaScript (`document.cookie`) |
| `secure`   | Sends cookie only on HTTPS                           |
| `path`     | URL path where cookie is valid                       |

