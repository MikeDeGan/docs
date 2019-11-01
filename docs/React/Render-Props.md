---
title: Render Props
---

# Render Props

The term “render prop” refers to a technique for sharing code between React components using a prop whose value is a function. It helps to share state or behavior that one component contains into another component. 

In most cases this technique can be handled cleaner with the new React Hooks.

> *Hooks can replace some render props, but not all of them.*
>
> *Hooks can’t render anything, they can’t set values on context (even though they can consume values), and they can’t implement error boundaries. Given these limitations, you may still find yourself using render props from time to time.*

## React Docs Example

In this example taken from the [reactjs.org docs](https://reactjs.org/docs/render-props.html) render props page you can see how they have made the Mouse component reusable by passing in a component to dynamically determine what to render. 

```javascript
class Cat extends React.Component {
  render() {
    const mouse = this.props.mouse;
    return (
      <img src="/cat.jpg" style={{ position: 'absolute', left: mouse.x, top: mouse.y }} />
    );
  }
}

class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  }

  render() {
    return (
      <div style={{ height: '100%' }} onMouseMove={this.handleMouseMove}>

        {/*
          Instead of providing a static representation of what <Mouse> renders,
          use the `render` prop to dynamically determine what to render.
        */}
        {this.props.render(this.state)}
      </div>
    );

  }
}

class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>Move the mouse around!</h1>
        <Mouse render={mouse => (
          <Cat mouse={mouse} />
        )}/>
      </div>
    );
  }
}
```

