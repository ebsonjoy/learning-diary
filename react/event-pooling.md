## Event Pooling in React

**What:**  
In older React versions (before 17), React reused event objects to save memory.  
This is called **event pooling**.

**Problem:**  
The event object was **cleared** after the event handler finished.  
So if you used it later (like in `setTimeout`), it would not work.

**Example (React < 17):**
```js
function handleClick(e) {
  setTimeout(() => {
    console.log(e.target); // ❌ Won’t work
  }, 1000);
}
