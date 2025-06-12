# What Is the "Hook Concept" in React?
- The hook concept in React is the idea of using special functions (called hooks) to let functional components do things that only class components could do before — like:

- Manage state

- Handle side effects (e.g., data fetching)

- Use context

- Control DOM elements

- Access lifecycle-like behavior

## 🔵 1. Basic Hooks
These are the most commonly used hooks in day-to-day development.

| Hook         | Purpose                                                      |
| ------------ | ------------------------------------------------------------ |
| `useState`   | Adds **state** to functional components                      |
| `useEffect`  | Handles **side effects** (like API calls, DOM updates, etc.) |
| `useContext` | Accesses values from a **React Context**                     |


## 🟣 2. Additional Hooks
These are used for more advanced features and optimizations.

| Hook                  | Purpose                                                                                   |
| --------------------- | ----------------------------------------------------------------------------------------- |
| `useReducer`          | Alternative to `useState` for **complex state logic** (like Redux-style reducers)         |
| `useCallback`         | Returns a **memoized callback function** to avoid unnecessary re-renders                  |
| `useMemo`             | Returns a **memoized value** (used to optimize performance)                               |
| `useRef`              | Access **DOM elements** or store a **mutable value** that doesn’t re-render the component |
| `useImperativeHandle` | Customizes what is exposed to parent when using `ref` with `forwardRef`                   |
| `useLayoutEffect`     | Like `useEffect`, but fires **synchronously** after all DOM mutations (used rarely)       |
| `useDebugValue`       | Used to **display custom hook info** in React DevTools                                    |


## 🟢 3. Hooks for Concurrent Features (Advanced and rare)
These are related to experimental features in React like concurrent rendering.

| Hook                   | Purpose                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------- |
| `useDeferredValue`     | Delays a value update to avoid blocking the UI                                        |
| `useTransition`        | Used to mark **state updates as non-urgent** (for smoother transitions)               |
| `useId`                | Generates a unique ID for accessibility (useful in forms and SSR)                     |
| `useSyncExternalStore` | Used for subscribing to **external stores** (like Zustand, Redux)                     |
| `useInsertionEffect`   | Fires **before DOM mutations**, useful for styling libraries (like styled-components) |


## 🛠 Example Summary

| Category       | Hook Names                                                                                                  |
| -------------- | ----------------------------------------------------------------------------------------------------------- |
| 🔹 Basic Hooks | `useState`, `useEffect`, `useContext`                                                                       |
| 🔸 Additional  | `useReducer`, `useRef`, `useMemo`, `useCallback`, `useLayoutEffect`, `useDebugValue`, `useImperativeHandle` |
| 🔺 Concurrent  | `useTransition`, `useDeferredValue`, `useId`, `useSyncExternalStore`, `useInsertionEffect`                  |
