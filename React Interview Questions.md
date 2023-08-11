
---

## React Interview Questions

---

### 1. What is React? 
**Answer:** React is a JavaScript library for building user interfaces. It's component-based, which means you can build reusable UI components.

---

### 2. What is JSX?
**Answer:** JSX stands for JavaScript XML. It's a syntax extension for JavaScript recommended by React for describing the UI. It looks like HTML in your JavaScript code.

**Example:**
```javascript
const element = <h1>Hello, world!</h1>;
```

---

### 3. What is the virtual DOM?
**Answer:** Virtual DOM (VDOM) is a programming concept where an ideal, or "virtual", representation of a UI is kept in memory and synced with the "real" DOM via a process called reconciliation. This process efficiently updates the DOM, leading to faster and smoother user experiences.

---

### 4. How is state different from props?
**Answer:** 
- **Props (short for "properties"):** are a way of passing data from parent to child components. They are read-only.
- **State:** is a data structure that starts with a default value and can change over time, usually due to user actions.

**Example:**
```javascript
// Using Props
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Using State
class Welcome extends React.Component {
  constructor(props) {
    super(props);
    this.state = { name: 'React' };
  }

  render() {
    return <h1>Hello, {this.state.name}</h1>;
  }
}
```

---

### 5. What are lifecycle methods in React?
**Answer:** Lifecycle methods are special methods that automatically get called as your component achieves certain milestones.

**Example:**
- `componentDidMount()`: Called once a component is attached to the DOM.
- `componentDidUpdate()`: Called whenever a re-render occurs.
- `componentWillUnmount()`: Called right before a component is removed from the DOM.

---

### 6. Can you explain the difference between a Class component and a Functional component?
**Answer:** 
- **Class Component:** It's ES6 class based and extends `React.Component`. It has lifecycle methods and state.
- **Functional Component:** It's just a JS function which returns JSX. Before React 16.8, functional components were stateless but with the introduction of Hooks, we can now have state and side effects in functional components.

**Example:**
```javascript
// Class Component
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

// Functional Component
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

---

### 7. What are React Hooks?
**Answer:** Introduced in React 16.8, Hooks are functions that let developers "hook into" React state and lifecycle features from function components.

**Example:**
```javascript
import { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

---

## Advanced React Interview Questions

---

### 8. What are keys in React and why are they important?

**Answer:** 
Keys are a special attribute you need to include when creating lists of elements in React. They help React identify which items have been added, removed, or changed. Keys should be given to the elements inside the array to give the elements a stable identity.

**Example:**
```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>{number}</li>
);
```

---

### 9. Explain the difference between controlled and uncontrolled components.

**Answer:** 
- **Controlled Component:** In a controlled component, the form data is handled by the React component (state). The value of the input element is controlled by React in this method.
  
- **Uncontrolled Component:** In an uncontrolled component, the form data is handled by the DOM itself. Refs are used to get values from the DOM.

**Example:**
```javascript
// Controlled Component
<input type="text" value={this.state.value} onChange={this.handleChange} />

// Uncontrolled Component
<input type="text" ref={this.inputRef} />
```

---

### 10. What is React's context API?

**Answer:** 
The Context API is a feature in React that allows you to share values like preferences, themes, or authentication status across component trees without passing props down manually at every level.

**Example:**
```javascript
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    return (
      <ThemeContext.Provider value="dark">
        <ThemedButton />
      </ThemeContext.Provider>
    );
  }
}

function ThemedButton(props) {
  return (
    <ThemeContext.Consumer>
      {theme => <button theme={theme} {...props} />}
    </ThemeContext.Consumer>
  );
}
```

---

### 11. What are higher-order components (HOC)?

**Answer:** 
HOC is a function that takes a component and returns a new component. It's a pattern derived from React's compositional nature. HOCs are common in third-party React libraries, like Redux's `connect` and React Router's `withRouter`.

**Example:**
```javascript
function withSubscription(WrappedComponent, selectData) {
  return class extends React.Component {
    // ... 
    render() {
      return <WrappedComponent data={selectData(this.props.dataSource, this.props)} {...this.props} />;
    }
  };
}
```

---

### 12. What are React Fragments?

**Answer:** 
Fragments let you group a list of children without adding extra nodes to the DOM. This is useful when a component returns multiple elements.

**Example:**
```javascript
render() {
  return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
}
```

---

### 13. What is prop drilling and how can you avoid it?

**Answer:** 
Prop drilling refers to the process of passing data with props through multiple levels of components. While it's a natural part of React's component structure, it can become tedious with deeper component trees. To avoid it, you can use React's Context API, Redux, or other state management libraries.

---

### 14. Explain the purpose of `shouldComponentUpdate` lifecycle method.

**Answer:** 
`shouldComponentUpdate` is a lifecycle method that allows you to opt out of component updates. By default, React always re-renders on state or props change. If `shouldComponentUpdate` returns `false`, the update is aborted.

**Example:**
```javascript
shouldComponentUpdate(nextProps, nextState) {
  return this.props.value !== nextProps.value;
}
```

---

---

## React Hooks Interview Questions

---

### 1. What are React Hooks?

**Answer:** React Hooks are functions that let developers "hook into" React state and lifecycle features from function components. They were introduced in React 16.8 to enable state and other React features without writing a class.

---

### 2. What is the `useState` hook? Provide an example.

**Answer:** 
The `useState` hook is used to declare state in a functional component. It returns a pair: the current state value and a function to update it.

**Example:**
```javascript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

---

### 3. What is the `useEffect` hook and how is it used?

**Answer:** 
The `useEffect` hook is used to perform side effects, such as data fetching, manual DOM manipulations, or subscriptions, in functional components. It serves the same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined in class components.

**Example:**
```javascript
import { useState, useEffect } from 'react';

function User({ userId }) {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch(`/api/users/${userId}`)
      .then(res => res.json())
      .then(data => setUser(data));
  }, [userId]);

  return (
    <div>{user ? user.name : 'Loading...'}</div>
  );
}
```

---

### 4. How do you mimic `componentDidMount` with hooks?

**Answer:** 
To mimic `componentDidMount` with hooks, you can use the `useEffect` hook with an empty dependency array. This will ensure the effect runs only once, similar to `componentDidMount`.

**Example:**
```javascript
useEffect(() => {
  console.log("Component did mount!");
}, []);
```

---

### 5. Explain the `useRef` hook with an example.

**Answer:** 
The `useRef` hook is used to access and interact with a DOM element or to keep a mutable reference to a value that doesn't trigger a re-render when changed.

**Example:**
```javascript
import { useRef } from 'react';

function TextInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus the input</button>
    </div>
  );
}
```

---

### 6. What is the `useCallback` hook?

**Answer:** 
The `useCallback` hook returns a memoized version of the callback function that only changes if one of its dependencies has changed. It's useful to prevent unnecessary renders when passing callbacks to optimized child components.

**Example:**
```javascript
import { useState, useCallback } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(prevCount => prevCount + 1);
  }, []);

  return (
    <div>
      <p>{count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

---

### 7. Explain the `useContext` hook.

**Answer:** 
The `useContext` hook allows you to access the value of a React context without wrapping your component in a `Context.Consumer`. It makes it easier to access context values in functional components.

**Example:**
```javascript
import { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function Display() {
  const theme = useContext(ThemeContext);
  return <div>The theme is {theme}</div>;
}
```

---

### 8. How does the `useReducer` hook work?

**Answer:** 
The `useReducer` hook is used for managing complex state logic in React components. It accepts a reducer function and an initial state, and returns the current state paired with a dispatch method.

**Example:**
```javascript
import { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      Count: {state.count}
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
    </div>
  );
}
```

---

I hope this README helps you prepare for the React Hooks portion of your interview. Remember, practice is key! Writing out your own examples and explaining them out loud can be a good way to solidify your understanding.
