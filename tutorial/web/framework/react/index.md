---
title: ReactJS
layout: default
parent: Framework
grand_parent: Web Development
description: "ReactJS"
---

# Getting Started with ReactJS

ReactJS is one of the most popular JavaScript libraries for building dynamic and interactive web applications. Created by Facebook, React lets you build components that make up the user interface, manage data and states, and re-render efficiently whenever the data changes. This tutorial will guide you through the basics of React, how to set up your environment, and create a simple app.

---

### What is React?

React is a *component-based library*, meaning it allows you to build the UI by creating reusable, independent components. Each component can manage its own state, allowing it to keep track of changing data and update itself when necessary. React handles these updates efficiently, making it a top choice for apps that require frequent user interaction and data changes.

### Key Concepts in React

1. **Components**  
   In React, everything is a component. Components are JavaScript functions or classes that return React elements—what you see on the screen. You can think of components as building blocks for your app, which can be reused and combined to create complex UIs.

2. **JSX (JavaScript XML)**  
   React uses a syntax extension called JSX, which allows you to write HTML-like code in JavaScript. With JSX, you can structure your component’s layout directly within the JavaScript code, making the code more readable and closer to HTML.

3. **Props**  
   Props (short for properties) allow data to be passed from one component to another. Components can receive data as props, making them dynamic and adaptable to different contexts.

4. **State**  
   State is a way to keep track of data that can change within a component. When a component’s state changes, React re-renders it, reflecting the updated data.

5. **Lifecycle Methods**  
   React components go through different stages in their “lifecycle” (creation, update, and deletion). There are specific functions, or *lifecycle methods*, you can use to control the component’s behavior at each stage. (These are more prominent in class components, though functional components with hooks can handle similar tasks.)

### Setting Up React

To get started with React, you’ll need Node.js installed on your system. You can use the popular tool Create React App to set up your project quickly.

1. **Install Node.js and npm (Node Package Manager)** if you haven’t already.
2. **Run the following command in your terminal** to create a new React app:

   ```bash
   npx create-react-app my-app
   ```

   This command creates a new React project named `my-app` with a basic structure.

3. **Navigate into your project directory and start the development server**:

   ```bash
   cd my-app
   npm start
   ```

   This will open your app in the browser at `http://localhost:3000`, and any changes you make to the code will automatically reload the page.

### Building Your First React Component

Let’s create a simple React component to understand the basics. In the `src` folder, open `App.js`. Replace its contents with the following code:

```jsx
import React from 'react';

function App() {
  return (
    <div>
      <h1>Hello, React!</h1>
      <p>Welcome to your first React component!</p>
    </div>
  );
}

export default App;
```

In this example:
- `App` is a *functional component* that returns JSX.
- The component outputs an `h1` and `p` element, which will be displayed on the screen when you run the app.

### Working with Props

To pass data to components, let’s create a `Greeting` component that takes a name as a prop.

1. **Create a new file** in the `src` folder named `Greeting.js`.
2. Add the following code:

   ```jsx
   import React from 'react';

   function Greeting(props) {
     return <h2>Hello, {props.name}!</h2>;
   }

   export default Greeting;
   ```

3. Now, **use this component** in `App.js` by importing it and passing a name as a prop:

   ```jsx
   import React from 'react';
   import Greeting from './Greeting';

   function App() {
     return (
       <div>
         <Greeting name="Alice" />
         <Greeting name="Bob" />
       </div>
     );
   }

   export default App;
   ```

When you run this code, you’ll see `Hello, Alice!` and `Hello, Bob!` on the screen. Here, `Greeting` is a reusable component that can display different greetings based on the `name` prop.

### Using State and Events

Let’s enhance the app by adding a button that counts the number of clicks. We’ll use *state* to keep track of the click count.

1. Modify the `App.js` file as follows:

   ```jsx
   import React, { useState } from 'react';

   function App() {
     const [count, setCount] = useState(0);

     function handleClick() {
       setCount(count + 1);
     }

     return (
       <div>
         <h1>Click Counter</h1>
         <p>You clicked {count} times</p>
         <button onClick={handleClick}>Click me</button>
       </div>
     );
   }

   export default App;
   ```

2. **Explanation**:
    - We use `useState` to create a piece of state called `count` and a function called `setCount` to update it.
    - The `handleClick` function increments the count by 1 whenever the button is clicked.
    - When the button is clicked, the `handleClick` function updates the `count`, and React re-renders the component to display the new count.

### Conclusion: Building Interactive UIs with React

ReactJS simplifies the process of building dynamic and interactive UIs by letting you work with components, props, state, and events. This basic example demonstrates the power of React’s component-based approach. With this foundation, you can explore more advanced features like routing, context, and hooks, allowing you to create sophisticated and high-performance applications.

React’s ecosystem is vast, so as you get comfortable with these basics, you’ll find a range of libraries and tools to help you build out any functionality you need.