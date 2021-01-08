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

## Counter example with react-redux
### index.js
```javascript
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

import { Provider } from 'react-redux';
import { createStore } from '@reduxjs/toolkit';

const initialState = {
  count: 0
}

const reducer = (state = initialState, action) => {

  switch (action.type) {
    case 'INCREMENT':
      return {
        count: state.count + 1
      };
    case 'DECREMENT':
      return {
        count: state.count - 1
      };
    case 'RESET':
      return {
        count: 0
      }
    default:
      return state;
  }

}

const store = createStore(reducer);

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);
```
### app.js
```javascript
// app.js
import React from 'react';
import { connect } from 'react-redux';

const mapStateToProps = (state) => {
  return {
    count: state.count
  }
}

const App = (props) => {

  const increment = () => {
    props.dispatch({ type: 'INCREMENT' });
  }

  const decrement = () => {
    props.dispatch({ type: 'DECREMENT' });
  }

  const reset = () => {
    props.dispatch({ type: 'RESET' });
  }

  return (
    <div className="App">
      <h1>React Redux Playground</h1>

      <h2>Counter</h2>
      <div>
          <div>
            <button onClick={decrement}>-</button>
            <span className='count-span'>{props.count}</span>
            <button onClick={increment}>+</button>
          </div>
          <button onClick={reset} style={{display:'block'}}>Reset</button>
        </div>
    </div>
  );
}

export default connect(mapStateToProps)(App);
```

`TODO: Add redux-thunk to the example.`