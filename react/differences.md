# Topics
- 1.Class Components vs Functional Components
- 2.State vs Props
- 3.useEffect vs useLayoutEffect
- 4.SSR vs CSR (Server-Side Rendering vs Client-Side Rendering)
- 5.Props vs State
- 6.localStorage vs sessionStorage (Browser)

# 1.Class Components vs Functional Components

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

# 🟦 2.State vs Props in React

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

#  🔄 3.useEffect vs useLayoutEffect

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

NB : Scree Painting Means You tell React something changed → React updates it → You see it → That's painting the screen.
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
# 🌐 4.SSR vs CSR (Server-Side Rendering vs Client-Side Rendering)

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

# ⚛️ 5.Props vs State

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
# 🗃️ 6.localStorage vs sessionStorage (Browser)

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
---

