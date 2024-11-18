---
title: Props in ReactJS
layout: default
parent: ReactJS
grand_parent: Framework
description: "Props in ReactJS"
---

# Props in React

**Table of Contents**
1. [Introduction](#introduction)
2. [What Are Props in React?](#what-are-props-in-react)
3. [How Props Work](#how-props-work)
4. [Passing Props to Components](#passing-props-to-components)
   - [Passing Basic Data](#1-passing-basic-data)
   - [Passing Functions as Props](#2-passing-functions-as-props)
   - [Passing Objects as Props](#3-passing-objects-as-props)
5. [Props vs State](#props-vs-state)
6. [Default Props](#default-props)
7. [Prop Validation with PropTypes](#prop-validation-with-proptypes)
8. [Conclusion](#conclusion)

---

## Introduction
Props, short for "properties," are a core concept in React that enable components to be dynamic and reusable. Props allow you to pass data from a parent component to its child components, making your application modular and maintainable.

---

## What Are Props in React?
Props are read-only inputs passed to a component. They are immutable and are primarily used for rendering dynamic content or controlling a child component's behavior. Think of props as arguments passed to a function, but in this case, the function is a React component.

---

## How Props Work
1. Props are passed from a parent component to a child component.
2. A child component can access props using the `props` object or destructuring.
3. Props are immutable, meaning a child component cannot modify them.

---

## Passing Props to Components

### 1. Passing Basic Data
You can pass strings, numbers, or boolean values as props:

**Example:**
```javascript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="John" />;
}
```

---

### 2. Passing Functions as Props
You can pass functions to child components to handle events or share logic:

**Example:**
```javascript
function Button({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}

function App() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return <Button onClick={handleClick} />;
}
```

---

### 3. Passing Objects as Props
Instead of passing multiple props, you can bundle them into an object and pass that object as a single prop:

**Example:**
```javascript
function UserProfile({ user }) {
  return (
    <div>
      <h2>{user.name}</h2>
      <p>Age: {user.age}</p>
    </div>
  );
}

function App() {
  const user = { name: 'Jane Doe', age: 28 };
  return <UserProfile user={user} />;
}
```

---

## Props vs State
| **Props**             | **State**              |  
|------------------------|------------------------|  
| Passed from parent to child | Managed locally within a component |  
| Immutable             | Mutable               |  
| Used for component communication | Used for dynamic, interactive data |  

---

## Default Props
Default props allow you to set default values for props that are not passed by the parent component.

**Example:**
```javascript
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

Greeting.defaultProps = {
  name: 'Guest',
};
```

---

## Prop Validation with PropTypes
React provides a library called `prop-types` to validate the types of props passed to components.

**Installation:**
```bash
npm install prop-types
```

**Example:**
```javascript
import PropTypes from 'prop-types';

function Greeting({ name, age }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Age: {age}</p>
    </div>
  );
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};
```

---

## Conclusion
Props are a vital part of React, allowing you to build flexible and reusable components. By passing data, functions, or objects to child components, you can create dynamic UIs while maintaining a clean and modular structure.

Understanding how to use props effectively is a fundamental skill for any React developer. Start experimenting with props in your projects to see how they can enhance your applications!