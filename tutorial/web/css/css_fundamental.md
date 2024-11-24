---
title: CSS Fundamental
layout: default
parent: CSS
grand_parent: Web Development
nav_order: 1
description: "CSS Fundamental"
---

# CSS Fundamentals: Building Blocks for Web Design

CSS fundamentals are the core principles and techniques every developer needs to know to style web pages effectively.
This guide covers essential concepts to get you started on mastering CSS.

---

## Table of Contents

- [The Cascade in CSS](#the-cascade-in-css)
    - [Specificity](#specificity)
    - [Inheritance](#inheritance)
    - [The Importance of the Cascade](#the-importance-of-the-cascade)
- [The Box Model](#the-box-model)
    - [Content, Padding, Border, Margin](#content-padding-border-margin)
    - [Visualizing the Box Model](#visualizing-the-box-model)
- [CSS Units](#css-units)
    - [Absolute Units](#absolute-units)
    - [Relative Units](#relative-units)
- [Positioning in CSS](#positioning-in-css)
    - [Static Positioning](#static-positioning)
    - [Relative Positioning](#relative-positioning)
    - [Absolute and Fixed Positioning](#absolute-and-fixed-positioning)
- [Flexbox and Grid Layout](#flexbox-and-grid-layout)
    - [Flexbox](#flexbox)
    - [Grid](#grid)
- [Conclusion](#conclusion)

---

## The Cascade in CSS

CSS stands for **Cascading Style Sheets**, where "cascading" refers to the rules that determine how styles are applied
when there are conflicts.

### Specificity

Specificity determines which styles take precedence when multiple rules apply.

- Inline styles (`style` attribute) have the highest specificity.
- ID selectors (`#idName`) are more specific than class selectors (`.className`).

Example:

```html

<style>
    p {
        color: blue; /* Less specific */
    }

    #special {
        color: red; /* More specific */
    }
</style>
<p id="special">This text is red.</p>
```  

### Inheritance

Some properties, like text color and font, are inherited by child elements. Others, like margin and padding, are not.

Example:

```html

<style>
    div {
        color: green;
    }
</style>
<div>
    <p>This text is green because it inherits the color.</p>
</div>
```  

### The Importance of the Cascade

The cascade ensures that styles are applied logically, allowing you to create flexible designs without redundant code.

---

## The Box Model

The box model is at the heart of CSS layout. Every element is a rectangular box composed of:

### Content, Padding, Border, Margin

- **Content**: The actual content of the element (text, images, etc.).
- **Padding**: Space between the content and the border.
- **Border**: The edge surrounding the padding.
- **Margin**: Space outside the border, separating the element from others.

### Visualizing the Box Model

```css
div {
    width: 200px;
    padding: 10px;
    border: 5px solid black;
    margin: 20px;
}
```  

In this example:

- Total width = `200px + 10px (padding) * 2 + 5px (border) * 2 + 20px (margin) * 2`.

---

## CSS Units

### Absolute Units

- Pixels (`px`), centimeters (`cm`), and inches (`in`) are fixed-size units.  
  Example:

```css
h1 {
    font-size: 16px;
}
```  

### Relative Units

- Percentages (`%`), `em`, `rem`, and `vh`/`vw` adapt to their context.  
  Example:

```css
p {
    font-size: 1.5em; /* 1.5 times the parent font size */
}
```  

---

## Positioning in CSS

### Static Positioning

The default position of elements.

### Relative Positioning

Moves the element relative to its normal position.

```css
div {
    position: relative;
    top: 20px;
}
```  

### Absolute and Fixed Positioning

Places the element relative to its nearest positioned ancestor (absolute) or the viewport (fixed).

```css
div {
    position: absolute;
    left: 50px;
}
```  

---

## Flexbox and Grid Layout

### Flexbox

Flexbox simplifies alignment and distribution of elements.

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```  

### Grid

CSS Grid is for creating two-dimensional layouts.

```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr;
}
```  

---

## Conclusion

Understanding CSS fundamentals like the cascade, box model, and positioning is crucial for building responsive and
visually appealing websites. Experiment with these concepts to strengthen your web design skills!

Stay tuned for more advanced CSS tutorials.