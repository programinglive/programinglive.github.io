---
title: Let vs Var
layout: default
parent: JavaScript
grand_parent: Web Development
description: "Let vs Var"
---

# Let vs Var in JavaScript

In JavaScript, variables are fundamental to writing dynamic code. They allow developers to store, modify, and use data across an application. Until ES6 (ECMAScript 2015), JavaScript only had the `var` keyword for declaring variables. However, ES6 introduced `let` and `const`, providing developers with more flexible and safer ways to handle variables. This article explores the differences between `let` and `var`, why `let` is generally preferred, and when to use each.

## Introduction to `let` and `var`

Both `let` and `var` are used to declare variables, but they differ in several ways, including scope, hoisting, and reassignment rules. Understanding these differences is essential for writing clean, bug-free JavaScript code.

### Example

To see the basics, here’s how `let` and `var` declarations work:

```javascript
var x = 10;
let y = 20;

console.log(x); // 10
console.log(y); // 20
```

This looks straightforward, but the real distinctions appear in more complex scenarios.

---

## Key Differences Between `let` and `var`

### 1. Scope

Scope determines where a variable is accessible in code.

- **`var`** is **function-scoped**, meaning it’s confined to the function in which it’s declared. If declared outside a function, it becomes globally accessible.
- **`let`** is **block-scoped**, meaning it’s only accessible within the block `{ }` where it was declared, such as within an `if` statement or a `for` loop.

#### Example of Scope Difference

```javascript
function scopeTest() {
  if (true) {
    var a = "var variable";
    let b = "let variable";
  }
  console.log(a); // Accessible: "var variable"
  console.log(b); // Error: b is not defined
}
scopeTest();
```

In this example, the `var` variable `a` is accessible outside the `if` block because it’s function-scoped, while the `let` variable `b` is not, since it’s block-scoped.

### 2. Hoisting

**Hoisting** refers to JavaScript’s behavior of moving variable and function declarations to the top of their scope before code execution.

- **`var`** is hoisted to the top of its scope and initialized with `undefined`. This can lead to unexpected results if not handled carefully.
- **`let`** is hoisted as well, but it’s not initialized. It remains in a "temporal dead zone" until its actual declaration is encountered, which prevents access to it before initialization.

#### Example of Hoisting Difference

```javascript
console.log(varVariable); // undefined
var varVariable = "I'm a var variable";

console.log(letVariable); // Error: Cannot access 'letVariable' before initialization
let letVariable = "I'm a let variable";
```

Here, `varVariable` logs `undefined` because `var` is hoisted and initialized as `undefined`. However, accessing `letVariable` before its declaration results in an error, as `let` is not initialized during hoisting.

### 3. Re-declaration

- **`var`** allows re-declaring the same variable within the same scope without error, which can lead to bugs due to unintentional re-declarations.
- **`let`** doesn’t allow re-declaration within the same scope, which enforces more predictable code.

#### Example of Re-declaration

```javascript
var reDeclare = "First declaration";
var reDeclare = "Re-declared with var"; // No error
console.log(reDeclare); // "Re-declared with var"

let uniqueDeclare = "First declaration";
let uniqueDeclare = "Attempt to re-declare"; // Error: Identifier 'uniqueDeclare' has already been declared
```

Using `let` here prevents accidental re-declaration, making code more robust and helping avoid bugs.

### 4. Global Object Binding

In the global scope (outside any function or block), `var` declarations become properties of the global `window` object (in browsers), whereas `let` declarations do not.

#### Example of Global Object Binding

```javascript
var globalVar = "I’m a var";
let globalLet = "I’m a let";

console.log(window.globalVar); // "I’m a var"
console.log(window.globalLet); // undefined
```

Since `globalVar` is bound to `window`, it can be accessed as a property of the global object. `globalLet`, on the other hand, does not become a property of the global object, reducing the risk of conflicts.

---

## When to Use `let` and `var`

In modern JavaScript, `let` is generally preferred due to its block scope, non-redeclaration behavior, and avoidance of hoisting-related issues. However, there are a few considerations:

- **Use `let`** when you expect the variable’s value to change or when block scoping is needed.
- **Use `var`** if you’re working with legacy code or specific cases that rely on function scoping. In new code, however, `var` is largely considered obsolete in favor of `let` and `const`.

---

## Summary of `let` vs `var`

Here’s a quick comparison to summarize the main differences:

| Feature              | `var`                            | `let`                        |
|----------------------|----------------------------------|------------------------------|
| **Scope**            | Function-scoped                 | Block-scoped                 |
| **Hoisting**         | Hoisted with `undefined`        | Hoisted, but not initialized |
| **Re-declaration**   | Allowed within the same scope   | Not allowed in the same scope |
| **Global Object**    | Binds to the global object      | Does not bind to global object |

---

## Best Practices

1. **Use `let` over `var`** in most cases, as it provides more predictable scoping and reduces the chances of accidental re-declaration and hoisting issues.
2. **Consider `const`** when you know the value of a variable won’t change, as it signals that a variable’s reference is fixed (although the value itself may still be mutable if it’s an object).
3. Avoid `var` in modern JavaScript, except for backward compatibility.

## Conclusion

The `let` and `var` keywords offer different scoping, hoisting, and reassignment behaviors. While `var` was sufficient for early JavaScript, `let` (and `const`) provide safer, more intuitive options for modern JavaScript programming. By understanding these differences and following best practices, you can write cleaner, more reliable code that avoids common pitfalls.