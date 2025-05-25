# 📘 JavaScript - Deep Copy vs Shallow Copy  

## 🔍 What is Copying in JavaScript?
Copying an object or array means creating another version of it — either referencing the original or making an entirely independent duplicate.

## 📦 Shallow Copy
A shallow copy copies only the first level of the object. Nested objects/arrays are still referenced.

```js
const obj1 = { a: 1, b: { c: 2 } };
const obj2 = { ...obj1 };

obj2.b.c = 99;
console.log(obj1.b.c); // 99 ❗ (still linked)

// ✅ Examples of Shallow Copy:

// Arrays
const arr = [1, 2, 3];
const copyArr = [...arr];  // or arr.slice()

// Objects
const obj = { x: 1, y: 2 };
const copyObj = Object.assign({}, obj);  // or {...obj}

```
## 📦 Deep Copy
A deep copy duplicates everything recursively, so nested objects are copied independently.
```js
const obj1 = { a: 1, b: { c: 2 } };
const obj2 = JSON.parse(JSON.stringify(obj1));

obj2.b.c = 99;
console.log(obj1.b.c); // 2 ✅ (fully separated)

```
## ✅ Ways to Do Deep Copy:

| Method                         | Note                                                            |
| ------------------------------ | --------------------------------------------------------------- |
| `JSON.parse(JSON.stringify())` | Easy but doesn't support `functions`, `undefined`, `Date`, etc. |
| **Lodash**: `_.cloneDeep(obj)` | Best, supports all types                                        |
| **Recursive manual method**    | Custom implementation for full control                          |

## 🧠 Real-Life Use

- Copying state in React apps

- Cloning configuration or settings

- Avoiding mutation in Redux/store/state

## ⚖️ Comparison Table:

| Feature            | Shallow Copy    | Deep Copy                           |
| ------------------ | --------------- | ----------------------------------- |
| Copies nested data | ❌ Referenced    | ✅ Fully duplicated                  |
| Performance        | ✅ Fast          | ❌ Slower                            |
| Complexity         | ✅ Simple        | ❌ Complex (custom logic or library) |
| Use case           | Flat structures | Nested structures                   |

## ❌ Disadvantages:

- Shallow Copy: Bugs due to shared references

- Deep Copy: Performance issues with large objects