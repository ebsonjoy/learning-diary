# 📘 MongoDB - Capped Collection


## 🔍 What is a Capped Collection....?

- A **capped collection** is a fixed-size collection that automatically overwrites the oldest entries when it reaches the maximum size.
- It maintains the **insertion order**.
- Useful for storing **logs, cache, or real-time streaming data**.

## ✅ Key Features:

- Fixed size (specified in bytes or documents).
- Automatically removes oldest documents (no manual deletion needed).
- Insertion-only (you can’t delete or update to a bigger size).
- Fast writes, as MongoDB doesn't need to move documents.

## ⚙️ How to Create One:

```js
db.createCollection("logs", {
  capped: true,
  size: 100000,   // Size in bytes
  max: 1000       // (Optional) Max number of documents
});


db.logs.isCapped()     // Check if a collection is capped