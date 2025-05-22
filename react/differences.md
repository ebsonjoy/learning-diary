# 1. Class Components vs Functional Components in React

React supports two types of components: **Class Components** and **Functional Components**. Below is a detailed comparison of both.

---

## 1. 🔤 **Syntax**

### ✅ Class Component
```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return <h1>Hello from Class</h1>;
  }
}
```
### ✅ Functional Component
```js
import React from 'react';

function MyComponent() {
  return <h1>Hello from Function</h1>;
}
```
## ✅ Conclusion

| Feature                   | Class Component           | Functional Component |
| ------------------------- | ------------------------- | -------------------- |
| Syntax Style              | Verbose                   | Simple               |
| State Handling            | `this.state`              | `useState`           |
| Lifecycle Methods         | Yes (`componentDidMount`) | Yes (`useEffect`)    |
| Hook Support              | ❌ No                      | ✅ Yes                |
| Readability               | Moderate                  | High                 |
| `this` usage              | Required                  | Not used             |
| Preferred in Modern React | ❌ Less Preferred          | ✅ Recommended        |


---

# 2 🟦 State vs Props in React

In React, both **state** and **props** are used to manage and pass data in components, but they serve different purposes.

---

## 1. 📦 **Definition**

### 🧠 State
- A built-in object to store data **within a component**.
- It is **mutable** (can be changed).
- Managed **inside** the component using `useState` (in functional components) or `this.state` (in class components).

### 📬 Props
- Short for **properties**.
- Used to pass data **from parent to child** components.
- They are **read-only** (immutable).

---

## 2. 🛠️ **How to Use**

### ✅ Using State (Functional Component)
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```
### ✅ Using Props
```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage:
<Welcome name="Ebson" />
```
## ✅ Summary Table
| Feature           | State                           | Props                   |
| ----------------- | ------------------------------- | ----------------------- |
| Definition        | Local data of the component     | Data passed from parent |
| Mutability        | Mutable (can be changed)        | Immutable (read-only)   |
| Used for          | Internal data and interactivity | External configuration  |
| Updated by        | Component itself                | Parent component        |
| Causes re-render? | Yes                             | Yes                     |

---

#  3.🔄 useEffect vs useLayoutEffect in React

Both `useEffect` and `useLayoutEffect` are React Hooks used to run side effects in functional components.  
However, they have key differences in **timing and behavior**.

---

## 1. 📜 Basic Definitions

### 🔁 useEffect
- Runs **after** the component renders and paints the UI on the screen.
- Mostly used for **API calls**, **event listeners**, **timers**, etc.

### 🧱 useLayoutEffect
- Runs **synchronously after rendering** but **before the browser paints** the screen.
- Mainly used for **DOM measurements or mutations** that need to block the browser from painting.

---

## 2. 🕒 Timing Difference

| Hook             | When It Runs                                 |
|------------------|-----------------------------------------------|
| `useEffect`      | After the component renders and paints        |
| `useLayoutEffect`| After the render but **before painting**      |

---

## 3. 🛠️ Example Code

### ✅ useEffect Example
```jsx
useEffect(() => {
  console.log('useEffect called');
}, []);

// Output:
Component rendered → Screen painted → useEffect runs

```
## ✅ useLayoutEffect Example
```js
useLayoutEffect(() => {
  console.log('useLayoutEffect called');
}, []);
// Output:
Component rendered → useLayoutEffect runs → Screen painted
```
## ✅ Summary Table

| Feature                   | `useEffect`         | `useLayoutEffect`              |
| ------------------------- | ------------------- | ------------------------------ |
| Run Timing                | After paint         | Before paint                   |
| Blocking UI               | ❌ No                | ✅ Yes                          |
| Performance               | Faster and smoother | Slower if misused              |
| Use for DOM changes       | ❌ Not reliable      | ✅ Yes                          |
| Common Usage              | API calls, logging  | DOM measurements, layout fixes |
| Preferred for general use | ✅ Yes               | ❌ Only when necessary          |

---
