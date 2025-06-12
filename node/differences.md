1. Query Params vs Path Params


## Query Params vs Path Params

**What:**  
Both are used to send data in the URL, but for different purposes.

---

### 🔹 Path Params (for specific data)
- Data is **part of the URL path**.
- Commonly used for getting a specific item by ID.

**Example:**
```js
// Route
app.get('/user/:id', (req, res) => {
  res.send(req.params.id);
});

// URL
http://localhost:3000/user/123
// Output: 123
//✅ Use req.params to access path params.
```
## 🔹 Query Params (for filtering/search)
- Data is sent after ? in the URL.

- Used for search, filters, or optional inputs.

### Example:
```js
// Route
app.get('/search', (req, res) => {
  res.send(req.query.name);
});

// URL
http://localhost:3000/search?name=ebson&age=25
// Output: ebson
// ✅ Use req.query to access query params.

```
## 🔁 Summary Table

| Feature        | Path Params       | Query Params        |
| -------------- | ----------------- | ------------------- |
| Format         | `/user/:id`       | `/search?key=value` |
| Use case       | Identify resource | Filter/search data  |
| Accessed using | `req.params`      | `req.query`         |
| Can have many? | Usually 1–2       | Yes, with `&`       |
