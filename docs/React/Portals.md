# Modal window in a React app



The key to getting a modal window to work in React is to use Portals. 

Portals allow a component to render a sub component but to have it act as a child of some other component, usually the 'root' div.

In this example StreamDelete is opening a modal window under 'root'.

![React component hierarchy chart](/home/mikedegan/dev/docs/docs/images/Screenshot 2019-10-22 at 7.11.11 PM.png)

Portals are described in detail in the Udemy course *Modern React with Redux* section 21.

When you attach the modal to a div the modal will replace the content of that div or whatever with the content of your modal. So you will almost always create a sibling to the 'root' element to attach the modal to. 

```html
 <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    <div id="modal"></div>
  </body>
```

  The modal component will not return normal jsx it will return the ReactDOM.createPortal function. 

```javascript
import React from "react";
import ReactDOM from "react-dom";

const Modal = props => {
  return ReactDOM.createPortal(
    <div className="ui dimmer modals visible active">
      <div className="ui standard modal visible active">
        lorem20 crap lkjsflj ljsdf ljf lkjs flksjdf
      </div>
    </div>,
    document.querySelector("#modal")
  );
};

export default Modal;
```

To call the modal you just call it like any component

```javascript
import React from "react";
import Modal from "../Modal";

const StreamDelete = () => {
  return (
    <div>
      StreamDelete
      <Modal />
    </div>
  );
};

export default StreamDelete;
```

NOTE:

You would normally use Portals to render modal windows but would also use portals if trying to render some React component into some html that was not created by your application like server side rendered html like Java or Ruby or something like that.

