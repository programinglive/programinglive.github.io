---
title: State in ReactJS
layout: default
parent: ReactJS
grand_parent: Framework
description: "State in ReactJS"
---

# State in React

**Table of Contents**
1. [Introduction](#introduction)
2. [What is State in React?](#what-is-state-in-react)
3. [Why is State Important?](#why-is-state-important)
4. [Types of State in React](#types-of-state-in-react)
5. [How to Use State in React](#how-to-use-state-in-react)
   - [Using State in Class Components](#1-using-state-in-class-components)
   - [Using State in Functional Components (Hooks)](#2-using-state-in-functional-components-hooks)
6. [Common Use Cases of State](#common-use-cases-of-state)
7. [Best Practices for Managing State](#best-practices-for-managing-state)
8. [Conclusion](#conclusion)

---

## Introduction
State is one of the most crucial concepts in React, enabling components to create dynamic and interactive user interfaces. It represents the "memory" of a component, holding information that can change over time, such as user input, fetched data, or the current UI state.

This guide will walk you through the fundamentals of state in React, how it works, and best practices for managing it effectively.

---

## What is State in React?
State in React refers to an object that stores dynamic data for a component and determines its behavior and rendering. Unlike props, which are immutable and passed from parent to child, the state is mutable and managed internally by the component itself.

---

## Why is State Important?
State enables React components to:
1. **Track Changes:** For example, updating the UI in response to user actions like clicking a button or submitting a form.
2. **Control Behavior:** State can dictate whether a modal is visible, a button is disabled, or which tab is active.
3. **Handle Asynchronous Updates:** It manages data fetched from APIs and ensures components re-render when the data changes.

---

## Types of State in React

React state can be categorized into four types:
1. **Local State:** Managed within a single component (e.g., form inputs).
2. **Global State:** Shared across multiple components (e.g., user authentication).
3. **Server State:** Synchronized with an external server (e.g., API data).
4. **URL State:** Synced with the browser's URL (e.g., query parameters or route information).

---

## How to Use State in React

### 1. Using State in Class Components
In class components, state is defined as an object and managed using the `this.setState` method.

#### Example:
```javascript
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>{this.state.count}</h1>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```

### 2. Using State in Functional Components (Hooks)
With the introduction of React Hooks in version 16.8, state can now be used in functional components via the `useState` hook.

#### Example:
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;
```

---

## Common Use Cases of State

1. **Form Handling:** Storing and updating user inputs.
2. **Toggling UI Elements:** Managing modal visibility or dropdown states.
3. **Fetching Data:** Updating UI based on API responses.
4. **Conditional Rendering:** Showing or hiding components based on specific conditions.

---

## Best Practices for Managing State

1. **Keep State Local When Possible:** Avoid over-complicating by lifting state unnecessarily.
2. **Use State Management Libraries When Needed:** For complex apps, tools like Redux, MobX, or React Context can help manage global state.
3. **Avoid Direct State Mutation:** Always use `setState` or the state updater function.
4. **Batch State Updates:** When updating state based on the previous value, always use a function inside `setState` or `setCount`.
   ```javascript
   setCount(prevCount => prevCount + 1);
   ```  
5. **Optimize Renders:** Use `React.memo` or `useCallback` to prevent unnecessary re-renders.

---

## Conclusion
State is fundamental to building dynamic and interactive React applications. Whether you're working with class components or functional components, understanding how to properly manage state can significantly improve your development workflow and application performance.

With a solid grasp of React state, you’re well on your way to building robust and engaging user interfaces.  