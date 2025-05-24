# 📘 JavaScript - call(), apply(), and bind()

## 🔍 What Are call(), apply(), and bind()?

They are JavaScript methods used to set the `this` context of a function manually.

→ Useful when borrowing methods, or calling functions with custom objects.

## 🧠 Basic Idea

functionName.call(context, arg1, arg2, ...);
functionName.apply(context, [arg1, arg2, ...]);
functionName.bind(context, arg1, arg2, ...); // returns a new function

## 📦 Example Object

```js
const person = {
  fullName: function(city, country) {
    return `${this.firstName} ${this.lastName} from ${city}, ${country}`;
  }
};

const user = {
  firstName: "Ebson",
  lastName: "Joy"
};

```
## 📌 1. call()
- Calls the function immediately with a given `this` value.
```js
person.fullName.call(user, "Kochi", "India");
```
// Output: Ebson Joy from Kochi, India
## 📌 2. apply()
- Same as call(), but arguments are passed as an array.
```js
person.fullName.apply(user, ["Kochi", "India"]);

// Output: Ebson John from Kochi, India
```
## 📌 3. bind()
- Returns a new function with a bound context and optional arguments.
- Needs to be invoked separately.
```js
const boundFunc = person.fullName.bind(user, "Kochi", "India");
console.log(boundFunc());

// Output: Ebson John from Kochi, India
```
## 🔄 Summary Table

| Method  | Executes Immediately | Pass Args       | Returns Function |
| ------- | -------------------- | --------------- | ---------------- |
| call()  | ✅ Yes                | Comma separated | ❌ No             |
| apply() | ✅ Yes                | Array           | ❌ No             |
| bind()  | ❌ No                 | Optional        | ✅ Yes            |

## 📌 Real-Life Example

When using event listeners, or borrowing methods from another object.
```js
const car = {
  brand: "Tesla",
  showBrand() {
    console.log(this.brand);
  }
};

const bike = { brand: "Yamaha" };

car.showBrand.call(bike); // Output: Yamaha
