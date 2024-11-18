---
title: What is Component in ReactJS
layout: default
parent: ReactJS
grand_parent: Framework
description: "What is Component in ReactJS"
---

# React Components

**Table of Contents**
1. [Introduction](#introduction)
2. [What is a Component?](#what-is-a-component)
3. [Types of React Components](#types-of-react-components)
    - [Functional Components](#1-functional-components)
    - [Class Components](#2-class-components)
4. [Key Features of React Components](#key-features-of-react-components)
5. [Creating Components](#creating-components)
    - [Stateless Components](#1-stateless-components)
    - [Stateful Components](#2-stateful-components)
6. [Component Composition](#component-composition)
7. [Props in Components](#props-in-components)
8. [Lifecycle of Class Components](#lifecycle-of-class-components)
9. [Conclusion](#conclusion)

---

## Introduction
Components are at the core of React’s architecture. They enable you to divide the user interface into smaller, reusable pieces, each focusing on a specific functionality or behavior. This modular approach simplifies development and enhances maintainability.

---

## What is a Component?
A component in React is a self-contained piece of UI. It can render content, accept input (via **props**), and manage its own state. Components are reusable and can be combined to build complex interfaces.

**Example:**
```javascript
function Greeting() {
  return <h1>Hello, World!</h1>;
}
```

---

## Types of React Components

### 1. Functional Components
Functional components are simple JavaScript functions that return JSX. They are lightweight, easier to read, and can now manage state and lifecycle events with hooks.

**Example:**
```javascript
function Welcome(props) {
  return <h1>Welcome, {props.name}!</h1>;
}
```

---

### 2. Class Components
Class components are ES6 classes that extend `React.Component`. They include a render method and can manage state and lifecycle events without hooks.

**Example:**
```javascript
import React, { Component } from 'react';

class Welcome extends Component {
  render() {
    return <h1>Welcome, {this.props.name}!</h1>;
  }
}
```

---

## Key Features of React Components
1. **Reusable:** Write once and use across multiple parts of your app.
2. **Composable:** Combine smaller components to build complex UIs.
3. **Dynamic:** React components can accept data (props) and manage state for dynamic rendering.

---

## Creating Components

### 1. Stateless Components
Stateless components do not manage their own state. They focus on rendering content based on props.

**Example:**
```javascript
function User(props) {
  return <p>User: {props.name}</p>;
}
```

---

### 2. Stateful Components
Stateful components manage their own state using either class component state or the `useState` hook in functional components.

**Example:**
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

## Component Composition
Composition is the process of combining multiple components to build a complete UI.

**Example:**
```javascript
function Header() {
  return <h1>Header Section</h1>;
}

function Footer() {
  return <footer>Footer Section</footer>;
}

function App() {
  return (
    <div>
      <Header />
      <p>Welcome to the App!</p>
      <Footer />
    </div>
  );
}
```

---

## Props in Components
Props are inputs passed to a component to make it dynamic and reusable. Learn more about [props here](#props-in-react).

**Example:**
```javascript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

---

## Lifecycle of Class Components
Class components have lifecycle methods that allow you to hook into different stages of a component’s lifecycle.

### Common Lifecycle Methods:
1. **Mounting:** `componentDidMount` (when a component is added to the DOM).
2. **Updating:** `componentDidUpdate` (when props or state changes).
3. **Unmounting:** `componentWillUnmount` (when a component is removed from the DOM).

**Example:**
```javascript
import React, { Component } from 'react';

class Timer extends Component {
  componentDidMount() {
    console.log('Timer mounted!');
  }

  componentWillUnmount() {
    console.log('Timer unmounted!');
  }

  render() {
    return <p>Timer Component</p>;
  }
}
```

---

## Conclusion
React components are the building blocks of modern web applications. They make it easy to divide your UI into manageable, reusable pieces, enhancing your app’s scalability and maintainability. Whether you're working with functional or class components, mastering their usage is a critical step in your React development journey.

Explore the power of components and create seamless, dynamic user interfaces!  