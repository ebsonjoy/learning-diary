# 📘 JSON Web Token (JWT)

## 🔐 What is JWT?
JWT (JSON Web Token) is a standard for securely transmitting information between parties as a JSON object.
It is compact, URL-safe, and digitally signed. It’s most commonly used for authentication and authorization in web applications.

## 🧠 Why JWT?

Imagine this:
You log in to a website, and the server wants to remember who you are. One way is using sessions (stored in memory/database).
But in scalable applications (e.g., microservices or stateless APIs), storing sessions becomes a problem.

That’s where JWT comes in:

- ✅ Stateless (no need to store anything on the server)

- ✅ Compact and fast

- ✅ Secure with signature verification

## 📦 JWT Structure

A JWT consists of three parts, separated by dots (.):
```js
<Header>.<Payload>.<Signature>
```
### 🔹 1. Header
```js
{
  "alg": "HS256",
  "typ": "JWT"
}
```
- alg → the algorithm used for signing (e.g., HMAC SHA256)

- typ → type of the token, usually "JWT"

- 👉 Encoded using Base64Url

### 🔹 2. Payload (Claims)

- Contains the actual data (claims) we want to transmit:
```js
{
  "userId": "12345",
  "role": "admin",
  "email": "abc@example.com",
  "exp": 1712345678
}
```
There are 3 types of claims:

| Type           | Examples                                |
| -------------- | --------------------------------------- |
| **Registered** | `iss`, `exp`, `sub`, `aud`              |
| **Public**     | Custom claims like `userId`, `role`     |
| **Private**    | Internal-use claims (e.g., `x-app-key`) |


### 🔹 3. Signature

Created by encoding the header and payload, then signing them:

```js
HMACSHA256(
  base64UrlEncode(header) + "." + base64UrlEncode(payload),
  secret
)
```
- Prevents tampering

- Validates the token’s authenticity

## 🔄 JWT Workflow in Authentication

Client                          Server
  |                                 |
  | -- Login (email/password) -->   |
  |                                 |
  | <--  JWT Token (signed) ------  |
  |                                 |
  | -- Request with JWT -->         |
  |    (Authorization header)       |
  |                                 |
  | <-- Protected Resource -------- |


### Token is stored in:

- localStorage (⚠️ exposed to XSS)

- OR HTTP-only cookie (✅ more secure)

## ⚙️ Real Implementation (Node.js + Express)

### Step 1: Install

- npm install jsonwebtoken

### Step 2: Create Token (Login Route)

```js

const jwt = require('jsonwebtoken');

const token = jwt.sign(
  { userId: 'abc123', role: 'user' },
  'yourSecretKey',
  { expiresIn: '1h' }
);
```
### Step 3: Verify Token (Middleware)
```js
const jwt = require('jsonwebtoken');

function verifyToken(req, res, next) {
  const authHeader = req.headers.authorization;
  const token = authHeader && authHeader.split(" ")[1];
  
  if (!token) return res.status(403).send("Token missing");

  jwt.verify(token, "yourSecretKey", (err, decoded) => {
    if (err) return res.status(401).send("Invalid token");
    req.user = decoded;
    next();
  });
}
```
## ⚖️ Advantages of JWT

| ✅ Feature           | ✅ Benefit                                   |
| ------------------- | ------------------------------------------- |
| Stateless           | No need to store sessions server-side       |
| Compact             | Can be sent in headers, cookies             |
| Secure (signed)     | Tampering is detectable                     |
| Scalable            | Easy to use in microservices                |
| Expiration built-in | Auto-expiring tokens                        |
| Language-agnostic   | Works with any backend (Node, Python, etc.) |

## ❌ Disadvantages of JWT

| ❌ Limitation            | ⚠️ Description                                       |
| ----------------------- | ---------------------------------------------------- |
| No easy revocation      | Once issued, cannot force logout (without blacklist) |
| Token exposed if stolen | Store in `localStorage` → XSS risk                   |
| Can become large        | Payload grows → more bandwidth                       |
| Not encrypted           | Payload is readable → don’t store passwords!         |

