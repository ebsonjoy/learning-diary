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
10. Array field
11. Find users whose email ends with @gmail.com
12.  Find users with exactly 2 hobbies
13. Find users whose hobbies do NOT include "coding"
14. Find users from "kannur" OR "kochi"
15.  Find users from "kannur" OR have "chess" as a hobby
16. Find active users AND (age > 25 OR city is "kochi")
17. Find users who do NOT have "movies" in hobbies ($ne)
18. Update users from "kannur" to include state: "Kerala"
19. Find users with hobbies in ["chess","music"] but not "coding"
20. Find users younger than 25 or older than 30.
21. Find users whose pincode is not "670001".
22. Find users who have "chess" as their first hobby.
23. Find users who have "reading" but not "chess".
24. Find users where the city is in lowercase (e.g., "kannur" vs "Kannur").
25. Find users where the pincode is a 6-digit number.
26. Find users whose city name contains "puram" (e.g., "Malappuram").
27. Create a text index on name and hobbies for keyword searches.
28. Find users with hobbies containing "read" or "chess".



### Aggregation
1. Count users with "reading" as a hobby
2. Group users by city and count them
3. Find the average age of users
4. Find the oldest user in each city.
5. Count the number of users per hobby (unwind hobbies first).
6. Find users with duplicate emails (assuming emails should be unique).

### updation 

1. Add "yoga" to the hobbies of all users older than 25.
2. Remove "movies" from Bob's hobbies.
3. Set isActive: false for users with no hobbies.
4. Increase the age of all users by 1 year.

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

## 11. Find users whose email ends with @gmail.com
```js
db.users.find({ email: /@gmail\.com$/ })
```
## 12. Find users with exactly 2 hobbies
```js
db.users.find({ hobbies: { $size: 2 } })
```
## 13. Find users whose hobbies do NOT include "coding" 
```js
db.users.find({ hobbies: { $nin: ["coding"] } })
```
## 14. Find users from "kannur" OR "kochi"
```js
db.users.find({ "address.city": { $in: ["kannur", "kochi"] } })
```
## 15.  Find users from "kannur" OR have "chess" as a hobby
```js
db.users.find({
  $or: [
    { "address.city": "kannur" },
    { hobbies: "chess" }
  ]
})
```
## 16. Find active users AND (age > 25 OR city is "kochi")
```js
db.users.find({
  isActive: true,
  $or: [
    { age: { $gt: 25 } },
    { "address.city": "kochi" }
  ]
})
```
## 17. Find users who do NOT have "movies" in hobbies ($ne)
```js
db.users.find({ hobbies: { $ne: "movies" } })
```
## 18. Update users from "kannur" to include state: "Kerala"
```js
db.users.updateMany(
  { "address.city": "kannur" },
  { $set: { "address.state": "Kerala" } }
)
```

## 19. Find users with hobbies in ["chess","music"] but not "coding"
```js
db.users.find({
  hobbies: { $in: ["chess", "music"], $nin: ["coding"] }
})
```
## 20. Find users younger than 25 or older than 30.
```js
db.users.find({ $or: [{ age: { $lt: 25 } }, { age: { $gt: 30 } }] })
```
## 21. Find users whose pincode is not "670001".
```js
db.users.find({ "address.pincode": { $ne: "670001" } })
```
## 22. Find users who have "chess" as their first hobby.
```js
db.users.find({ "hobbies.0": "chess" }) 
```
## 23. Find users who have "reading" but not "chess".
```js
db.users.find({ hobbies: "reading", hobbies: { $nin: ["chess"] } })  // Charlie, Anu
```
## 24. Find users where the city is in lowercase (e.g., "kannur" vs "Kannur").
```js
db.users.find({ "address.city": { $regex: /^[a-z]+$/ } })
```
## 25. Find users where the pincode is a 6-digit number.
```js
db.users.find({ "address.pincode": { $regex: /^\d{6}$/ } })
```
## 26. Find users whose city name contains "puram" (e.g., "Malappuram").
```js
db.users.find({ "address.city": /puram/i })
```
## 27. Create a text index on name and hobbies for keyword searches.
```js
db.users.createIndex({ name: "text", hobbies: "text" })
```

## 28. Find users with hobbies containing "read" or "chess".
```js
db.users.find({ $text: { $search: "read chess" } })
```



---

## Aggregation

## 1. Count users with "reading" as a hobby

```js
db.users.countDocuments({ hobbies: "reading" })

```
## 2. Group users by city and count them

```js
db.users.aggregate([
  { $group: { _id: "$address.city", count: { $sum: 1 } } }
])
```
## 3. Find the average age of users
```js
db.users.aggregate([
  { $group: { _id: null, avgAge: { $avg: "$age" } } }
])
```
## 4. Find the oldest user in each city.
```js
db.users.aggregate([
  { $group: { _id: "$address.city", maxAge: { $max: "$age" } } }
])
```
## 5. Count the number of users per hobby (unwind hobbies first).
```js
db.users.aggregate([
  { $unwind: "$hobbies" },
  { $group: { _id: "$hobbies", count: { $sum: 1 } } }
])
```
## 6. Find users with duplicate emails (assuming emails should be unique).
```js
db.users.aggregate([
  { $group: { _id: "$email", count: { $sum: 1 } } },
  { $match: { count: { $gt: 1 } } }
])
```

---

# Updation 

## 1. Add "yoga" to the hobbies of all users older than 25.
```js
db.users.updateMany(
  { age: { $gt: 25 } },
  { $push: { hobbies: "yoga" } }
)
```
## 2. Remove "movies" from Bob's hobbies.
```js
db.users.updateOne(
  { name: "Bob" },
  { $pull: { hobbies: "movies" } }
)
```
## 3. Set isActive: false for users with no hobbies.
```js
db.users.updateMany(
  { hobbies: { $exists: true, $size: 0 } },
  { $set: { isActive: false } }
)
```
## 4. Increase the age of all users by 1 year.
```js
db.users.updateMany({}, { $inc: { age: 1 } })
```