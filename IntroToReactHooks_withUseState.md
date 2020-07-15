
# An Intro into React Hooks with `useState` 

First, lets get a baseline. 

React hooks allow developers to encapsulate abstract logic that can be re-used in some, a few or many components within a react application. Since state is one of the most cumbersome items to manage within a react application; most react hooks help manage state. In fact, one of the most-used react hooks is called `useState` and (unsurprisingly) it abstracts the code surrounding using state, allowing the developer to focus more on application functionality and less on the technicalities surrounding creating, modifying, and retrieving state. 

## Old vs. New 

To better understand this, let's take a look at a traditional component built **without** hooks. 

```js
import React from 'react' 
// a Counter component that allows an end-user to increment or decrement a counter 
class Counter extends React.component {
  constructor(props) {
    super(props)
    this.state = { count: 0 }
  }

  // increment the value of the counter, defaulting to increase of 1
  increment(amount = 1){
    this.setState(prevState => {
      return { count: prevState.count + amount }
    })
  }
  
  // decrement the value of the counter, defaulting to a decrement of 1
  decrement(amount = 1){
    this.setState(prevState => {
      return { count: prevState.count - amount }
    })
  }

  // reset the counter to the initial state 
  reset() {
    this.setState({ count: 0 })
  }

  render() {
    return (
      <div>
        <span>{this.state.count}</span>
        <button onClick={ e => increment() }>+</button>
        <button onClick={ e => decrement() }>-</button>
        <button onClick={ e => reset() }>Reset</button>
      </div>
    )
  }
}
```

The code above demonstrates a traditional react component built with class-based inheritance. With hooks, we can transition this code to a more _functional_ approach, with less "boiler-plate" code. 


```js
import React, { useState } from 'react' 

function Counter (props) {
  const [value, setValue] = useState(0)

  function increment(amount = 1){
    setValue(value + amount)
  }

  function decrement(amount = 1){
    setValue(value - amount)
  }

  function reset(){
    setValue(0)
  }

  return (
      <div>
        <span>{this.state.count}</span>
        <button onClick={ e => increment() }>+</button>
        <button onClick={ e => decrement() }>-</button>
        <button onClick={ e => reset() }>Reset</button>
      </div>
    )
}
```

## Getting started 

The first thing that changes, is that inherently, functions are **stateless**. In order to circumvent this limitation hooks offload that task to a seperate function: `useState`. 

So first we must import `useState` from the React library: 
```js 
import React { useState } from 'react' 
```

Now instead of setting the initial state in the constructor of the component (functional components do **not** have constructors), we set state in the constructor of the `useState` hook: `useState(initialValue)`. 

```js
// old 
class Counter extends React.component {
  constructor(props) {
    super(props)
    this.state = { count: 0 } // providing initial value 
  }
}
// new 
import { useState } from 'react'
function Counter(props){
  const [count, setCount] = useState(0) // providing initial value
}
```
Unlike class-based state, `state` using hooks can be of any data type (recall that class-based components are hashes). 

### Mutating State 

The `useState` hook returns two variables to the caller: 
1. a variable that can be used to access the current state. 
2. a function that can be used to mutate state. 

It is up to the developer to name the returned values accordingly, but by convention it is common to name the returned values as 'value' and 'setValue' as `[value, setValue]` or in the case of our `Counter` component: `[count, setCount]`. 

When we want to change state, we have a couple options: 
1. We can directly modify the state, in which we use the `setValue` function returned by `useState` to mutate the value. 
2. We can provide a function that mutates the state, in which the function recieves (as an argument) the previous state and the output of that function is the new state. 

This would be contrasted with the component based approach, where we must use a function that recieves the previous state as the argument and returns the new state:

```js
// Component based approach 
increment(amount = 1){
  this.setState(prevState => {
    return { count: prevState.count + amount }
  })
}
```
So with hooks, we could do the same thing: 
```js
// functional approach mirroring the component based approach 
function increment(amount = 1){
  setCount(previousCount => { 
    return previousCount + 1
  })
} 
// or (shorthand)
function increment(amount = 1){
  setCount(previousCount => previousCount + 1)
} 
```

But with functional components we could simplify this even more: 
```js
function increment(amount = 1){
  setCount(count + 1)
} 
```
Since we already have the current count in memory, all we have to do is access that and implement the same logic, since whatever is placed in the `setCount` function will be the new value for state. 

## The Gotchas 

With class-based state, we typically store data in a hash, we then copy and modify the state in order to mutate it. While we could do this with the `useState` hook, it is not recomended. Instead, it is more efficient (and likely more readable) to place each piece of state in seperate state variables: 

```js
//incorrect: 
const [state, setState] = useState({ count: 0, color: 'blue'})

// correct 
const [count, setCount] = useState(0)
const [color, setColor] = useState('blue') 
```

Why? 

This would be best answered by reviewing an example; imaginge we had a component that needed to manage states including `count` and `color`... To change the color of the component with class-based components we would: 

```js
function changeColor(newColor){
  this.setState(previousState => {
    // copy previous state and overwrite color attribute 
    return {...previousState, color: newColor }
  })
}
```
In functional components, leveraging the `useState` hook, it would look like: 
```js
function changeColor(newColor) {
  setColor(newColor)
}
```

So why would we use hooks instead of classes? 
1. When you update state, it is more clear what is changing
2. The syntax is more readable and concise
3. It is more effecient ( we are not repeatably copying and overwritting data) 


# Summary 

Woah, I know that could be a lot to grasp at once, so here are the key take aways: 

1. React hooks abstract functionality that would typically require a class-based component into a function that can be used in **any** component within a React application. 
2. The `useState` hook allows us to more simply manage state than the traditional class-based approach. 
3. If there are multiple pieces of state to be modified, those should be seperated into seperate pieces of state with their own accessor and setter. 
