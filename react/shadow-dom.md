# Shadow DOM in React

## What is Shadow DOM?

The **Shadow DOM** is a browser technology that allows developers to **encapsulate HTML, CSS, and JavaScript** so that it doesn't affect the rest of the page.

Think of it like a **separate mini DOM** inside an element. Whatever happens inside the shadow DOM **stays isolated** — styles and scripts inside it don’t leak out, and outer styles don’t leak in.

---

## Why is it useful?

- Prevents **style conflicts** (CSS from one component doesn't affect others).
- Helps create **truly reusable** and self-contained components.
- Commonly used in **Web Components** (like `<video>`, `<input type="range">`, etc.).

---

## Is Shadow DOM used in React?

### No, not by default.

React does **not use Shadow DOM** out of the box. Instead, it uses a **virtual DOM**, which is different.

However, if you want to use Shadow DOM in React:

- You can manually attach a shadow root using `ref` and `attachShadow()`.

---

## Example: Shadow DOM in React

```jsx
import React, { useRef, useEffect } from 'react';

function ShadowComponent() {
  const hostRef = useRef(null);

  useEffect(() => {
    const shadowRoot = hostRef.current.attachShadow({ mode: 'open' });
    shadowRoot.innerHTML = `
      <style>
        p { color: red; }
      </style>
      <p>This is inside Shadow DOM</p>
    `;
  }, []);

  return <div ref={hostRef}></div>;
}

export default ShadowComponent;
