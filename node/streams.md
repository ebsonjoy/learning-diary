# 🌊 Node.js - Streams

**Date:** 2025-05-20

---

## 🔍 What Are Streams?

Streams are objects in Node.js that let you **read or write data** continuously and efficiently.

- Useful when dealing with large amounts of data (like video files, logs, or network data).
- Streams work in **chunks**, not all at once — saving memory and improving speed.

---

## ✅ Types of Streams

| Stream Type        | Description                               | Example Use Case                        |
|--------------------|-------------------------------------------|------------------------------------------|
| **Readable**       | Read data from source                     | Reading from a file, API, socket         |
| **Writable**       | Write data to a destination               | Writing to a file, sending HTTP response |
| **Duplex**         | Both readable and writable                | TCP sockets                              |
| **Transform**      | Modify data during reading or writing     | Compressing, encryption, parsing         |

---

## 📦 Real-Life Examples

| Stream Type   | Real-Life Example                                |
|---------------|--------------------------------------------------|
| Readable      | Reading a large video file to stream to browser  |
| Writable      | Writing logs into a file continuously            |
| Duplex        | Chat app (sending & receiving messages)          |
| Transform     | GZIP compression while uploading a file          |

---

## 📈 Why Use Streams?

✅ Handle large files efficiently
✅ Reduce memory usage
✅ Speed up data processing
✅ Great for network communication & file handling


## ⚙️ Events Used in Streams

| Event    | Description                          |
| -------- | ------------------------------------ |
| `data`   | Triggered when a chunk is available  |
| `end`    | No more data to read                 |
| `error`  | Error during stream operation        |
| `finish` | Writable stream has finished writing |

## 🧠 Summary
Streams are perfect when:

You're working with files, HTTP, or sockets.

You want to process data bit by bit instead of whole.

You want non-blocking, memory-efficient Node.js apps.

---

## 🧑‍💻 1. Readable Stream Example

```js
const fs = require('fs');

const readableStream = fs.createReadStream('bigfile.txt', 'utf8');

readableStream.on('data', (chunk) => {
  console.log('Received chunk:', chunk);
});

readableStream.on('end', () => {
  console.log('Finished reading file.');
});


 🧑‍💻 2. Writable Stream Example

 const fs = require('fs');

const writableStream = fs.createWriteStream('output.txt');

writableStream.write('Hello, this is written in chunks!\n');
writableStream.end();

🧑‍💻 3. Duplex Stream Example

const { Duplex } = require('stream');

const duplexStream = new Duplex({
  read(size) {
    this.push('Reading from duplex\n');
    this.push(null);
  },
  write(chunk, encoding, callback) {
    console.log('Writing:', chunk.toString());
    callback();
  }
});

duplexStream.on('data', (chunk) => {
  console.log('From Read:', chunk.toString());
});

duplexStream.write('Write this to duplex\n');
duplexStream.read();


🧑‍💻 4. Transform Stream Example (Uppercase)

const { Transform } = require('stream');

const upperCaseTransform = new Transform({
  transform(chunk, encoding, callback) {
    const upper = chunk.toString().toUpperCase();
    callback(null, upper);
  }
});

process.stdin.pipe(upperCaseTransform).pipe(process.stdout);

