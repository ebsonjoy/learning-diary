# MongoDB `bulkWrite` Operation

## What is `bulkWrite` in MongoDB?

`bulkWrite` is a powerful method in MongoDB that allows you to perform multiple write operations (like insert, update, delete, replace) in a single command. This improves performance by reducing the number of round trips between your application and the database.

Instead of executing many individual operations one by one, you can group them together and execute them as a batch.

---

## Why use `bulkWrite`?

- **Efficiency**: Executes multiple operations in a single network request.
- **Atomicity** (optional): You can choose to execute the batch with `ordered: true` to stop on the first error or `ordered: false` to continue despite errors.
- **Better performance** for bulk data changes.

---

## Syntax

```js
db.collection.bulkWrite(operations, options)
```
- operations: An array of write operation objects.

- options: Optional settings, e.g., { ordered: true } or { ordered: false }.

## Supported Operations in bulkWrite

- insertOne: Insert a single document.

- updateOne: Update a single document matching the filter.

- updateMany: Update multiple documents matching the filter.

- deleteOne: Delete a single document matching the filter.

- deleteMany: Delete multiple documents matching the filter.

- replaceOne: Replace a single document matching the filter.

## Example Usage

```js

db.users.bulkWrite([
  { insertOne: { document: { name: "Alice", age: 25 } } },
  { updateOne: { filter: { name: "Bob" }, update: { $set: { age: 30 } } } },
  { deleteMany: { filter: { status: "inactive" } } }
], { ordered: true })
.then(result => {
  console.log("Bulk operation result:", result);
})
.catch(err => {
  console.error("Bulk operation error:", err);
});


// Inserts a new user named Alice.

// Updates the age of the user named Bob to 30.

// Deletes all users with status "inactive".

// Because ordered is true, if one operation fails, the rest will not run.

```

## Example: Multiple operations in one bulkWrite
```js

db.users.bulkWrite([
  // Insert a new user
  {
    insertOne: {
      document: {
        name: "Frank",
        age: 33,
        email: "frank@example.com",
        isActive: true,
        address: { city: "Kollam", pincode: 691001 }
      }
    }
  },

  // Update Bob's city to 'Alappuzha'
  {
    updateOne: {
      filter: { name: "Bob" },
      update: { $set: { "address.city": "Alappuzha" } }
    }
  },

  // Delete inactive users younger than 25
  {
    deleteMany: {
      filter: { isActive: false, age: { $lt: 25 } }
    }
  },

  // Upsert (update or insert) Diana's info
  {
    updateOne: {
      filter: { name: "Diana" },
      update: {
        $set: {
          age: 30,
          email: "diana_updated@example.com",
          isActive: true,
          address: { city: "Thrissur", pincode: 680001 }
        }
      },
      upsert: true
    }
  }
])
```