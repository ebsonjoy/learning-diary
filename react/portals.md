# React Portals

## What is React Portal?

React Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

Normally, a child component is rendered within its parent component's DOM tree. But with portals, you can render it into a different part of the DOM, often used for components like modals, tooltips, and dropdowns.

## Where is it used?

- Modals (popup dialogs)
- Tooltips
- Dropdown menus
- Overlays

These UI elements often need to visually "break out" of their parent container (e.g., avoid being clipped or hidden by overflow rules), and portals help achieve that.

## Syntax

```js
ReactDOM.createPortal(child, container)

child: The React element you want to render.

container: The DOM node where the child should be rendered.

```
## Simple Example

```js
//index.html
<body>
  <div id="root"></div>
  <div id="portal-root"></div>
</body>

//Modal.js 

import React from 'react';
import ReactDOM from 'react-dom';

const Modal = ({ children }) => {
  return ReactDOM.createPortal(
    <div className="modal">{children}</div>,
    document.getElementById('portal-root')
  );
};

export default Modal;

//App.js
import React from 'react';
import Modal from './Modal';

function App() {
  return (
    <div>
      <h1>Hello React</h1>
      <Modal>
        <p>This is inside a portal!</p>
      </Modal>
    </div>
  );
}

export default App;
