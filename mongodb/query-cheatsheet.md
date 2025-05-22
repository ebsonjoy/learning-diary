```js
db.users.find({})
[
  {
    "_id": ObjectId("1"),
    "name": "John Doe",
    "age": 28,
    "email": "john@example.com",
    "city": "New York"
  },
  {
    "_id": ObjectId("2"),
    "name": "Jane Smith",
    "age": 32,
    "email": "jane@example.com",
    "city": "Los Angeles"
  }
]
```
## 1. 🧮 Count All Documents
```js
db.users.countDocuments()

Returns the total number of documents in the users collection.

```
## 2. 🔤 Find Users Whose Name Starts with "J"
```js
db.users.find({ name: /^j/i })
```
## 3. 👴 Name and Age of Users Above 35, Sorted by Age
```js
db.users.find(
  { age: { $gt: 35 } },
  { _id: 0, name: 1, age: 1 }
).sort({ age: 1 })
```

## 4. 📊 Average Age of Users with Age > 40
```js
db.users.aggregate([
  { $match: { age: { $gt: 40 } } },
  {
    $group: {
      _id: null,
      averageAge: { $avg: "$age" }
    }
  }
])
```