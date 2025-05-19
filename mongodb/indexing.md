# 📘 MongoDB - Indexing

**Date:** 2025-05-19

---

## 🔍 What is Indexing?

- **Indexing** improves the speed of read operations (queries).
- Without an index, MongoDB performs a **collection scan**.
- Indexes reduce CPU, memory, and disk I/O during lookups.

---

## ✅ Types of Indexes

| Index Type         | Description                          |
|--------------------|--------------------------------------|
| **Default _id**     | Automatically created on `_id`       |
| **Single Field**    | Index on one field                   |
| **Compound**        | Index on two or more fields          |
| **Multikey**        | Index on array fields                |
| **Text**            | Full-text search                     |
| **Hashed**          | Used in sharding                     |
| **Geospatial 2d**   | For flat geometry coordinates        |
| **Geospatial 2dsphere** | For spherical (Earth-like) geometry |
| **TTL**             | Time-To-Live index to auto-delete documents |
| **Wildcard**        | Index all fields dynamically         |
| **Partial**         | Index subset of documents only       |
| **Unique**          | Enforce uniqueness on a field        |

---

## 📂 Sample Collection: `users`

```js
db.users.insertOne({
  name: "Alice",
  age: 25,
  email: "alice@example.com",
  interests: ["reading", "coding"],
  bio: "Loves JavaScript and MongoDB.",
  location: {
    type: "Point",
    coordinates: [77.5946, 12.9716]
  },
  createdAt: new Date()
});


## 📌 1. Single Field Index
// Ascending
db.users.createIndex({ name: 1 });
// Descending
db.users.createIndex({ age: -1 });


## 📌 2. Compound Index
db.users.createIndex({ name: 1, age: -1 });


## 📌 3. Multikey Index (Array Field)
db.users.createIndex({ interests: 1 });


## 📌 4. Text Index
db.users.createIndex({ bio: "text" });
// Example query
db.users.find({ $text: { $search: "MongoDB" } });


## 📌 5. Hashed Index
db.users.createIndex({ email: "hashed" });


## 📌 6. Geospatial Index (2dsphere)

db.users.createIndex({ location: "2dsphere" });

// Nearby users query
db.users.find({
  location: {
    $near: {
      $geometry: {
        type: "Point",
        coordinates: [77.5946, 12.9716]
      },
      $maxDistance: 5000
    }
  }
});


## 📌 7. TTL (Time-To-Live) Index
// Automatically delete documents after 3600 seconds (1 hour)
db.users.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 });


## 📌 8. Wildcard Index
db.users.createIndex({ "$**": 1 });


## 📌 9. Partial Index
db.users.createIndex(
  { age: 1 },
  { partialFilterExpression: { age: { $gt: 18 } } }
);


## 📌 10. Unique Index
db.users.createIndex({ email: 1 }, { unique: true });


🧪 View Indexes
db.users.getIndexes();

❌ Drop Index
db.users.dropIndex("email_1");
