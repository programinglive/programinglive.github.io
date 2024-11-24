---
title: Let vs Var
layout: default
parent: JavaScript
grand_parent: Web Development
description: "Let vs Var"
---

# Let vs Var in JavaScript

In JavaScript, `let` and `var` are both used to declare variables, but they behave differently in terms of scope,
hoisting, and reassignability. Understanding the differences between them is important to write more efficient and
error-free JavaScript code.

---

## Table of Contents

- [What is `var`?](#what-is-var)
- [What is `let`?](#what-is-let)
- [Key Differences Between `let` and `var`](#key-differences-between-let-and-var)
- [When to Use `let` and When to Use `var`](#when-to-use-let-and-when-to-use-var)
- [Conclusion](#conclusion)

---

## What is `var`?

`var` is the traditional way of declaring variables in JavaScript. It was introduced in ECMAScript 5 and earlier
versions. While it is still widely used, there are some quirks that have been improved upon in later versions of
JavaScript (ES6 and beyond).

### Characteristics of `var`:

1. **Function Scope**: Variables declared with `var` are scoped to the nearest function block. If declared outside any
   function, they are globally scoped.
2. **Hoisting**: Variables declared with `var` are "hoisted," meaning their declarations are moved to the top of their
   scope, but the values are not assigned until the line of declaration is reached.

Example of hoisting:

```javascript
console.log(a); // undefined
var a = 10;
console.log(a); // 10
```  

---

## What is `let`?

`let` was introduced in ECMAScript 6 (ES6) and provides a more predictable and reliable way of declaring variables
compared to `var`.

### Characteristics of `let`:

1. **Block Scope**: Variables declared with `let` are scoped to the nearest block (like loops or conditionals), not just
   functions.
2. **Hoisting**: Like `var`, `let` is hoisted, but it does not initialize the variable until the declaration is
   encountered in the code. This leads to a behavior known as the **temporal dead zone**, where accessing the variable
   before its declaration results in a reference error.

Example of block scope:

```javascript
if (true) {
	let b = 20;
	console.log(b); // 20
}
console.log(b); // ReferenceError: b is not defined
```  

---

## Key Differences Between `let` and `var`

| Feature            | `var`                                                                                   | `let`                                                                             |  
|--------------------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
| **Scope**          | Function scope                                                                          | Block scope                                                                       |  
| **Hoisting**       | Hoisted to the top but initialized to `undefined`                                       | Hoisted but not initialized until declaration is encountered (Temporal Dead Zone) |  
| **Re-declaration** | Can be re-declared in the same scope                                                    | Cannot be re-declared in the same scope                                           |  
| **Global Object**  | If declared globally, it becomes a property of the global object (`window` in browsers) | If declared globally, it does not become a property of the global object          |  

---

## When to Use `let` and When to Use `var`

- **Use `let`**:
    - When you need a variable to be scoped to a block, such as in loops, conditionals, or functions.
    - To prevent re-declaration of the same variable in the same scope.
    - For a cleaner and more predictable behavior in modern JavaScript.

- **Avoid `var`**:
    - `var` is considered outdated due to its function-scoped behavior, hoisting issues, and potential for bugs. It is
      better to use `let` or `const` (if the variable value won't change) to ensure more predictable and less
      error-prone code.

---

## Conclusion

In modern JavaScript development, `let` is generally preferred over `var` because it offers better scoping, avoids
hoisting issues, and is more predictable. Use `let` when you need to declare variables in blocks or loops, and
save `const` for variables whose values will not change. By understanding the differences between `let` and `var`, you
can write more reliable and maintainable code.