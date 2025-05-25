# CLOSURES IN JAVASCRIPT: MEMORY MANAGEMENT EXPLAINED 🎒

## **1. Definition**
A **closure** is a function that "remembers" its lexical scope (variables from its parent function) even after the parent function has finished executing.

## **2. How Memory Works**
### **Without Closure (Normal Function)**
```js
function noClosure() {
  let temp = "gone!";
  console.log(temp); // "gone!"
}
noClosure(); // After execution, `temp` is GARBAGE-COLLECTED.

// With Closure (Persistent Memory)

function parent() {
  let saved = "I persist!"; // Should be deleted after `parent()` finishes...
  return function child() {
    console.log(saved); // ...but `child` keeps it alive!
  };
}

const remember = parent(); // `parent()` finishes...
remember(); // "I persist!" (Variable still accessible!)
```

## 3. Memory Mechanism

- The JS engine attaches a hidden [[Scope]] property to the inner function.

- This creates a closure scope (a "backpack" of referenced variables).

- Variables in the closure scope survive garbage collection.


## 4. When Memory is Freed
```js
let closureFunc = parent(); // `saved` stays in memory.
closureFunc = null;         // Now `saved` can be garbage-collected.

```

## 5. Key Use Cases

Data Privacy (Module Pattern)
```js
function createCounter() {
  let count = 0; // Hidden by closure!
  return {
    increment: () => ++count,
    get: () => count,
  };
}
const counter = createCounter();
counter.increment();
console.log(counter.get()); // 1 (but `count` is private!)

// Event Handlers (Stateful Callbacks)

function initButton() {
  let clicks = 0;
  document.querySelector("button").addEventListener("click", () => {
    console.log(`Clicked ${++clicks} times`);
  });
}
// `clicks` persists between clicks!

```

## 6. Cheat Sheet

| Behavior               | No Closure            | With Closure               |
|------------------------|------------------------|-----------------------------|
| Outer function finishes| Variables deleted 🗑️   | Variables kept 🎒           |
| Memory freed when...  | Function ends          | Inner function is GC'd      |


