# Topics
- 1.Cleanup Function
- 2.Prevent Prop Drilling
- 3.Higher Order Component (HOC)
- 4.Conditional Rendering
- 5.Render Props
- 6.Synthetic Events
- 7.Rules of Hooks
- 8.React.StrictMode

---
# 1.Cleanup Function in React

## What is it?
A cleanup function is returned inside `useEffect` to clean up side effects when the component unmounts or before the effect re-runs.

## Where is it used?
- Inside `useEffect`
- To stop timers
- To remove event listeners
- To cancel async tasks

## Syntax
```js
useEffect(() => {
  // effect code

  return () => {
    // cleanup code
  };
}, []);
```

## Example
```js
import { useEffect } from 'react';

function Timer() {
  useEffect(() => {
    const id = setInterval(() => {
      console.log('Tick');
    }, 1000);

    return () => {
      clearInterval(id);
      console.log('Cleanup');
    };
  }, []);

  return <div>Timer running...</div>;
}
```
---

# 2.Prevent Prop Drilling in React

## What is it?
Prop drilling happens when you pass data through many nested components, even if only the deepest one needs it.

## Problem
Too many props passed down → hard to manage, cluttered code.

## How to Prevent It?

### 1. Context API
Use it to share data without passing props manually.

```js
// context.js
import { createContext, useContext } from 'react';
export const UserContext = createContext();

// App.js
<UserContext.Provider value={{ name: 'Ebson' }}>
  <Parent />
</UserContext.Provider>

// Any child
const { name } = useContext(UserContext);
```

### 2. Redux / State Management
Use Redux, Zustand, or other global state libraries to manage and access state.

### 3. Component Composition
Pass components as children or props instead of data.

```js
function Wrapper({ children }) {
  return <div>{children}</div>;
}

<Wrapper>
  <ComponentNeedingData />
</Wrapper>
```
---

# 3.Higher Order Component (HOC) in React

## What is it?  
A Higher Order Component is a function that takes a component and returns a new enhanced component.

## Why use it?  
To reuse logic and add extra functionality to components without repeating code.

## Syntax  
```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

## Example  
```js
function withLogger(WrappedComponent) {
  return function(props) {
    console.log('Rendering:', WrappedComponent.name);
    return <WrappedComponent {...props} />;
  }
}

// Usage
const Button = (props) => <button {...props}>Click me</button>;
const ButtonWithLogger = withLogger(Button);
```

In this example, `withLogger` adds a console log whenever the component renders.

---

# 4.Conditional Rendering in React

## What is it?  
Showing or hiding UI elements based on conditions.

## How to use it?

### 1. Using `if` statement  
```js
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign in.</h1>;
}
```

### 2. Using Ternary Operator  
```js
<div>{isLoggedIn ? <UserProfile /> : <LoginButton />}</div>
```

### 3. Using Logical AND (`&&`)  
```js
{isLoggedIn && <LogoutButton />}
```

## Why use?  
To display different UI based on app state or props.

---

# 5.Render Props in React

## What is it?  
A **render prop** is a function prop that a component uses to know what to render. It lets you share code between components by passing a function that returns React elements.

## Why use it?  
To reuse logic in different ways without repeating code or using inheritance.

## Simple Example  
```js
function MouseTracker({ render }) {
  const [position, setPosition] = React.useState({ x: 0, y: 0 });

  function handleMouseMove(e) {
    setPosition({ x: e.clientX, y: e.clientY });
  }

  return (
    <div onMouseMove={handleMouseMove} style={{ height: '100px', border: '1px solid black' }}>
      {render(position)}
    </div>
  );
}

// Usage:
<MouseTracker render={({ x, y }) => (
  <p>Mouse position: {x}, {y}</p>
)} />
```

- `MouseTracker` tracks mouse position.
- It calls `render` function with current position to decide what to show.
---

# 6.Synthetic Events in React

## What is it?  
Synthetic events are React’s cross-browser wrapper around the native browser events. They provide a consistent interface for events in React apps.

## Why use it?  
To handle events the same way in all browsers.

## Example  
```js
function ClickButton() {
  function handleClick(event) {
    console.log('Button clicked', event.type);
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

- React’s event object is called a SyntheticEvent.
- It works like the native event but is consistent across browsers.
- Synthetic events are pooled for performance (reused internally).

---

# 7.Rules of Hooks

## What are Hooks?
Hooks are functions that let you **use state and other React features** in functional components.

## Rules of Hooks

### 1. **Only call Hooks at the top level**
- Do **not** call Hooks inside loops, conditions, or nested functions.
- Always call them at the **top level** of your component.

✅ Correct:
```js
function MyComponent() {
  const [count, setCount] = useState(0);
}
```

---

# 8.React.StrictMode

## What is it?
`React.StrictMode` is a **tool provided by React to help developers write better code**.  
It **does not show any UI** — it's only used in **development mode** (not in production).

## What does it do?
It helps you find and fix:
- **Unsafe or outdated lifecycle methods**
- **Side effects** that happen during rendering
- **Incorrect usage of hooks**
- **Deprecated APIs**

It makes React **stricter in development** to catch bugs early.

## How does it work?
- It **intentionally runs components twice** (only in development) to check for side effects.
- It shows **warnings** in the browser console if it finds any issues.

## Where is it used?
You wrap your app or part of it in `<React.StrictMode>` in the root file:

### Example:
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

