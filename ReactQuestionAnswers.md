Q. What is react js and latest version (14-06-2024)?
A. React is a javascript library for building user interface (18.3.1).

Q. What are react components?
A. -> React apps are made out of Components. A Component is a piece of the UI (USER INTERFACE) that has its own login and appearance. A Component can be small as button, as large as an entire page.
-> React components are javascript functions that returns markup.
-> React component names must always start with capital letter.
-> The export default keywords specify the main component in the file.

   -> Components are the building block of React. Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML. 
   -> We can say that every application you will develop in React will be made up of pieces called Components.

Q. What is JSX?
A. JSX is a powerful feature of React that allows developers to write HTML like syntax directly in Javascript. It combines the expressiveness of HTML with the power of Javascript, making it a core part of the React ecosystem.
Q. .JS vs .JSX?
A. The use of .js and .jsx extensions in React projects is a matter of convention and clarity. While .js is a general-purpose JavaScript file extension, .jsx explicitly indicates that the file contains JSX code. The distinction helps with organization, readability, and can leverage specific tooling advantages. However, functionally, there is no difference between the two, and both can be used to write React Component.

Q. What is Fragment?
A. React Fragments provide a way to group multiple React elements without adding extra nodes to the DOM. They allow you to return multiple elements from a component's render method without needing to wrap them in a parent element like a div. Fragments were introduced in React 16.2 as a lightweight way to solve the problem of returning adjacent JSX elements without a common parent.

Q. Types of react components?
A. 
-. Functional (Stateless) Component
Functional components are simple JavaScript functions that accepts props as an argument and return React elements. They are also known as stateless component because, historically, they did not manage state or lifecycle methods.
Characteristics: 
=> Simpler Syntax: Functional components are typically shorter and simpler to write that class-based component.
=> No 'this' Keyword: They do not use the 'this' keyword, making them easier to read and understand.
=> Hooks: With the introduction of React Hooks in version 16.8, functional components gained the ability to manage state and side effects, making them as powerful as class-based components.

-. Class Components.
Class based components are created using E6 classes. They can mange their own state and use lifecycle methods to perform actions at different stages of the component's lifecycle.
Characteristics: 
=> State and Lifecycle Methods: Class based components can manage local state and implement lifecycle methods such as 'componentDidMount'.
=> 'this' Keyword: They require the use of the 'this' keyword to access props, state, and other class methods.
=> More Boilerplates: They generally require more boilerplate code compared to functional components.

-. Higher Order Components.
An HOC is a function that takes a component and returns a new component:
-. Dumb Components.
In React, a "dumb component" (also known as a presentational component) is a component that is concerned primarily with how things look. It does not manage its own state (except for state related to UI like form inputs) or handle any business logic. Instead, it receives data and functions via props from its parent component, which handles the state and logic.
Characteristics of Dumb Components
= Stateless: They don't manage their own state, except for UI-specific state.
= Props-based: They rely on props to receive data and functions.
= Reusable: Because they don't contain business logic, they are easily reusable across different parts of an application.
= Focus on UI: Their main concern is how things look, not how they work.
-. Smart Components.
A "smart component" (also known as a container component) handles state and logic, passing necessary data and functions to the dumb component:
-. Presentational Components.
a "dumb component" (also known as a presentational component)
-. Container Components.
A "smart component" (also known as a container component)

-. Pure Components.
A pure component is a component that renders the same output given the same input. In other words, it doesn't produce side effects or depend on anything other than its props and state. Pure components help in optimizing performance by preventing unnecessary re-renders.
<!-- Pure component -->
import React from 'react';

const PureCounter = React.memo(({ count }) => {
  console.log('PureCounter rendered');
  return <div>Count: {count}</div>;
});

export default PureCounter;

-. Impure Components
An impure component is a component that can produce different outputs even if given the same props and state. These components might have side effects, or their rendering might depend on factors other than their props and state.
<!-- Impure component -->
import React from 'react';

class ImpureCounter extends React.Component {
  render() {
    console.log('ImpureCounter rendered');
    return <div>Count: {this.props.count + Math.random()}</div>;
  }
}

export default ImpureCounter;

-. 
-. Context Components.

Q. What are side effects in React Js?
A. In React side effects refer to operations that can affect other part of the application or interact with external systems. These operations are typically asynchronous and can include things like data fetching, subscriptions, timers, logging, and manual DOM manipulation.

Q. How to handle side effects in functional components.
A. In functional components, side effects are handled using the 'useEffect' Hook. The 'useEffect' Hook allows you to perform side effects in function components and runs after the component renders.

Q. useEffect?
A. Effect function: The first argument to 'useEffect' is the effect function where you place your side effect code.
Cleanup Function: The effect function can return a cleanup function. This cleanup function is executed when the component unmounts or before the effect runs again.
Dependency Array: The second argument to 'useEffect' is an optional dependency array. The effect will only re-run if one of the dependencies changes.

Q. Hooks?
A. In React, Hooks are functions that allows you to "hook into" React state and lifecycle features from function components. They were introduced in React 16.8 to provide a more flexible and simpler way to manage state and side effects in functional components, without the need to use class-based components.

Built-In hooks:
1. 'useState': Allows you to add state to functional components.
2. 'useEffect': Allows you to perform side effects in functional components, such as data fetching or subscribing to events.
3. 'useContext': Allows you to use the context API to share values between components without passing props manually through every level of the tree.
4. 'useReducer': A more advanced state management Hook, useful for managing complex state logic.
5. 'useRef': Allows you to persist values across renders without causing a re-render when updated, often used to access DOM elements directly.
6. 'useMemo': Memoizes the result of a function, re-calculating only when dependencies change.
7. 'useCallback': Returns a memoized callback function, re-creating it only when dependencies change.
8. 'useLayoutEffect': Similar to useEffect, but fires synchronously after all DOM mutations.
9. 'useDebugValue': Adds debug information to custom Hooks for development tools.

Custom Hooks: 
Custom Hooks are a way to reuse stateful logic across multiple components. A custom Hook is a JavaScript function whose name starts with "use" and that may call other Hooks. Custom hooks enable the encapsulation and reuse of stateful logic, leading to cleaner and more maintainable React code.

Q. What are lifecycle methods?
A. Lifecycle methods in React are special methods that get called at different states of a component's existence. They allow developers to hook into specific points in the component's lifecycle, such as when it mounts, updates, or unmounts. Lifecycle methods are primarily used in class-based components, but similar behaviors can be achieved in functional components using Hooks.

=> Class based components have a series of lifecycle methods divided into three main phases: 
1. Mounting : When a component is being inserted into the DOM.
2. Updating : When a component is being re-rendered due to changes in props or state.
3. Unmounting: When a component is being removed from the DOM.

+=> MOUNTING:
1. constructor: Called before the component is mounted. Used for initializing state and binding event handlers.
<!-- Constructor -->
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
}
<!-- Constructor -->

2. 'static getDerivedStateFromProps': Invoked right before calling the render method, both on the initial mount and on subsequent updates. Used to update the state based on props.
<!-- getDerivedStateFromProps -->
static getDerivedStateFromProps(nextProps, prevState) {
  // Return an object to update state or null to update nothing.
  if (nextProps.value !== prevState.value) {
    return { value: nextProps.value };
  }
  return null;
}
<!-- getDerivedStateFromProps -->

3. render: The only required method in a class component. Returns the React elements to be rendered.
4. 'componentDidMount': Called after the component is mounted. Used for side effects like fetching data or setting up subscriptions.

+=> UPDATING:
1. 'static getDerivedStateFromProps': Also called during updates.
2. 'shouldComponentUpdate': Determine if the component should re-render in response to state or prop changes. Return a boolean value.
<!-- shouldComponentUpdate -->
shouldComponentUpdate(nextProps, nextState) {
  // Return true to update or false to prevent update
  return nextState.count !== this.state.count;
}
<!-- shouldComponentUpdate -->

3. render
4. 'getSnapshotBeforeUpdate': Called right before the DOM is updated. It allows you to capture some information (e.g., scroll position) from the DOM before it changes.
<!--  -->
getSnapshotBeforeUpdate(prevProps, prevState) {
  // Return a snapshot value (or null)
  return { scrollPosition: window.scrollY };
}
<!--  -->

5. 'componentDidUpdate': Called after the component has updated. Used to perform side effects based on the changes in state or props.

+=> UNMOUNTING: 
1. 'componentWillUnmount': Called right before the component is removed from the DOM. Used to clean up side effects like canceling network request or removing event listeners.

Q. What is Props drilling in React JS?
A. Prop drilling in React refers to the process of passing props down through multiple layers of components in order to reach a deeply nested component that needs access to those props. While prop drilling is a common pattern in React, it can lead to issues such as decreased code maintainability and readability, as well as potential performances problems.
==> Solutions to Prop Drilling
 = Context API: Use React's Context API to provide values to components deep within the component tree without explicitly passing props through intermediate components. Context provides a way to share values between components without having to explicitly pass props through each level of the tree.

 = State Management Libraries: Use state management libraries like Redux, MobX, or Recoil to manage shared state in a centralized store and access it from any component in the application, eliminating the need for prop drilling.

 = Higher-order Components (HOCs): Use HOCs to wrap components and provide them with additional props or functionality without directly passing props through intermediate components.

 = Render Props: Use the render prop pattern to pass a function as a prop to components, allowing them to render content based on that function's return value. This can be an alternative to prop drilling when passing data or behavior down the component tree.

 Q. What are context?
 A. Context is a feature that allows you to share values (such as theme, user data, or configuration settings) between components without having to pass props down through every level of the component tree. This is particularly useful ofr deeply nested components or when certain data needs to be accessible by many components at different levels.

 Q. Working of Context?
 A. 1. Context Provider: This component provides the context value to its children.
 2. Context Consumer: This component subscribes to the context value and uses it.
 3. React.createContext: This function creates a Context object.

 Q. Why Context?
 A. Benefits/Advantages of Using Context.
 1. Avoids Prop Drilling: Context helps avoid passing props through many levels of the component tree, simplifying your code and making it more maintainable.
 2. Global State management: Context can be used to mange global state in your application, making certain values accessible across different components.
 3. Decoupled Components: Components become more decoupled and easier to reuse since they don't need to receive all there data through props.

 Q. Error Boundaries?
 A. In React functional components, error boundaries are a feature that helps to handle errors that occur during rendering, in lifecycle methods, and in constructors of the whole component tree. They catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the entire component tree.
implement error boundaries in React functional components:
1. Create an Error Boundary Component:
2. Wrap Components with ErrorBoundary:
Wrap the components you want to be covered by the error boundary with the ErrorBoundary component.
3. Fallback UI:
In the render() method of the ErrorBoundary component, you can specify what UI to display in case an error occurs within its child components.
4. Logging Errors:
Use the componentDidCatch lifecycle method to log errors to an error reporting service or console. This helps in diagnosing and fixing issues.

=> Remember, error boundaries only catch errors during rendering, not during event handling, asynchronous code (e.g., setTimeout or requestAnimationFrame callbacks), or in custom event handlers.


