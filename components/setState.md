# setState()

setState() enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state. This is the primary method you use to update the user interface in response to event handlers and server responses.

Think of setState() as a request rather than an immediate command to update the component. For better perceived performance, React may delay it, and then update several components in a single pass. React does not guarantee that the state changes are applied immediately.

setState() does not always immediately update the component. It may batch or defer the update until later. This makes reading this.state right after calling setState() a potential pitfall. Instead, use componentDidUpdate or a setState callback (setState(updater, callback)), either of which are guaranteed to fire after the update has been applied.

## setState has 2 function signatures

1. `setState(updater: function, [callback])`
    
2. `setState(stateChange: object, [callback])`

### setState(updater: function, [callback])

```js 
setState((prevState, props) => stateChange)
```

prevState is a reference to the previous state. It should not be directly mutated. Instead, changes should be represented by building a new object based on the input from prevState and props. For instance, suppose we wanted to increment a value in state by props.step:

```js
this.setState((prevState, props) => {
  return {counter: prevState.counter + props.step}
})
```

Both prevState and props received by the updater function are guaranteed to be up-to-date. The output of the updater is shallowly merged with prevState.

### setState(stateChange: object, [callback])

```js
this.setState({ledOn: true})
```

This form of setState() is also asynchronous, and multiple calls during the same cycle may be batched together. Subsequent calls will override values from previous calls in the same cycle, so the quantity will only be incremented once.

```js
// these 3 calls will be batched together as 1 single call 
// and counter will only be incremented once at the end.
this.setState({counter: this.state.counter + 1})
this.setState({counter: this.state.counter + 1})
this.setState({counter: this.state.counter + 1})
```

 If the next state depends on the previous state, we recommend using the updater function form. 

 ```js
this.setState((prevState) => {
  return {counter: prevState.counter + 1}
})
this.setState((prevState) => {
  return {counter: prevState.counter + 1}
})
this.setState((prevState) => {
  return {counter: prevState.counter + 1}
})
 ```