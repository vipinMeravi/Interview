Q. Redux Core Concepts (Actions, Reducers, Store)
A. Redux is a JS library for predictable and maintainable global state management.
Redux is a predictable state container for javascript applications. It helps mange the state of an application in a consistent and centralized manner.
Redux operates based on three core principles: 
1. Single source of truth: The entire state of the application is stored in a single object within a cental store.
2. State is Read-Only: The state can only be changed by dispatching actions, which describes the changes that should occur.
3. Changes are made in pure functions: Reducers are pure functions that take the current state and an action, and return a new state, ensuring that the state transitions are predictable and traceable.

 "dispatch" is a function that sends an action to the Redux store.

Core Concepts of Redux
Actions
Reducers
Store
1. Actions
Actions are plain JavaScript objects that represent an intention to change the state. They are the only source of information for the store. Every action must have a type property that indicates the type of action being performed, and it can optionally have additional data.

Example of an Action:
const addAction = {
  type: 'ADD_TODO',
  payload: {
    id: 1,
    text: 'Learn Redux'
  }
};

Action Creators:

Action creators are functions that create and return action objects.
function addTodoAction(text) {
  return {
    type: 'ADD_TODO',
    payload: {
      id: Math.random(),
      text
    }
  };
}

2. Reducers
Reducers are pure functions that specify how the application's state changes in response to actions. A reducer takes the current state and an action as arguments and returns a new state.

Example of a Reducer:
const initialState = {
  todos: []
};

function todoReducer(state = initialState, action) {
  switch (action.type) {
    case 'ADD_TODO':
      return {
        ...state,
        todos: [...state.todos, action.payload]
      };
    default:
      return state;
  }
}

3. Store
The store is an object that holds the application's state. It provides methods to access the state, dispatch actions, and register listeners.

Creating a Store:
import { createStore } from 'redux';

// Assume todoReducer is already defined
const store = createStore(todoReducer);

Accessing the State:
const currentState = store.getState();
console.log(currentState);

Dispatching Actions:
store.dispatch(addTodoAction('Learn Redux'));

Subscribing to Changes:
store.subscribe(() => {
  console.log('State changed:', store.getState());
});


Q. Immutable State and Pure Functions.
A. => Immutable State
Immutable state means that the state cannot be changed directly. Instead of modifying the existing state object, a new state object is created with the updated values.

=> Pure functions are functions that meet the following criteria:
-Deterministic: Given the same input, a pure function will always return the same output.
-No Side Effects: Pure functions do not cause any side effects. They do not modify external state, perform I/O operations, or rely on data that may change over time.

Q. Redux Middleware (e.g., redux-thunk, redux-saga)
Actions and Action Creators
Store and createStore()
Q. combineReducers()
A. combineReducers
combineReducers is a utility function in Redux that allows you to combine multiple reducer functions into a single reducer. This is useful when you have multiple pieces of state that are managed by different reducers, and you want to combine them into a single state object.

How combineReducers Works:
Each reducer manages its own part of the global state.
combineReducers maps each reducer to a specific key in the state object.
When an action is dispatched, each reducer receives the action, and the resulting state is combined into a single state object.

Q. Connecting Redux to React Components (e.g., mapStateToProps, mapDispatchToProps)
A. The primary tool for connecting Redux to React is the connect function provided by the react-redux library.
eg: 
<!-- Connect example -->
import { connect } from 'react-redux';
import { increment, decrement } from './actions';

const Counter = ({ count, increment, decrement }) => (
  <div>
    <p>Count: {count}</p>
    <button onClick={increment}>Increment</button>
    <button onClick={decrement}>Decrement</button>
  </div>
);

const mapStateToProps = (state) => ({
  count: state.counter.count
});

const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch(increment()),
  decrement: () => dispatch(decrement())
});

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
<!-- Connect example -->

Map State and Dispatch to Props: Use the mapStateToProps and mapDispatchToProps functions to map the Redux store state and action dispatch functions to props in your connected component.

=> mapStateToProps: Maps state from the Redux store to props in your component.
=> mapDispatchToProps: Maps action dispatch functions to props in your component.

Q. Redux DevTools Extension (Time-Travel Debugging)
A. The Redux DevTools Extension is a powerful tool that enhances the development experience when working with Redux. It provides a visual interface to inspect and debug Redux state changes, time-travel through actions, and analyze performance. 
<!-- Example -->
import { createStore } from 'redux';
import { composeWithDevTools } from 'redux-devtools-extension';
import rootReducer from './reducers';

const store = createStore(
  rootReducer,
  composeWithDevTools()
);

export default store;
<!-- Example -->

Q. Asynchronous Actions in Redux
A. Asynchronous actions in Redux allow you to handle asynchronous logic, such as fetching data from a server or performing asynchronous computations, in your Redux applications. Redux itself is synchronous, but you can use middleware like redux-thunk, redux-saga, or redux-observable to handle asynchronous actions.

Thunks vs. Sagas for Handling Side Effects
Handling Complex State in Redux
Normalizing State Shape
Using Selector Functions (reselect) for Efficient State Access
Redux Best Practices and Code Structure
Unit Testing Redux Code (e.g., reducers, actions)
Managing Authentication State with Redux
Redux Middleware (Custom Middleware)
Redux Middleware Execution Order
Performance Optimization Techniques with Redux
Handling Errors in Redux Applications
Integrating Redux with Other Libraries (e.g., React Router)
Redux Toolkit and Simplified Redux Setup
Redux vs. Context API for State Management in React
Migrating from Redux to Redux Toolkit
Redux in Large-Scale Applications