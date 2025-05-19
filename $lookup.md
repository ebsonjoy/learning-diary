# 📘 MongoDB - `$lookup` (Aggregation)

**Date:** 2025-05-19

---

## 🔍 What is `$lookup`?

- `$lookup` is used in **aggregation** to perform a **join** between two collections.
- It allows you to combine related data like SQL JOINs.

---

## 🧩 Syntax

```js
{
  $lookup: {
    from: "otherCollection",      // Target collection to join
    localField: "fieldInThis",    // Field in the current (local) collection
    foreignField: "fieldInOther", // Matching field in the other collection
    as: "joinedField"             // Output array field name
  }
}

🗃 Example Collections

users Collection

{
  _id: ObjectId("1"),
  name: "Alice",
  cityId: 101
}

cities Collection

{
  _id: 101,
  cityName: "Bangalore"
}


 Basic $lookup Example

db.users.aggregate([
  {
    $lookup: {
      from: "cities",
      localField: "cityId",
      foreignField: "_id",
      as: "cityDetails"
    }
  }
]);
🧾 cityDetails will be an array containing matched city object(s).

-------------------------------------------------------------------

📌 Advanced: Pipeline $lookup

can use a pipeline inside $lookup for more flexible matching:

{
  $lookup: {
    from: "cities",
    let: { city_id: "$cityId" },
    pipeline: [
      { $match: { $expr: { $eq: ["$_id", "$$city_id"] } } },
      { $project: { cityName: 1, _id: 0 } }
    ],
    as: "cityDetails"
  }
}

📂 Real Use Case
Join orders with users to show who made which order:

db.orders.aggregate([
  {
    $lookup: {
      from: "users",
      localField: "userId",
      foreignField: "_id",
      as: "userDetails"
    }
  },
  { $unwind: "$userDetails" },
  {
    $project: {
      orderId: 1,
      amount: 1,
      "userDetails.name": 1
    }
  }
]);

