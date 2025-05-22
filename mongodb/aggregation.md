# 📘 MongoDB - Aggregation

## 🔍 What is Aggregation?

Aggregation is a powerful feature in MongoDB to:
✅ Process data
✅ Transform data
✅ Perform operations like filtering, grouping, sorting, joining, projecting

🔧 It works like a **data pipeline** with multiple stages.


## 🧱 Common Aggregation Stages

| Stage           | Purpose                                      |
|------------------|----------------------------------------------|
| $match           | Filter documents (like WHERE in SQL)         |
| $project         | Include/exclude/rename fields                |
| $group           | Group documents and apply operations         |
| $sort            | Sort the output                              |
| $limit           | Limit the number of documents                |
| $skip            | Skip a number of documents                   |
| $lookup          | Join with another collection (like SQL JOIN) |
| $unwind          | Deconstruct arrays into separate documents   |
| $addFields       | Add new fields to documents                  |
| $count           | Count number of documents                    |
| $replaceRoot     | Replace the document root                    |
| $facet           | Perform multiple aggregations at once        |

## 📂 Example Collection: users
```js
{
  _id: ObjectId("..."),
  name: "Alice",
  age: 25,
  city: "Mumbai",
  hobbies: ["reading", "traveling"]
}

📌 $match - Filter Documents

db.users.aggregate([
  { $match: { age: { $gt: 20 } } }
])

📌 $project - Include Specific Fields

db.users.aggregate([
  { $project: { name: 1, age: 1, _id: 0 } }
])

📌 $group - Grouping and Aggregation

db.users.aggregate([
  { $group: { _id: "$city", total: { $sum: 1 } } }
])

📌 $sort - Sorting

db.users.aggregate([
  { $sort: { age: -1 } }
])

📌 $lookup - Join Collections

db.orders.aggregate([
  {
    $lookup: {
      from: "users",
      localField: "userId",
      foreignField: "_id",
      as: "userInfo"
    }
  }
])

📌 $unwind - Split Array Elements

db.users.aggregate([
  { $unwind: "$hobbies" }
])

📌 $addFields - Add Computed Fields

db.users.aggregate([
  { $addFields: { isAdult: { $gte: ["$age", 18] } } }
])

📌 $facet - Multi-Pipeline Aggregation

db.users.aggregate([
  {
    $facet: {
      "AgeAbove20": [{ $match: { age: { $gt: 20 } } }],
      "SortedByName": [{ $sort: { name: 1 } }]
    }
  }
])

```
## 📌 Use Cases of Aggregation:

• Analytics dashboards
• Real-time report generation
• Joining multiple collections
• Data transformation & reshaping
• Filtering & grouping large datasets

## 🧠 Summary:

✔ Aggregation = pipeline of transformations
✔ Each stage changes or filters the data
✔ Used for advanced queries and reporting
✔ $match → $group → $project → $sort → $lookup etc.

