# render()

**The `render()` method is required.**

When called, it should examine this.props and this.state and return a single React element. This element can be either a representation of a native DOM component, such as `<div />`, or another composite component that you've defined yourself.

You can also return null or false to indicate that you don't want anything rendered. When returning null or false, ReactDOM.findDOMNode(this) will return null.

The `render()` function should be pure, meaning that it does not modify component state, it returns the same result each time it's invoked, and it does not directly interact with the browser. If you need to interact with the browser, perform your work in `componentDidMount()` or the other lifecycle methods instead. Keeping `render()` pure makes components easier to think about.

In short terms, `render` only has 1 job and does not modify anything. You can perform math calculations in `render` but not direct state manipulation!

```js
import React, { Component } from 'react'

class VoltageMeter extends Component {
    render() {
        const { voltage } = this.state 

        if (voltage > 9000) {
            return null
        }

        return (
            <div>
                <h1>Voltage Meter</h1>
                <span>Current Voltage Reading: {voltage}</span>
            </div>
        )
    }
}

```