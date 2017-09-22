# What makes up a Component

As you can see from the examples, every component has a `render` method defined inside it's class. Like the `render` method there are other methods that are supported through a components lifecycle. Methods marked with a :star: will be the ones we will primarily use while developing the User Interface. 

## Mounting

These methods are called when an instance of a component is being created and inserted into the DOM:

  - `constructor()` :star:
  - `componentWillMount()`
  - `render()` :star:
  - `componentDidMount()` :star:

## Updating

An update can be caused by changes to props or state. These methods are called when a component is being re-rendered:

  - `componentWillReceiveProps()`
  - `shouldComponentUpdate()`
  - `componentWillUpdate()`
  - `render()` :star:
  - `componentDidUpdate()`

## Unmounting

This method is called when a component is being removed from the DOM:

  - `componentWillUnmount()`

## Other APIs

Each component also provides some other APIs:

  - `setState()` :star:
  - `forceUpdate()`

## Class Properties

  - `defaultProps` 
  - `displayName`

## Instance Properties

  - `props`
  - `state`

---

**For a full read on the component lifecycle: [click here](https://facebook.github.io/react/docs/react-component.html)**