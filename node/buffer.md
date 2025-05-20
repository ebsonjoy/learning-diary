# 🧠 Node.js - Buffer

**Date:** 2025-05-20

---

## 📦 What is a Buffer?

- A **Buffer** is a temporary storage area for **raw binary data**.
- Used when dealing with binary streams (files, TCP streams, etc.).
- Unlike JavaScript strings (which are UTF-16 encoded), Buffers handle raw bytes directly.

---

## ✅ Why Use Buffer?

- For **reading/writing files**
- For handling **TCP streams** or network data
- For **streaming audio/video**
- For **binary protocol communication**

---

## 🧪 How Buffers Work

- Allocated in memory.
- Not resizable once created.
- Represented as a sequence of **bytes**.

---

## 🧮 Buffer Methods

| Method                  | Description                             |
| ----------------------- | --------------------------------------- |
| `Buffer.alloc(size)`    | Create zero-filled buffer of given size |
| `Buffer.from(data)`     | Create buffer from string/array         |
| `buf.write(string)`     | Write string into buffer                |
| `buf.toString()`        | Convert buffer back to string           |
| `buf.length`            | Length of buffer (in bytes)             |
| `buf.slice(start, end)` | Create a new view into buffer           |
| `buf.equals(otherBuf)`  | Compare two buffers                     |
| `buf.copy(targetBuf)`   | Copy buffer data to another buffer      |


## ✅ Advantages of Buffer
- Efficient for handling raw binary data.
- Works well with streams and file operations.
- Enables communication with low-level systems (e.g., TCP, UDP).

## ⚠️ Limitations / Considerations
- Fixed size — can't dynamically grow.
- Must manage memory manually when working with large data sets.

## 📌 Summary
- Buffer is essential when handling binary data in Node.js.

- Common in file system, network, or stream-based operations.

- Gives fine-grained control over memory and data representation.


## 🧑‍💻 Create a Buffer

```js
const buffer = Buffer.alloc(10);  // Allocate 10 bytes
console.log(buffer);  // <Buffer 00 00 00 00 00 00 00 00 00 00>

const bufferFromStr = Buffer.from('Hello');
console.log(bufferFromStr);  // <Buffer 48 65 6c 6c 6f>

🧑‍💻 Write and Read from Buffer

const buf = Buffer.alloc(4);
buf.write('ABCD');
console.log(buf.toString());  // ABCD


🔄 Convert Buffer to String

const buf = Buffer.from('Node.js');
const str = buf.toString();
console.log(str);  // Node.js


📏 Buffer Length

const buf = Buffer.from('Test');
console.log(buf.length);  // 4


💡Real-Life Example: File Reading

const fs = require('fs');

fs.readFile('example.txt', (err, data) => {
  if (err) throw err;
  console.log('Buffer:', data);         // Raw bytes
  console.log('String:', data.toString());  // Readable content
});




