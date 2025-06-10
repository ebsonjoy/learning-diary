## Using MongoDB Shell (mongosh)
- mongosh
## Show Databases
- show dbs
## Switch to (or Create) a Database
- use myDatabase
// If you do use myDatabase but don’t insert anything, MongoDB won’t show this database in show dbs
##  Create a Collection
Option 1: Implicitly (Auto-create on insert)

- db.myCollection.users({ name: "John", age: 25 })

Option 2: Explicitly (Manual creation)

- db.createCollection("myCollection")

```js
 Example Combined:
 use market          // Creates or switches to 'school' DB

db.createCollection("users")  // Creates a collection

db.users.insertMany([
  {
    name: "Bob",
    age: 30,
    email: "bob@example.com",
    hobbies: ["cricket", "movies"],
    address: { city: "Kannur", pincode: 670001 },
    isActive: true,
    createdAt: new Date()
  },
  {
    name: "Charlie",
    age: 22,
    email: "charlie@example.com",
    hobbies: ["reading", "football"],
    address: { city: "Thrissur", pincode: 680001 },
    isActive: false,
    createdAt: new Date()
  },
  {
    name: "Diana",
    age: 28,
    email: "diana@example.com",
    hobbies: ["chess", "painting"],
    address: { city: "Kochi", pincode: 682001 },
    isActive: true,
    createdAt: new Date()
  }
])

```
---
# QUERY

1. Count All
2. Name Starts with "J"
3. Name and Age of Users Above 35, Sorted by Age
4. Average Age of Users with Age > 40
5. Query to Remove city inside address
6. Rename Field address ➝ addss
7. Add createdAt Field Only to Documents That Don’t Have It
8. Find users having "reading" as a hobby(array)
9. Delete inactive users
10. 
11. 

---
```js
db.users.find({})
[
  {
    _id: ObjectId("1"),
    name: "Bob",
    age: 30,
    email: "bob@example.com",
    hobbies: ["cricket", "movies"],
    address: { city: "Kannur", pincode: 670001 },
    isActive: true,
    createdAt: new Date()
  },
  {
    _id: ObjectId("2"),
    name: "Charlie",
    age: 22,
    email: "charlie@example.com",
    hobbies: ["reading", "football"],
    address: { city: "Thrissur", pincode: 680001 },
    isActive: false,
    createdAt: new Date()
  },
  {
    _id: ObjectId("3"),
    name: "Diana",
    age: 28,
    email: "diana@example.com",
    hobbies: ["chess", "painting"],
    address: { city: "Kochi", pincode: 682001 },
    isActive: true,
    createdAt: new Date()
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
## 5. Query to Remove city inside address
```js
db.users.updateMany(
  {},
  { $unset: { "address.city": "" } }
)
```
## 6. Rename Field address ➝ addss
```js
db.users.updateMany(
  {},
  { $rename: { "address": "addss" } }
)
```
## 7. Add createdAt Field Only to Documents That Don’t Have It

```js
db.users.updateMany(
  { createdAt: { $exists: false } },  // Filter: documents without createdAt
  { $set: { createdAt: new Date() } } // Add current date and time
)
```
## 8. Find users having "reading" as a hobby
```js
db.users.find({ hobbies: "reading" })
```
## 9. Delete inactive users
```js
db.users.deleteMany({ isActive: false })
```
## 10. Array field

```js
// documents where both "chess" and "music" are present in the hobbies array

db.users.find({ hobbies: { $all: ["chess", "music"] } }) // chess AND music

// Matches if any of the values exist in the array (OR condition).

db.users.find({ hobbies: { $in: ["chess", "music"] } }) // chess OR music
```

