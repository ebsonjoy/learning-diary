# Topics
- 1.Self-Invoking Functions
- 2.Object Prototypes
- 3.Constructor Function
- 4.Rest vs Spread
- 5.Generator Function


---

# 1.Self-Invoking Functions

## What is it?
A **self-invoking function** is a function that runs **automatically** when it is defined.

## Where is it used?
Used to **create a local scope** and **avoid polluting the global scope**.

## Syntax:
```js
(function () {
  // code runs automatically
  console.log("Self-invoked");
})();
```
---

# 2.Object Prototypes

## What is it?
A **prototype** is an object from which other objects **inherit properties and methods**.  
In JavaScript, every object has a hidden property called `[[Prototype]]` that refers to another object.

## Where is it used?
Used for **inheritance** — to share methods and properties between objects without duplicating them.

## Example:
```js
function Person(name) {
  this.name = name;
}

// Method added to prototype
Person.prototype.greet = function () {
  console.log("Hi, I'm " + this.name);
};

let user = new Person("Ebson");
user.greet(); // Hi, I'm Ebson
// user inherits the greet method from Person.prototype.
```
---

# 3.Constructor Function

## What is it?
A **constructor function** is a regular function used to **create and initialize objects**.

## Where is it used?
Used when we want to create **multiple similar objects** with the same structure and methods.

## Syntax:
- Starts with a **capital letter** by convention.
- Use the `new` keyword to create an object.

## Example:
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let user1 = new Person("Ebson", 22);
console.log(user1.name); // Ebson
```
---

# 4.Rest vs Spread

## Rest Operator (`...`)

### What is it?
The **rest** operator collects **multiple values into a single array**.

### Where is it used?
Used in **function parameters** to handle **any number of arguments**.

### Example:
```js
function showNames(...names) {
  console.log(names);
}
showNames("Alice", "Bob", "Charlie"); 
// Output: ["Alice", "Bob", "Charlie"]

```
## Spread Operator (`...`)

## What is it?
The spread operator takes an array or object and spreads its values out.

## Where is it used?
Used to copy, combine, or pass values into arrays or objects.

## Example 1: Spread in array
```js
let nums = [1, 2, 3];
let newNums = [...nums, 4, 5];
console.log(newNums); 
// Output: [1, 2, 3, 4, 5]
```
## Example 2: Spread in object
```js
let person = { name: "Ebson" };
let newPerson = { ...person, age: 22 };
console.log(newPerson); 
// Output: { name: "Ebson", age: 22 }

```
## Simple Difference:

| Feature | Rest (`...`)                       | Spread (`...`)                                 |
| ------- | ---------------------------------- | ---------------------------------------------- |
| Use     | To **gather** values into an array | To **expand** values out of an array or object |
| Where   | Function parameters                | Arrays and objects                             |

---

# 5.Generator Function

## What is it?
A **generator function** is a special function that can **pause and resume** its execution using the `yield` keyword.

## Where is it used?
Used when you want to **return values one by one**, like in loops or lazy data processing.

## Syntax:
```js
function* generatorFunc() {
  yield 1;
  yield 2;
  yield 3;
}

function* count() {
  yield 1;
  yield 2;
}

const counter = count();

console.log(counter.next().value); // 1
console.log(counter.next().value); // 2
console.log(counter.next().value); // undefined
```
- function* defines a generator.

- yield returns a value and pauses.

- .next() resumes the function from where it paused.