componentDidMount()

The `componentDidMount` method is triggered at the end when a component is rendered at least once and is mounted onto the DOM.

```js
import React, { Component } from 'react'

class Panel extends Component {
  constructor(props) {
    super(props)
    // ...
  }

  componentDidMount() {
    if (this.props.someValue === 5) {
      this.setState({ ledOn: true })
    }
  }
}
```