# react-redux
## keywords

* The ```state``` is the data, and the ```store``` is where it’s kept.

* ```Redux``` gives you a store, and lets you keep state in it, and get state out, and respond when the state changes.


* ```react-redux``` lets you connect pieces of the state to React components.

* ```reducer```: It takes the current state, and an action, and returns the newState.

  * Reducer rule #1: Never return undefined from a reducer.

  * Reducer rule #2: Reducers must be pure functions.

* An ```action``` is plain object with a property called type. eg. ```{ type: 'ACTION_NAME' }```
  * In order to make an action DO something, you need to dispatch it. The store object has a built-in function called dispatch. Call it with an action, and Redux will call your reducer with that action (and then replace the state with whatever your reducer returned).
  
  * ```store.dispatch({ type: 'ACTION_NAME' });```

* ```Provider``` and ```connect()```: By wrapping the entire app with the Provider component, every component in the app tree will be able to access the Redux store if it wants to. But not automatically. We’ll need to use the connect function on our components to access the store.

> TODO: Add an example here.