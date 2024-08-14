# How to pass value from child component to parent component
### What is a callback function?
### Callback Function in React

A callback function in React is a function that is passed as a prop from a parent component to a child component. It is typically used to allow the child component to communicate with the parent component. This pattern is particularly useful when you want to pass data or trigger actions in the parent component based on events that happen in the child component.

### Key Points About Callback Functions in React

1. **Defined in the Parent Component**:
   - The callback function is usually defined in the parent component. This function will do something in the parent component, like updating state or logging data.

2. **Passed as a Prop to the Child Component**:
   - The parent component passes the callback function to the child component as a prop.

3. **Called in the Child Component**:
   - The child component can call the callback function, typically in response to some user interaction (e.g., a button click). When called, the callback function can pass data back to the parent component.

### Example of a Callback Function in React

#### Parent Component:
```jsx
import React, { useState } from 'react';

function ParentComponent() {
  const [message, setMessage] = useState('');

  // Callback function defined in the parent
  const handleMessageChange = (newMessage) => {
    setMessage(newMessage);
  };

  return (
    <div>
      <h1>Parent Component</h1>
      <p>Message from Child: {message}</p>
      {/* Passing the callback function to the child as a prop */}
      <ChildComponent onMessageChange={handleMessageChange} />
    </div>
  );
}
```

#### Child Component:
```jsx
import React from 'react';

function ChildComponent({ onMessageChange }) {
  const handleClick = () => {
    // Calling the callback function and passing data to the parent
    onMessageChange('Hello from Child!');
  };

  return (
    <div>
      <h2>Child Component</h2>
      <button onClick={handleClick}>Send Message to Parent</button>
    </div>
  );
}

export default ParentComponent;
```

### How It Works

1. **Defining the Callback**:
   - The `ParentComponent` defines a callback function `handleMessageChange` that updates the parent's state.

2. **Passing the Callback**:
   - This function is passed to the `ChildComponent` via the `onMessageChange` prop.

3. **Calling the Callback**:
   - Inside the `ChildComponent`, the `handleClick` function is called when the button is clicked. This function triggers the `onMessageChange` callback, sending the string `"Hello from Child!"` back to the parent component.

4. **Parent Reacts to Child**:
   - The parent component receives this message and updates its state, which then updates the UI to display the new message.

### Why Use Callback Functions in React?

- **Communication**: They allow child components to communicate with parent components, enabling a flow of data in both directions (parent to child via props, and child to parent via callbacks).
  
- **State Management**: Callback functions help in lifting state up to a common ancestor when multiple components need to share and update the same piece of state.

- **Modularity**: They promote modular and reusable code by separating concerns between components while still enabling interaction between them.


# What is hoisting in react js and how does it works?
## What is Hoisting?

**Hoisting** in JavaScript refers to the behavior where variable and function declarations are moved ("hoisted") to the top of their containing scope (either the function scope or global scope) during the compile phase, before the code is executed. This means that you can use variables and functions before they are declared in the code.

## How Hoisting Works in JavaScript

### 1. Function Declarations
Functions declared using the `function` keyword are fully hoisted. This means that you can call the function before it is actually defined in the code.

**Example:**

```javascript
sayHello();

function sayHello() {
  console.log("Hello, world!");
}
```

- This code works because the `sayHello` function is hoisted to the top of its scope.

### 2. Variable Declarations
- Variables declared using `var` are hoisted, but their initialization is not hoisted. This means the declaration is hoisted to the top, but the assignment remains in place.

**Example:**

```javascript
console.log(name); // undefined
var name = "John";
console.log(name); // "John"
```

- Here, the `var name;` declaration is hoisted, but the `name = "John";` assignment is not, so the first `console.log(name);` outputs `undefined`.

- Variables declared using `let` and `const` are also hoisted, but they are not initialized until the interpreter reaches their definition in the code. This results in a "temporal dead zone" (TDZ) where the variable exists but cannot be accessed.

**Example:**

```javascript
console.log(age); // ReferenceError: Cannot access 'age' before initialization
let age = 30;
```

## Hoisting in React JS

In the context of **React**, hoisting behaves the same way as it does in vanilla JavaScript because React is built on top of JavaScript. However, understanding hoisting is crucial for working with state, hooks, and functions in React.

### Example 1: Hoisting with Functional Components

In React, functional components are just JavaScript functions. Hoisting applies to them in the same way as it does to regular functions.

```javascript
function App() {
  return (
    <div>
      <Header />
      <Content />
    </div>
  );
}

function Header() {
  return <h1>Welcome to My Website</h1>;
}

function Content() {
  return <p>This is the content of the website.</p>;
}
```

- Here, both `Header` and `Content` components can be used before their declarations because they are hoisted.

### Example 2: Hoisting with Hooks

When working with hooks like `useState` or `useEffect`, the rules of hoisting can impact how and when these hooks are called.

```javascript
function App() {
  console.log(counter); // ReferenceError if you use let/const
  const [counter, setCounter] = useState(0);
}
```

- While the declaration of `counter` and `setCounter` would normally be hoisted, you must call hooks like `useState` at the top level of your component function, not conditionally or inside loops, to maintain the integrity of the hook's execution order.

## Key Takeaways
- **Function Declarations**: Can be called before they are defined due to hoisting.
- **`var` Declarations**: Are hoisted, but only the declaration, not the initialization.
- **`let` and `const` Declarations**: Are hoisted but result in a "temporal dead zone" where accessing the variable before initialization results in a `ReferenceError`.
- **React Specific**: Understanding hoisting helps avoid common pitfalls, such as using variables before they are initialized or calling hooks conditionally.

In React development, understanding hoisting is crucial for writing predictable and bug-free code, especially when dealing with variable scopes, function declarations, and the proper use of hooks.



2. How does it work?
3. What is the difference between let and var?
4. What is the Event Loop?
5. What is precedence in the Event Loop?
6. What is the difference between setTimeout and setInterval?
7. Where do you use the Rest Operator?
8. Have you heard of array.reverse?
9. What is meant by Shallow copy and Deep copy?
10. What are Closures?
11. Have you used the reduce function in JS?
12. What is the difference between map and reduce?
13. What parameters does the map function accept?
14. What is the difference between a Promise and a Callback?
15. What position attributes in CSS have you used?
16. What is the difference between them?
17. What is Flexbox?
18. What is the difference between display=none and visibility=hidden?
19. What Hooks have you used?
20. What is the purpose of useCallback?
21. What are Class-based Lifecycle methods?
22. How can you achieve componentDidMount, componentDidUpdate & componentDidUnMount in a functional-based component?
23. What are Pure Components and their purpose?
24. What are Higher Order components?
25. What HOCs have you used?
26. Have you used the Context API?
27. You already have state management in React, so why go for Redux?
28. How does Redux work?
29. Have you used any Middlewares?
30. What is the purpose of using middlewares?

# How to pass values from Child component to parent component


# New components in HTML5

# Postgred sql versioning

# ACID properties of Database

# SOLID Architecure

# React JS

# Next JS

# React Redux

# Formik

# React Query

# React Virtrualized

# React Spring

# React Testing Library

# TypeScript

# React Nativ



