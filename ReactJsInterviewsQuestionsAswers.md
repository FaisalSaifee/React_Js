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


# New components in HTML5

# Postgred sql versioning

# ACID properties of Database
