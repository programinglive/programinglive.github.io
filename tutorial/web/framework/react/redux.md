---
title: Redux
layout: default
parent: ReactJS
grand_parent: Framework
description: "Redux"
---

# Redux

**Table of Contents**
1. [Introduction](#introduction)
2. [What is Redux?](#what-is-redux)
3. [Why Use Redux?](#why-use-redux)
4. [Core Concepts of Redux](#core-concepts-of-redux)
   - [Store](#1-store)
   - [Actions](#2-actions)
   - [Reducers](#3-reducers)
5. [Setting Up Redux](#setting-up-redux)
6. [Redux Workflow Example](#redux-workflow-example)
7. [Redux Toolkit: Simplifying Redux](#redux-toolkit-simplifying-redux)
8. [When to Use Redux?](#when-to-use-redux)
9. [Conclusion](#conclusion)

---

## Introduction
State management in React applications can become challenging as your app grows. Redux is a predictable state management library that helps manage application state efficiently, making complex apps easier to debug and maintain.

---

## What is Redux?
Redux is a JavaScript library designed to manage the state of an application in a predictable manner. Although commonly used with React, Redux can work with any JavaScript framework or library.

Redux centralizes the state into a single "store," which serves as the source of truth for the entire application.

---

## Why Use Redux?
1. **Centralized State Management:** Redux keeps all your application state in one place, making it easier to manage and debug.
2. **Predictable State Changes:** With strict rules about how state changes (via pure functions called reducers), your application behavior becomes more predictable.
3. **Debugging Tools:** Tools like Redux DevTools make tracking state changes and debugging straightforward.
4. **Scalability:** Redux excels in large applications with complex state interactions.

---

## Core Concepts of Redux

### 1. Store
The store is a single JavaScript object that holds the application state.

**Example:**
```javascript
import { createStore } from 'redux';

const store = createStore(reducer);
```

---

### 2. Actions
Actions are plain JavaScript objects that describe what you want to do. They must have a `type` property and optionally include additional data (payload).

**Example:**
```javascript
const increment = {
  type: 'INCREMENT',
  payload: 1,
};
```

---

### 3. Reducers
Reducers are pure functions that determine how the state changes in response to actions.

**Example:**
```javascript
const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + action.payload };
    case 'DECREMENT':
      return { count: state.count - action.payload };
    default:
      return state;
  }
}
```

---

## Setting Up Redux
Follow these steps to add Redux to your React application:

1. **Install Redux and React-Redux:**
   ```bash
   npm install redux react-redux
   ```

2. **Create the Store:**
   ```javascript
   import { createStore } from 'redux';
   import reducer from './reducer';

   const store = createStore(reducer);
   ```

3. **Provide the Store to Your App:**  
   Use the `Provider` component from `react-redux` to make the store accessible to your components.
   ```javascript
   import { Provider } from 'react-redux';
   import store from './store';

   function App() {
     return (
       <Provider store={store}>
         <MyComponent />
       </Provider>
     );
   }
   ```

4. **Connect Components to the Store:**  
   Use the `useSelector` and `useDispatch` hooks to access state and dispatch actions.

---

## Redux Workflow Example
Here’s a basic example of a counter app using Redux:

1. **Actions:**
   ```javascript
   const increment = { type: 'INCREMENT', payload: 1 };
   const decrement = { type: 'DECREMENT', payload: 1 };
   ```

2. **Reducer:**
   ```javascript
   const initialState = { count: 0 };

   function counterReducer(state = initialState, action) {
     switch (action.type) {
       case 'INCREMENT':
         return { count: state.count + action.payload };
       case 'DECREMENT':
         return { count: state.count - action.payload };
       default:
         return state;
     }
   }
   ```

3. **Store:**
   ```javascript
   import { createStore } from 'redux';

   const store = createStore(counterReducer);
   ```

4. **Component:**
   ```javascript
   import React from 'react';
   import { useSelector, useDispatch } from 'react-redux';

   function Counter() {
     const count = useSelector(state => state.count);
     const dispatch = useDispatch();

     return (
       <div>
         <h1>{count}</h1>
         <button onClick={() => dispatch({ type: 'INCREMENT', payload: 1 })}>
           Increment
         </button>
         <button onClick={() => dispatch({ type: 'DECREMENT', payload: 1 })}>
           Decrement
         </button>
       </div>
     );
   }

   export default Counter;
   ```

---

## Redux Toolkit: Simplifying Redux
Redux Toolkit (RTK) is the official, recommended way to use Redux. It simplifies Redux development by abstracting boilerplate code and providing utilities like `configureStore` and `createSlice`.

**Installation:**
```bash
npm install @reduxjs/toolkit
```

**Example:**
```javascript
import { createSlice, configureStore } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: state => { state.count += 1; },
    decrement: state => { state.count -= 1; },
  },
});

export const { increment, decrement } = counterSlice.actions;

const store = configureStore({ reducer: counterSlice.reducer });
```

---

## When to Use Redux?
Use Redux if your application:
- Has complex state interactions.
- Shares state across many components.
- Requires consistent and predictable state updates.
- Benefits from tools like time-travel debugging (Redux DevTools).

For simpler state management needs, React Context or local state might suffice.

---

## Conclusion
Redux is a powerful state management library that excels in handling complex state scenarios. While it introduces some learning curve and boilerplate, tools like Redux Toolkit streamline the process, making Redux accessible and efficient.

Mastering Redux equips you with the skills to build scalable and maintainable applications, especially as your projects grow in size and complexity. Dive in, experiment, and discover the full potential of Redux in your React journey!  