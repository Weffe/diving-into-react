# constructor()

The `constructor` method is defined inside of the component class. 

The `constructor` is the right place to initialize state. If you don't initialize state and you don't bind methods, you don't need to implement a `constructor` for your React component. 

The `constructor` for a React component is called before it is mounted. When implementing the `constructor` for a React.Component subclass, you should call `super(props)` before any other statement. Otherwise, this.props will be undefined in the `constructor`, which can lead to bugs.

```js
import React, { Component } from 'react'

// if you need to access this.props in the constructor
class Panel extends Component {
  constructor(props) {
    super(props)
    
    this.state = { color: this.props.initColor }
  }
}
```

```js
import React, { Component } from 'react'

// if you do NOT need to access this.props in the constructor
class Panel extends Component {
  constructor() {
    this.state = { ledOn: false }
  }
}
```