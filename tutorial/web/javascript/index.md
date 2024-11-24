---
title: JavaScript
layout: default
parent: Web Development
nav_order: 3
description: "JavaScript Tutorial"
---

# JavaScript

JavaScript is a versatile programming language used to make web pages interactive and dynamic. It’s an essential skill
for any web developer and forms the core of modern web applications.

---

## Table of Contents

- [What is JavaScript?](#what-is-javascript)
- [How JavaScript Works in the Browser](#how-javascript-works-in-the-browser)
- [Basic Syntax](#basic-syntax)
    - [Variables and Constants](#variables-and-constants)
    - [Data Types](#data-types)
    - [Operators](#operators)
- [Control Flow](#control-flow)
    - [Conditional Statements](#conditional-statements)
    - [Loops](#loops)
- [Functions in JavaScript](#functions-in-javascript)
    - [Function Declarations](#function-declarations)
    - [Arrow Functions](#arrow-functions)
- [DOM Manipulation](#dom-manipulation)
- [Conclusion](#conclusion)

---

## What is JavaScript?

JavaScript is a high-level, interpreted scripting language primarily used for creating interactive web pages. It can:

- Add dynamic content to web pages (e.g., animations, forms).
- Respond to user events (e.g., clicks, hover).
- Communicate with servers using APIs.

---

## How JavaScript Works in the Browser

JavaScript runs in the browser's **JavaScript engine**. It interacts with the Document Object Model (DOM), which
represents the structure of a web page, allowing developers to dynamically update content and styles.

Example: Changing text dynamically:

```html
<p id="demo">Hello, World!</p>
<script>
    document.getElementById("demo").textContent = "Hello, JavaScript!";
</script>
```  

---

## Basic Syntax

### Variables and Constants

Variables store data that can be updated, while constants hold data that cannot be changed.

```javascript
let age = 25; // A variable that can change
const pi = 3.14; // A constant value
```  

### Data Types

JavaScript has different types of data:

- **String**: Text (`"Hello"`).
- **Number**: Numeric values (`42`).
- **Boolean**: True or false (`true`).
- **Array**: A collection of values (`[1, 2, 3]`).
- **Object**: Key-value pairs (`{name: "John", age: 25}`).

### Operators

Perform operations like addition or comparison:

```javascript
let sum = 10 + 20; // 30
let isEqual = (sum === 30); // true
```  

---

## Control Flow

### Conditional Statements

Run code based on conditions:

```javascript
let age = 18;
if (age >= 18) {
	console.log("You are an adult.");
} else {
	console.log("You are a minor.");
}
```  

### Loops

Repeat code multiple times:

```javascript
for (let i = 0; i < 5; i++) {
	console.log(i);
}
```  

---

## Functions in JavaScript

### Function Declarations

Reusable blocks of code:

```javascript
function greet(name) {
	return `Hello, ${name}!`;
}

console.log(greet("Alice"));
```  

### Arrow Functions

A concise way to write functions:

```javascript
const greet = (name) => `Hello, ${name}!`;
console.log(greet("Bob"));
```  

---

## DOM Manipulation

The DOM allows you to interact with HTML elements programmatically.

- **Selecting Elements**:

```javascript
let element = document.querySelector(".className");
```  

- **Changing Content**:

```javascript
element.textContent = "Updated Text";
```  

- **Adding Event Listeners**:

```javascript
element.addEventListener("click", () => {
	alert("Element clicked!");
});
```  

Example: Changing a button's text on click:

```html

<button id="myButton">Click Me</button>
<script>
    document.getElementById("myButton").addEventListener("click", function () {
        this.textContent = "Clicked!";
    });
</script>
```  

---

## Conclusion

JavaScript is a vital skill for building interactive and dynamic web applications. From manipulating the DOM to
implementing complex logic, it gives developers the tools to create engaging user experiences.

Start experimenting with JavaScript today, and you'll unlock the full potential of web development!