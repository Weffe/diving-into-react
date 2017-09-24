 # Local State Management

 Managing local state comes into play when developing a component that requires the ability to track values or certain properties. It should be noted that local state for a component only exists when that component is mounted in the react app and will cease to exist when it is unmounted. It's also worthy to note that a component's local state cannot be implicitly shared with other components unless passed in via props. So that if you have 3 of the same components then all 3 will have their own state.

 ```js 
 // Form.js
import React, { Component } from 'react'

export default class Form extends Component {
  constructor() {
    super()
    this.state = { value: 0 }
  }

  handleChange = (e) => {
    const newValue = e.target.value
    this.setState({ value: newValue })
  }

  render() {
    return (
      <div>
        <h2>Current Value: {this.state.value}</h2>
        <input value={this.state.value} onChange={this.handleChange} />
      </div>
    )
  }
}
 ```

 [![Edit 48m2rw2y9](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/48m2rw2y9?module=%2FForm.js&view=preview)

 ## Use cases

 Some usual use cases for managing local state would be:

- Tracking the state of a button click (toggleable button)
- Whether a checkbox is marked or not
- Input values from input fields