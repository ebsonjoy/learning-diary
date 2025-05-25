# useRef Hook in React

## 📌 What is `useRef`?

`useRef` is a **React Hook** that allows you to create a **mutable reference object**. This object can persist across renders without causing a re-render when it’s updated.

```tsx
const myRef = useRef(initialValue);
// It returns a plain JavaScript object with a .current property.
// Example
const myRef = useRef(null);
// You can then attach it to a DOM element:
<input ref={myRef} />
// Access the element directly via:
myRef.current
```
## 🧠 When to Use useRef?
- To access and interact with DOM elements (like focusing an input, scrolling a div, etc.)

- To store mutable values that don’t cause re-renders when updated

- To store values like previous state/props

## 📍 Where is useRef Used?
- Accessing DOM Elements

- Storing Mutable Values

- Persisting Values Across Renders Without Triggering a Re-render

## ✅ Example 1: Accessing a DOM Element

```js
import { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current?.focus();
  };

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus Input</button>
    </>
  );
}
```
## ✅ Example 2: Storing a Mutable Value Without Re-rendering
```js
import { useRef, useState } from 'react';

function Timer() {
  const countRef = useRef(0);
  const [_, forceRender] = useState(false);

  const handleClick = () => {
    countRef.current += 1;
    console.log('Count:', countRef.current);
  };

  return (
    <>
      <p>Check console to see count (won’t re-render)</p>
      <button onClick={handleClick}>Increment Ref</button>
    </>
  );
}
```
## ✅ Example 3: Storing Previous Props or State
```js
import { useEffect, useRef, useState } from 'react';

function PreviousValue() {
  const [count, setCount] = useState(0);
  const prevCountRef = useRef<number>();

  useEffect(() => {
    prevCountRef.current = count;
  }, [count]);

  return (
    <>
      <p>Current: {count}</p>
      <p>Previous: {prevCountRef.current}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```
## 📝 Notes
- Updating .current does not cause a re-render

- Perfect for storing non-UI values like timers, IDs, DOM references

- It’s similar to using instance variables in class components

## 🚫 Avoid This
- Don't use useRef to replace state if your UI depends on the value — use useState instead for reactive updates.
