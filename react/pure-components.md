# Pure Components in React

## What is a Pure Component?

A **Pure Component** in React is a special type of component that **automatically avoids unnecessary re-renders**.

It does this by performing a **shallow comparison** of props and state.

---

## Where is it used?

Used to **optimize performance** when:
- The component re-renders often
- Props and state don't change much
- You want to avoid duplicate renders for the same data

---

## How is it different from a normal component?

| Feature              | Regular Component       | Pure Component         |
|----------------------|--------------------------|-------------------------|
| Re-renders always?   | ✅ Yes (on any update)    | ❌ No (only if needed)  |
| Comparison method    | Manual (if any)          | Shallow check (auto)   |
| Performance          | May be slower            | Usually faster          |

---

## Syntax

### ✅ Functional Component (Using `React.memo`)

```jsx
import React, { useState } from 'react';

const Child = React.memo(({ name }) => {
  console.log('Child rendered');
  return <div>Hello {name}</div>;
});

function Parent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <Child name="Ebson" />
      <button onClick={() => setCount(count + 1)}>Click</button>
    </div>
  );
}


```
## What is “shallow comparison”?
It means:

- It only checks if the top-level values of props/state are different.

- If you pass objects or arrays, make sure their reference changes to trigger a re-render.

Example :-

{ name: "Ebson" } === { name: "Ebson" } // false (different object references)

## When to Use `React.memo`?

- The component renders the same output for the same props.
- You want to optimize performance.
- You understand the risks of shallow comparison.
