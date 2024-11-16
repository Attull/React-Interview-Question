### 1. How does React work? How does Virtual-DOM work in React?

In React, the DOM is the representation of an HTML or XML document in memory, and the React DOM is a package that allows React components to render and update the actual DOM. When a React component’s state or properties change, the React DOM updates the actual DOM to reflect those changes.

React’s Virtual DOM (VDOM) is an abstract representation of a real DOM. In other words, the Virtual DOM acts as an intermediary between the React components and the actual DOM, providing a high-performance way to update the user interface.

The Virtual DOM in React is a concept that plays a crucial role in the library’s performance and efficiency. Updating DOM directly is a slow process when it comes to updating the structure of complex applications. Thus, the limitation of DOM leads to the concept VDOM.

When a component’s state or properties change, React updates the VDOM, which then calculates the minimum number of actual DOM updates required to reflect the changes. This process of updating the VDOM first before updating the actual DOM results in much faster updates, as the cost of changing the real DOM is significantly higher compared to updating the virtual DOM.

Summary
1. React updates the Virtual DOM : When a component’s state or properties change, React updates the Virtual DOM to reflect the changes.
2. Virtual DOM diffing : React then compares the updated Virtual DOM with a previous version of the Virtual DOM to determine the minimum number of updates necessary to the actual DOM. This process is called “diffing.”
3. Batch updates to the actual DOM : React then batches the necessary updates to the actual DOM, reducing the number of DOM updates and minimizing the impact on performance.

The major features of React are:
*	It uses VirtualDOM instead of RealDOM considering that RealDOM manipulations are expensive.
*	Follows Unidirectional data flow or data binding.
*	Uses reusable/composable UI components to develop the view.

### 2. What is JSX and why do we use it in React?

JSX is a powerful JavaScript Extension that enables the seamless integration of HTML-like structures within React.

Key Features
Readable Syntax: Familiar HTML tags make parsing code and debugging simpler.

Component Embedding: JSX supports direct embedding of components, which enhances modularity.

Automatic Babel Conversion: Behind the scenes, JSX and its HTML-like tags are transpiled by Babel into JavaScript for browser compatibility.

#### Code Example: JSX and Its Transpiled Output
Here is the JSX code
```js
const element=(
  <h1 classname="greeting">
    Hello World!
  </h1>
```
Here is the equivalent JS code transpiled by Babel:
```js
const element= React.createElement(
  'h1',
  {"classname": "greeting"},
  'Hello World!'
);
```

### 3.Why can’t browsers read JSX?

Browsers can only read JavaScript objects but JSX in not a regular JavaScript object. Thus to enable a browser to read JSX, first, we need to transform JSX file into a JavaScript object using JSX transformers like Babel and then pass it to the browser.

### 4.“In React, everything is a component.” Explain.

Components are the building blocks of a React application’s UI. These components split up the entire UI into small independent and reusable pieces. Then it renders each of these components independent of each other without affecting the rest of the UI.

### 5. Functional components vs Class componenets

In React, components are the building blocks of your UI. They are reusable pieces of code that can be used to render different parts of your application.

There are two primary ways to create React components:

1. Functional Components:

* Simpler and more concise syntax.
* Written as plain JavaScript functions that take props as arguments and return JSX. 
* Can use React Hooks (introduced in React 16.8) to manage state and side effects.
* Generally preferred for most new projects due to their simplicity and readability.

```js
import React from 'react';

const Greeting = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};
```

2. Class Components:

* More complex syntax, using ES6 class syntax.
* Extends from React.Component and requires a render() method that returns JSX.
* Traditionally used for managing state and lifecycle methods.
* Can still be used, but generally considered less preferred for new projects.

```js
import React, { Component } from 'react';

class Greeting extends Component {
  
  constructor(){
  }

  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

### 6.What are props?

Props: Passing Data from Parent to Child

Props stands for properties and they are used to pass data between React components. React’s data flow between components is uni-directional (from parent to child only).

Props are Immutable:Props are read-only and cannot be modified within the component that receives them. They are intended to be a one-way communication from parent to child.

```js
// Parent Component
function App() {
  return (
    <ChildComponent name="John" age={30} />
  );
}

// Child Component
function ChildComponent(props) {
  return (
    <div>
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
    </div>
  );
}
```

### 7.What are state?

State: Managing Component-Specific Data

While props are used for passing data from parent to child, state is used to manage data that can change over time within a component. Unlike props, state is managed within the component itself.

```js
function Counter() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}
```

### 8.Differences Between Props and State ?

Here are the key differences between props and state:

* Ownership: Props are owned by the parent component and passed down to child components, while state is owned and managed within the component itself.
* Mutability: Props are immutable, meaning they cannot be changed by the child component. State, on the other hand, can be changed using the setState function.
* Usage: Props are used to pass data from parent to child components, while state is used to manage data that can change over time within a component.

### 9.What are Higher Order Components(HOC)?

Higher Order Component is an advanced way of reusing the component logic. Basically, it’s a pattern that is derived from React’s compositional nature. HOC are custom components which wrap another component within it.
HOC can be used for code reuse & logic.

### 10.What are React Hooks?

React Hooks are functions that allow you to use state and other React features in functional components. Before hooks, stateful logic was only possible in class components. They were introduced in React 16.8 to enable developers to write cleaner and more reusable code by eliminating the need for classes.

* useState
* useEffect
* useContext
* useCallback
* useMemo
* useRef