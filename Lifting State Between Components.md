# Lifting State Between Components

Let's say we have an app that has 3 `<Counter />` components and we want to display the sum of each `<Counter />` value. In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called "lifting state up".

Let's dive into an example. Take our `<Counter />` component:

```js
// Counter.js
import React, { Component } from 'react'

export default class Counter extends Component {
  constructor(props) {
    super(props)
    this.state = { value: 0 }
  }

  increment = () => {

    const { name, updateParent } = this.props

    this.setState((prevState) => {
      // increment local state value
      const newValue = prevState.value + 1 

      // call the function updateParent that's passed in as a prop
      updateParent(name, newValue)

      return { value: newValue }
    })
  }

  render() {
    return (
      <div>
        <h2>Current Value: {this.state.value}</h2>
        <button onClick={this.increment}>increment</button>
      </div>
    )
  }
}
```

[![Edit Lifting State Up](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/72v16omrn6?module=%2FCounter.js)

## Yes, functions can be passed in as a Prop! Just like functions can be passed off as callbacks :)

Next, we examine our `<Parent />` component:

```js
// Parent.js
import React, { Component } from 'react'
import Counter from './Counter'

export default class Parent extends Component {
  constructor() {
    super()
    this.state = {
      counter1: 0,
      counter2: 0,
      counter3: 0
    }
  }

  updateParent = (name, value) => {
    this.setState({ [name]: value })
  } 

  render() {
    const { counter1, counter2, counter3 } = this.state

    return (
      <div>
        <h1>Sum: { counter1 + counter2 + counter3 }</h1>

        <Counter name="counter1" updateParent={this.updateParent} />

        <Counter name="counter2" updateParent={this.updateParent} />

        <Counter name="counter3" updateParent={this.updateParent} />
      </div>
    )
  }

}
```

[![Edit Lifting State Up](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/72v16omrn6?module=%2FParent.js)