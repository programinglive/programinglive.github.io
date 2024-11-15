---
title: Props in ReactJS
layout: default
parent: ReactJS
grand_parent: Framework
description: "Props in ReactJS"
---

# What are Props in React?

**Props** (short for *properties*) are a fundamental concept in React that allow data to be passed from a parent component to a child component. They are immutable, meaning the child component receiving props cannot modify them. Props enable the creation of dynamic and reusable components by allowing components to render based on data or settings provided by their parent.

---

## Key Characteristics of Props

1. **Read-Only**  
   Props are immutable, meaning once a parent passes them to a child, the child cannot change their value. This ensures a unidirectional data flow from parent to child.

2. **Used for Customization**  
   Props allow components to be configured with different data or behaviors, making components more reusable.

3. **Passed as Attributes**  
   Props are passed to components similarly to HTML attributes.

   **Example:**
   ```jsx
   <Button color="blue" label="Click Me" />
   ```

4. **Accessible via `props` Object**  
   In the receiving component, props can be accessed via the `props` object in class components or directly in function components.

---

## How to Use Props

1. **Passing Props**  
   In the parent component, you pass props by adding attributes to the child component.

   ```jsx
   function App() {
     return (
       <Greeting name="Alice" />
     );
   }
   ```

2. **Receiving Props**  
   In the child component, props can be accessed as a parameter (in functional components) or through `this.props` (in class components).

   **Functional Component Example:**
   ```jsx
   function Greeting(props) {
     return <h1>Hello, {props.name}!</h1>;
   }
   ```

   **Class Component Example:**
   ```jsx
   class Greeting extends React.Component {
     render() {
       return <h1>Hello, {this.props.name}!</h1>;
     }
   }
   ```

---

## Props vs. State

While both **props** and **state** hold information to control a component’s behavior, they serve different purposes:

| **Aspect**       | **Props**                                | **State**                              |
|-------------------|------------------------------------------|----------------------------------------|
| **Definition**    | Passed from parent to child components   | Internal to a component                |
| **Mutability**    | Immutable                               | Mutable                                |
| **Usage**         | Configure a component                   | Manage a component's internal data     |
| **Control**       | Controlled by parent components          | Controlled by the component itself     |

---

## Default Props

React allows you to define default props for components in case no value is provided by the parent.

**Example:**
```jsx
function Button({ label = "Default Label" }) {
  return <button>{label}</button>;
}

// OR using defaultProps:
Button.defaultProps = {
  label: "Default Label",
};
```

---

## Prop Types

Prop validation is essential for ensuring that components receive the correct data types. React provides the `prop-types` package to define and validate the types of props.

**Example:**
```jsx
import PropTypes from 'prop-types';

function Greeting({ name, age }) {
  return <h1>Hello, {name}! You are {age} years old.</h1>;
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};
```

---

## Passing Functions as Props

Props can also be used to pass functions from a parent component to a child. This is often used for handling events or managing shared state.

**Example:**
```jsx
function Parent() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return <Child onClick={handleClick} />;
}

function Child({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}
```

---

## Best Practices for Props

1. **Keep Components Pure**  
   Avoid modifying props within a child component. Use props as inputs to render output.

2. **Use PropTypes for Validation**  
   Validate prop types to catch errors and improve code reliability.

3. **Name Props Clearly**  
   Use descriptive names for props to make components easier to understand.

4. **Deconstruct Props**  
   Deconstruct props for cleaner code:
   ```jsx
   function Greeting({ name }) {
     return <h1>Hello, {name}!</h1>;
   }
   ```

---

## Conclusion

Props are a powerful tool in React that enable components to be dynamic, reusable, and easy to maintain. By passing data from parent to child components, they establish a clear, one-way data flow that aligns with React's design principles. Mastering props is essential for creating flexible and maintainable React applications.