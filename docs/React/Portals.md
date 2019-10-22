# Modal window in a React app



The key to getting a modal window to work in React is to use Portals. 

Portals allow a component to render a sub component but to have it act as a child of some other component, usually the 'root' div.

In this example StreamDelete is opening a modal window under 'root'.

![React component hierarchy chart](/home/mikedegan/dev/docs/docs/images/Screenshot 2019-10-22 at 7.11.11 PM.png)

Portals are described in detail in the Udemy course *Modern React with Redux* section 21.



