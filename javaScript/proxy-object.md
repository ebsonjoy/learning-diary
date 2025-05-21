# 📦 Proxy Object in JavaScript

## 🔍 What is a Proxy?

- A Proxy in JavaScript is an object that wraps another object (called target) and intercepts operations performed on it.
- You can define custom behavior for fundamental operations like reading/writing properties, function calls, etc.

## 📖 Definition

A **Proxy** in JavaScript is an object that wraps another object and **intercepts operations** like getting, setting, or deleting properties.  
It acts like a **middleman** between your code and the real object.

## 🧠 Purpose

A Proxy lets you:
- Change how an object behaves when accessed.
- Add custom logic when reading or writing properties.
- Protect or validate object data.

# 📘 Syntax:
```js
const proxy = new Proxy(target, handler);
```
## 🛠️ Parameters

• target  → The original object to wrap.
• handler → An object that defines traps (custom behaviors).

## 📌 Example: Basic Proxy

```js
const user = {
  name: "Alice",
};

const proxy = new Proxy(user, {
  get(target, prop) {
    return prop in target ? target[prop] : "Property not found";
  }
});

console.log(proxy.name);   // Alice
console.log(proxy.age);    // Property not found
```
## 🚦 Common Proxy Traps (Handler Methods)

| Trap          | Description                                    |
|---------------|------------------------------------------------|
| get           | Intercepts property read (proxy.prop)          |
| set           | Intercepts property write (proxy.prop = val)   |
| has           | Intercepts `in` operator                       |
| deleteProperty| Intercepts `delete` operator                   |
| ownKeys       | Intercepts `Object.keys()`, `for...in`         |
| apply         | Intercepts function calls                      |
| construct     | Intercepts `new` operator                      |
| defineProperty| Intercepts Object.defineProperty               |
| getOwnPropertyDescriptor | Intercepts Object.getOwnPropertyDescriptor |


 ## 📦 Example: set Trap
```js
const product = {
  name: "Laptop"
};

const proxyProduct = new Proxy(product, {
  set(target, prop, value) {
    if (prop === "price" && typeof value !== "number") {
      throw new TypeError("Price must be a number");
    }
    target[prop] = value;
    return true;
  }
});

proxyProduct.price = 1000;        // ✅ Works
proxyProduct.name = "MacBook";    // ✅ Works
proxyProduct.price = "cheap";     // ❌ Throws error
```
## 🧠 Real-Life Use Cases

1. **Validation** → Ensure only valid data is set on an object.
2. **Logging** → Track access to object properties.
3. **Access control** → Hide or protect certain properties.
4. **Mocking** → Create dummy APIs in testing environments.
5. **Reactive frameworks** → Used in Vue.js 3 (reactivity system).

## 📊 Advantages

+ Very flexible and powerful.
+ Great for debugging, validation, access control.
+ Enables creation of reactive data (used in Vue 3, MobX).

## ⚠️ Disadvantages

- Slower than direct property access (due to interception).
- Can make code harder to understand/debug if overused.
## 📌 Summary

- A Proxy object lets you customize the behavior of operations on another object.
- You use it by providing a target and a handler with traps.
- It is widely used in frameworks, testing, and security-focused code.

