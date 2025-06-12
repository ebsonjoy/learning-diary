# Topics
- 1. Class Components vs Functional Components
- 2. useEffect vs useLayoutEffect
- 3. SSR vs CSR (Server-Side Rendering vs Client-Side Rendering)
- 4. Props vs State
- 5. localStorage vs sessionStorage (Browser)
- 6. Controlled vs Uncontrolled Components 

# 1.Class Components vs Functional Components

React supports two types of components: **Class Components** and **Functional Components**. Below is a detailed comparison of both.

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


#  🔄 2.useEffect vs useLayoutEffect

Both `useEffect` and `useLayoutEffect` are React Hooks used to run side effects in functional components.  
However, they have key differences in **timing and behavior**.


## 1. 📜 Basic Definitions

### 🔁 useEffect
- Runs **after** the component renders and paints the UI on the screen.
- Mostly used for **API calls**, **event listeners**, **timers**, etc.

### 🧱 useLayoutEffect
- Runs **synchronously after rendering** but **before the browser paints** the screen.
- Mainly used for **DOM measurements or mutations** that need to block the browser from painting.

NB : Scree Painting Means You tell React something changed → React updates it → You see it → That's painting the screen.


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
# 🌐 3.SSR vs CSR (Server-Side Rendering vs Client-Side Rendering)

Both SSR and CSR are methods to render web pages, but they differ in **where** and **when** the HTML is generated.



## 1. 🧠 What They Are

### 🔁 Server-Side Rendering (SSR)
- The HTML is **generated on the server** and sent to the browser.
- The page is **ready to show** when it reaches the client.

### 🎨 Client-Side Rendering (CSR)
- The server sends a **basic HTML file with JavaScript**.
- The browser **downloads, parses, and executes JS** to render the page.


## 2. 🛠️ How They Work

### ✅ SSR Flow
1. User requests a page.
2. Server generates HTML dynamically.
3. HTML is sent to browser.
4. Browser displays the page immediately.

### ✅ CSR Flow
1. User requests a page.
2. Server sends basic HTML + JS files.
3. Browser loads JS.
4. JS renders the HTML on the client side.



## 3. ⏱️ Performance

| Feature         | SSR                            | CSR                           |
|------------------|----------------------------------|-------------------------------|
| Initial Load     | Faster to show content          | Slower, blank screen at first |
| After Load       | Can be slower to interact       | Faster, once loaded           |
| SEO Friendly     | ✅ Yes                          | ❌ No (needs extra setup)     |



## 4. 💡 Use Cases

| Use Case                     | SSR                         | CSR                        |
|------------------------------|------------------------------|----------------------------|
| SEO-optimized pages (blogs, news) | ✅ Good choice             | ❌ Not preferred            |
| Dashboards, SPAs             | ❌ Overkill                  | ✅ Better fit               |
| Static or dynamic content    | Good for both                | Good for dynamic only       |



## 5. 🔍 SEO & Crawling

- **SSR**: Search engines see full HTML content → ✅ SEO-friendly
- **CSR**: Search engines may only see empty HTML → ❌ Bad SEO (unless pre-rendered)



## ✅ Summary Table

| Feature             | SSR (Server-Side Rendering)      | CSR (Client-Side Rendering)      |
|----------------------|----------------------------------|----------------------------------|
| Rendering Location   | Server                          | Browser (Client)                 |
| Initial Load Time    | Fast (HTML already built)       | Slower (needs JS to load UI)     |
| SEO Friendly         | ✅ Yes                           | ❌ No (needs extra config)        |
| Developer Control    | Server handles view             | Browser builds view              |
| Best For             | Content-heavy, SEO pages        | Interactive apps, SPAs           |



📌 **Conclusion:**  
- Use **SSR** when SEO and fast first load matter. (e.g., Next.js with `getServerSideProps`)
- Use **CSR** for dynamic, interactive apps like dashboards or social media.
---

# ⚛️ 4.Props vs State

In React, both `props` and `state` are used to control data in components — but they serve different purposes.

---

## 1. 📜 Definition

### 📨 Props (Properties)
- Props are **read-only** data passed **from parent to child** components.
- Like function parameters.
- Cannot be changed by the receiving component.

### 🧠 State
- State is **data that belongs to a component**.
- It is **mutable** and can be updated inside the component.
- Controls the component’s behavior and how it renders.

---

## 2. 🛠️ How to Use

### ✅ Props Example
```jsx
function Greet(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Greet name="Ebson" />
```
### ✅ State Example
```js
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```
## 3. 📋 Comparison Table
| Feature           | Props                      | State                        |
| ----------------- | -------------------------- | ---------------------------- |
| Definition        | Data passed from parent    | Internal data of a component |
| Mutability        | ❌ Immutable (read-only)    | ✅ Mutable (can change)       |
| Ownership         | Parent component           | The component itself         |
| Usage             | Customize child components | Handle local dynamic data    |
| Can be changed by | Parent only                | The component itself         |
| Example Use Case  | Send user info to child    | Toggle a modal, count clicks |

## 4. 🔁 Can it change over time?
- Props: ❌ No — they are fixed once passed.

- State: ✅ Yes — it can be updated using setState() or useState().

## 5. 💬 Analogy
| Concept | Analogy                                   |
| ------- | ----------------------------------------- |
| Props   | Like function arguments                   |
| State   | Like variables declared inside a function |

## ✅ Summary
Props = Passed to the component (external, fixed).

State = Managed inside the component (internal, changeable).

🧠 Use props to pass data to a child.
🔁 Use state when you want your component to be interactive or dynamic.

---
# 🗃️ 5.localStorage vs sessionStorage (Browser)

| Feature              | `localStorage`                                                | `sessionStorage`                                    |
| -------------------- | ------------------------------------------------------------- | --------------------------------------------------- |
| 🕒 **Lifespan**      | Data is stored **permanently** (until manually cleared)       | Data is stored **only for the current tab session** |
| ❌ **Auto-Clears**    | ❌ No – stays after page reload, tab close, or browser restart | ✅ Yes – clears when the **tab or window is closed** |
| 📁 **Storage Scope** | Shared across **all tabs/windows** of the same origin         | Only available to the **same tab**                  |
| 📦 **Size Limit**    | Around **5–10 MB**                                            | Around **5 MB**                                     |
| 📚 **Use Case**      | Save long-term data (e.g. theme, token, user settings)        | Save temporary data (e.g. OTP, form draft)          |


## 🧠 Example
```js
// ✅ localStorage
localStorage.setItem("username", "Ebson");
console.log(localStorage.getItem("username")); // Ebson
//This stays even after you refresh or close and reopen the browser.

// ✅ sessionStorage
sessionStorage.setItem("otp", "123456");
console.log(sessionStorage.getItem("otp")); // 123456
//This disappears when you close the tab.
```
---
# 6. Controlled vs Uncontrolled Components

## 📘 What is a Controlled Component?

A **controlled component** is a React component whose form data is **handled by the React component's state**. In these components, the value of an input field (like `<input>`, `<textarea>`, or `<select>`) is controlled by React via the `useState` hook (or `this.state` in class components).

### 🔧 How It Works
- The value of the input is set using a state variable.
- Any changes to the input are handled using `onChange`, which updates the state.
- The input always reflects the current state.

### ✅ Example:
```jsx
import { useState } from 'react';

function ControlledInput() {
  const [name, setName] = useState('');

  const handleChange = (e) => {
    setName(e.target.value);
  };

  return (
    <input type="text" value={name} onChange={handleChange} />
  );
}
```
## 📘 What is an Uncontrolled Component?
An uncontrolled component is a form element where data is handled by the DOM itself, not by React. You can still access the value using a ref (useRef) when needed, but React doesn't control the input’s current value during typing.

### 🔧 How It Works
- The input maintains its own state internally (like normal HTML).

- React can read the value when needed using a ref, but it doesn’t control the value.

### ✅ Example:
```js
import { useRef } from 'react';

function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    alert('Input value: ' + inputRef.current.value);
  };

  return (
    <>
      <input type="text" ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```
## 🔍 Differences Between Controlled and Uncontrolled Components

| Feature                  | Controlled Component             | Uncontrolled Component                     |
| ------------------------ | -------------------------------- | ------------------------------------------ |
| Value managed by         | React state                      | DOM (default HTML behavior)                |
| Real-time validation     | Easy to implement                | Harder to do                               |
| Refs used?               | Not usually                      | Yes (useRef)                               |
| Easier to test?          | ✅ Yes                            | ❌ No                                       |
| Need for initial default | Use `useState`                   | Use `defaultValue` or `defaultChecked`     |
| Example Usage            | Login forms, filters, validation | Quick data access, third-party integration |

## 🧠 When to Use What?

| Scenario                                   | Recommended Component |
| ------------------------------------------ | --------------------- |
| You need instant validation                | Controlled            |
| You want to manipulate input conditionally | Controlled            |
| Working with 3rd-party DOM libraries       | Uncontrolled          |
| Need fast simple form without validation   | Uncontrolled          |
| Managing dynamic form inputs               | Controlled            |


## ⚙️ Summary
- Controlled Components give you full control using React state, perfect for validations, dynamic input rendering, and real-time data updates.

- Uncontrolled Components are quicker to set up and rely on traditional HTML form behavior with refs for occasional value access.

- Controlled is preferred in most React apps for consistency and better state management.

---
# 7.Stateless vs Stateful Components


## 📘 What is a Stateless Component?

A **stateless component** is a React component that does **not manage or hold any state**. It simply receives data via props and renders UI. These are sometimes called **presentational components**.

### 🔧 Characteristics:
- No use of `useState`, `useReducer`, or `this.state`.
- Pure functions: same output for same input (props).
- Mainly used for UI presentation.
- Easier to test and reuse.

### ✅ Example:
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
## 📘 What is a Stateful Component?

- A stateful component is a component that manages its own state. It can change its state over time, usually in response to user interaction or API calls.

### 🔧 Characteristics:
- Uses useState, useReducer, or this.state.

- Controls behavior/data inside the component.

- Often manages logic, user input, and rendering.
### ✅ Example:
```js

import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```
### 🔍 Differences Between Stateless and Stateful Components

| Feature           | Stateless Component           | Stateful Component     |
| ----------------- | ----------------------------- | ---------------------- |
| Manages state?    | ❌ No                          | ✅ Yes                  |
| Use of `useState` | Not used                      | Used                   |
| Complexity        | Simple                        | Can be complex         |
| Focus             | UI/Presentation only          | Data, logic, and UI    |
| Testability       | Easier                        | Slightly harder        |
| Example           | `Welcome`, `Button`, `Header` | `Counter`, `LoginForm` |

### 🧠 When to Use What?

| Scenario                                      | Recommended Component |
| --------------------------------------------- | --------------------- |
| Pure UI rendering, with no interaction        | Stateless             |
| Needs interaction or internal data management | Stateful              |
| Reusable, easy-to-test UI blocks              | Stateless             |
| Components like modals, toggles, forms        | Stateful              |

### 🔄 Can They Be Combined?

Yes! In large apps, stateless components are often nested inside stateful components. This improves separation of concerns.

### ✅ Example:

```js
function Display({ count }) {
  return <p>Current count: {count}</p>;
}

function Parent() {
  const [count, setCount] = useState(0);

  return (
    <>
      <Display count={count} />
      <button onClick={() => setCount(count + 1)}>+1</button>
    </>
  );
}

```
### ⚙️ Summary
- Stateless Components are simple, reusable, and focus on what to show.

- Stateful Components manage state and define how things behave.

- A good practice is to keep most components stateless and use state only where absolutely needed.

- "Use stateless components for structure and styling; use stateful components for behavior."