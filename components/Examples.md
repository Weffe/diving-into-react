# Examples

Let's go over a few simple examples to get you warmed up to the idea of a "Component".

## Example #1

```js
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import Hello from './Hello';

class App extends React.Component {
  render() {
    return (
      <div>
        <Hello name="Albert" />
        <p>This is a very simple example.</p>
      </div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('root'));

```

```js
// Hello.js
import React from 'react';

class Hello extends React.Component {
  render() {
    return(
      <h1>Hey there {this.props.name}!</h1>
    )
  }
}

export default Hello
```

[![Go to Example #1](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/j2nxoo851w?view=preview)

## Example #2

```js
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import Counter from './Counter';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello World!</h1>
        <Counter name="Counter 1"/>
        <Counter name="Another Counter"/>
        <Counter name="Last Counter"/>
      </div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('root'));
```

```js
// Counter.js
import React from 'react';

const styles = {
  border: '1px solid black',
  marginTop: 20,
  padding: 5
}

class Counter extends React.Component {
  constructor(props) {
    super(props)

    this.state = {value: 0}
    this.increment = this.increment.bind(this)
  }

  increment() {
    this.setState({value: this.state.value + 1})
  }

  render() {
    return(
      <div style={styles}>
        <h2 style={{color: 'blue'}}>{this.props.name}</h2>
        <div>Value: {this.state.value}</div>
        <button onClick={this.increment}>increment</button>
      </div>
    )
  }
}

export default Counter
```

[![Edit Example #2](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/6yy5x54m83?view=preview)