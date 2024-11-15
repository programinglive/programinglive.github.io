---
title: What is Component in ReactJS
layout: default
parent: ReactJS
grand_parent: Framework
description: "What is Component in ReactJS"
---

# What is a Component in ReactJS?

In ReactJS, a **component** is a building block of the user interface (UI) that allows you to break down the UI into reusable, self-contained pieces. Each component is responsible for rendering a part of the UI and managing its state and logic. React components can be thought of as custom HTML elements that provide a way to organize and structure complex UIs.

---

## Types of Components in React

React components can be classified into two main types:

1. **Functional Components**
2. **Class Components**

### 1. Functional Components

Functional components are JavaScript functions that accept **props** (inputs) and return JSX (JavaScript XML), which describes what the UI should look like. These are simpler, and since React introduced **hooks** in version 16.8, functional components can also manage state and side effects.

**Example of a Functional Component:**
```javascript
import React from 'react';

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;
```

In this example, the `Greeting` component receives a `name` prop and renders a greeting message.

### 2. Class Components

Class components are ES6 class-based components that extend from `React.Component`. They can hold **state** and have lifecycle methods, making them more suitable for handling complex logic. However, they are now less common in modern React code since functional components with hooks have become the preferred approach.

**Example of a Class Component:**
```javascript
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Greeting;
```

In this class component, the `Greeting` component receives a `name` prop and renders a greeting message just like the functional version.

---

## Key Concepts Related to Components

1. **JSX (JavaScript XML)**
    - JSX is a syntax extension for JavaScript that looks similar to HTML. It allows you to write elements and components in a way that closely resembles HTML, but under the hood, JSX is transformed into JavaScript.

   **Example:**
   ```javascript
   const element = <h1>Hello, world!</h1>;
   ```

2. **Props (Properties)**
    - **Props** are inputs to components. They are passed from parent components to child components, allowing components to be dynamic and reusable. Props are **read-only** and cannot be modified by the component receiving them.

   **Example:**
   ```javascript
   function Welcome(props) {
     return <h1>Welcome, {props.name}!</h1>;
   }
   ```

3. **State**
    - **State** is data that is managed within a component and can change over time. Unlike props, which are passed down from a parent, state is internal to a component and can be modified using functions like `setState` in class components or the `useState` hook in functional components.

   **Example (Functional Component with State):**
   ```javascript
   import React, { useState } from 'react';

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

4. **Event Handling**
    - React provides event handling mechanisms to respond to user actions like clicks, form submissions, or key presses. Events in React are handled via **synthetic events**, which normalize native events across browsers.

   **Example:**
   ```javascript
   function Button() {
     function handleClick() {
       alert('Button clicked!');
     }

     return <button onClick={handleClick}>Click Me</button>;
   }
   ```

---

## Lifecycle of a React Component

Components in React have a lifecycle, which refers to the different stages of a component's existence. These stages include mounting, updating, and unmounting, and they provide lifecycle methods (in class components) or hooks (in functional components) to run code at specific points in the lifecycle.

- **Mounting**: The process of creating and inserting a component into the DOM.
    - **Class Component Lifecycle Methods**: `componentDidMount`, `getDerivedStateFromProps`
    - **Functional Component Hook**: `useEffect` (when an empty dependency array `[]` is provided, it acts like `componentDidMount`)

- **Updating**: Occurs when the component's state or props change.
    - **Class Component Lifecycle Methods**: `shouldComponentUpdate`, `getSnapshotBeforeUpdate`
    - **Functional Component Hook**: `useEffect` (with dependencies)

- **Unmounting**: When a component is removed from the DOM.
    - **Class Component Lifecycle Method**: `componentWillUnmount`
    - **Functional Component Hook**: `useEffect` (with a cleanup function)

---

## Reusability and Composition of Components

One of the core benefits of using components in React is **reusability**. You can create a component once and reuse it multiple times with different props to render different content.

Components can also be **composed**. This means you can build complex UIs by combining simpler components together. This approach promotes modularity and makes the codebase easier to maintain.

**Example:**
```javascript
function App() {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Jane" />
    </div>
  );
}
```
In this example, the `Greeting` component is reused twice with different props.

---

## Advantages of Using Components in React

1. **Modularity**  
   Components allow you to break down a large application into smaller, manageable pieces. Each component handles a specific part of the UI, making the codebase easier to understand and maintain.

2. **Reusability**  
   Once a component is created, it can be reused throughout your application, leading to a more DRY (Don't Repeat Yourself) codebase.

3. **Separation of Concerns**  
   Components help you separate concerns by isolating specific logic (e.g., handling state or events) within individual units, making the application more organized.

4. **Declarative UI**  
   Components enable you to describe how the UI should look for different states. React takes care of the updating process, making the UI more predictable and easier to manage.

---

### Conclusion

In ReactJS, components are the fundamental units of building a UI. By breaking down the UI into small, reusable pieces, components provide a powerful and modular way to develop and manage large applications. With features like **props**, **state**, and **lifecycle methods**, React components can be easily customized and manipulated to create dynamic user interfaces that are efficient and maintainable. Whether using functional or class components, React’s component-based architecture is key to building scalable and maintainable applications.