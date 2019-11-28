---
title: Hooks
---

# Hooks

## Why Hooks

Hooks overcomes many of the issues that we come across when using class based components. 

- Calling Super(props) is annoying
- Classes make knowing how 'this' works difficult at times
- Organizing components by life-cycle methods forces us to sprinkle related logic throughout our components.
- React has no good primitive for sharing non-visual logic.

## Just use Functions

Using functions instead of classes removes the Super(props) and 'this' issues right away. Ok great now what about state and life-cycle methods, they are kind of handy.

## State

No need for a class based component. You will need to import 'useState' into your functional component.

```javascript
import React, { useState } from 'react'

const Shop = props => {
  const [cart, setCart] = useState([])
  const cartHandler = () => {
    setCart(['A Book'])
  }
  return <button onClick={cartHandler}>Add to Cart</button>
}
```

useState() returns an array with two elements. The first element is the state and the second is a function that will set the state. 

State is not just one object containing everything. You can have several 'states' and they can be anything like a string or boolean, whatever. It does not have to be an array as shown above.

If you have multiple pieces if state that you need to track just create them like this...

```javascript
  const [cart, setCart] = useState([])
  const [myList, setMyList] = useState('not an array')
```

When you set state it will completely replace state. You don't just pass in updates as you did in a class based component. So if your state was set to {el1: 'one', el2: 'two'} you could not just do 

```javascript
setState({el2: 'three'})
```

 you would have to either do 

```javascript
setState({...state}, {el2: 'three'})
```

 or something similar.

## Lifecycle Methods

It looks like lifecycle Methods are sort of being referred to as 'side effects' under React Hooks. The core React Hook that will be used in place of the Lifecycle Methods is called useEffect().

### componentDidMount

To perform the functionality of the class based componentDidMount do the following

```javascript
import React, { useState, useEffect } from 'react'

const Shop = props => {
  const [products, setProducts] = useState([])

  useEffect(() => {
    fetch('my-backend.com/products')
      .then(res => res.json())
      .then(fetchedProducts => setProducts(fetchedProducts))
  }, [])

  return (

    <ul>
      {products.map(product => (
        <li key={product.id}>{product.name}</li>
      ))}
    </ul>

  )
}
```

The key here is the second element of the useEffect function, the empty array []. The second element controls when this function gets run. It will run whenever the second element changes. So setting the second element to an empty array will ensure that it will never change and never run again.

## useParams

useParams will pull any parameter values from the route. In this example the route was something like /:userId/places. 

```javascript
import { useParams } from "react-router-dom";
...
  const userId = useParams().userId;
```

