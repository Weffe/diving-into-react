# componentDidMount()

`componentDidMount` is invoked immediately after a component is mounted. Initialization that requires DOM nodes should go here. If you need to load data from a remote endpoint, this is a good place to instantiate the network request. Setting state in this method will trigger a re-rendering.

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

    // example http request
    let fetchConfig = { method: 'POST', body: '10.923', mode: 'cors' }

    fetch('<SOME HTTP API URL>', fetchConfig).then((response) => {
      console.log(response)
    })
  }
}
```