---
title: What is a Media Query?
layout: default
parent: CSS
grand_parent: Web Development
description: "What is a Media Query?"
---

# What is Media Query?

Media queries are a fundamental feature of CSS that enable you to apply specific styles based on the characteristics of
the user’s device or browser. They are crucial for building responsive and adaptive web designs.

---

## Table of Contents

- [Definition and Purpose](#definition-and-purpose)
- [Basic Syntax of Media Queries](#basic-syntax-of-media-queries)
- [Using Media Queries in CSS](#using-media-queries-in-css)
    - [Targeting Screen Sizes](#targeting-screen-sizes)
    - [Targeting Orientation](#targeting-orientation)
    - [Combining Media Queries](#combining-media-queries)
- [Practical Examples](#practical-examples)
- [Conclusion](#conclusion)

---

## Definition and Purpose

A **media query** allows you to test for certain conditions, such as screen size, resolution, or orientation, and apply
styles accordingly. They are a cornerstone of responsive design, ensuring that your website looks great on all devices,
from smartphones to desktops.

---

## Basic Syntax of Media Queries

The syntax of a media query includes:

1. The `@media` rule.
2. The media type (e.g., `screen`, `print`).
3. A condition (e.g., `max-width: 768px`).
4. A block of CSS rules to apply when the condition is true.

Example:

```css
@media (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```  

This rule applies a light blue background when the screen width is 768px or smaller.

---

## Using Media Queries in CSS

### Targeting Screen Sizes

You can create styles for different device sizes using `max-width` or `min-width`.

```css
@media (max-width: 600px) {
    body {
        font-size: 14px;
    }
}

@media (min-width: 601px) and (max-width: 1200px) {
    body {
        font-size: 18px;
    }
}
```  

### Targeting Orientation

Use media queries to style based on device orientation (`portrait` or `landscape`).

```css
@media (orientation: portrait) {
    body {
        background-color: pink;
    }
}

@media (orientation: landscape) {
    body {
        background-color: lightgreen;
    }
}
```  

### Combining Media Queries

You can combine multiple conditions using `and`, `not`, or `or`.

```css
@media (min-width: 768px) and (orientation: landscape) {
    body {
        margin: 20px;
    }
}
```  

---

## Practical Examples

### Responsive Grid

Adjust a grid layout based on the screen size.

```css
.container {
    display: grid;
    grid-template-columns: 1fr;
}

@media (min-width: 768px) {
    .container {
        grid-template-columns: 1fr 1fr;
    }
}

@media (min-width: 1200px) {
    .container {
        grid-template-columns: 1fr 1fr 1fr;
    }
}
```  

### Hide Navigation Menu on Small Screens

Hide a menu for smaller devices and replace it with a hamburger icon.

```css
.nav-menu {
    display: block;
}

.hamburger {
    display: none;
}

@media (max-width: 768px) {
    .nav-menu {
        display: none;
    }

    .hamburger {
        display: block;
    }
}
```  

---

## Conclusion

Media queries are a powerful tool for creating responsive web designs. By tailoring styles to different devices and
conditions, you ensure an optimal user experience regardless of the user's device.

