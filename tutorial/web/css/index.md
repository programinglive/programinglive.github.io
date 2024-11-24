---
title: CSS
layout: default
parent: Web Development
nav_order: 2
description: "Tutorial CSS"
---

# CSS

CSS (Cascading Style Sheets) is a powerful tool that lets you style and lay out your web pages effectively. Whether
you're creating your first website or improving an existing one, understanding CSS is essential.

---

## Table of Contents

1. [What is CSS?](#1-what-is-css)
2. [How to Add CSS to Your Website](#2-how-to-add-css-to-your-website)

- [Inline CSS](#inline-css)
- [Internal CSS](#internal-css)
- [External CSS](#external-css)

3. [Selectors in CSS](#3-selectors-in-css)
4. [CSS Properties](#4-css-properties)

- [Colors and Backgrounds](#4-1-colors-and-backgrounds)
- [Fonts and Text](#4-2-fonts-and-text)
- [Box Model](#4-3-box-model)

5. [Advanced CSS Features](#5-advanced-css-features)

- [Media Queries](#5-1-media-queries)
- [CSS Variables](#5-2-css-variables)

6. [Conclusion](#6-conclusion)

---

## 1. What is CSS?

CSS (Cascading Style Sheets) is a stylesheet language that controls the appearance of HTML elements on a web page. It
allows you to change colors, fonts, layouts, and more, making your web page visually appealing and user-friendly.

---

## 2. How to Add CSS to Your Website

There are three main ways to apply CSS to your HTML document:

### Inline CSS

Add CSS directly to an HTML element using the `style` attribute.

```html
<p style="color: blue;">This text is blue.</p>
```  

### Internal CSS

Use the `<style>` tag within the `<head>` section of your HTML document.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: red;
        }
    </style>
</head>
<body>
<p>This text is red.</p>
</body>
</html>
```  

### External CSS

Link an external CSS file using the `<link>` tag.

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
<p>This text is styled from an external file.</p>
</body>
</html>
```  

---

## 3. Selectors in CSS

CSS selectors are used to "select" HTML elements to style them.

Examples:

- Element selector: `p { color: green; }`
- Class selector: `.className { font-size: 16px; }`
- ID selector: `#idName { margin: 10px; }`

---

## 4. CSS Properties

### Colors and Backgrounds

Set text color and background styles.

```css
body {
    background-color: lightgray;
    color: darkblue;
}
```  

### Fonts and Text

Customize font style, size, and alignment.

```css
h1 {
    font-family: Arial, sans-serif;
    text-align: center;
}
```  

### Box Model

Define margins, borders, padding, and content.

```css
div {
    margin: 20px;
    padding: 10px;
    border: 1px solid black;
}
```  

---

## 5. Advanced CSS Features

### Media Queries

Adapt styles to different screen sizes.

```css
@media (max-width: 600px) {
    body {
        background-color: yellow;
    }
}
```  

### CSS Variables

Reuse values throughout your stylesheet.

```css
:root {
    --main-color: teal;
}

h1 {
    color: var(--main-color);
}
```  

---

## 6. Conclusion

CSS is an essential part of modern web development. By mastering its basics and advanced features, you can create
visually stunning and responsive websites. Keep experimenting with different properties and layouts to find what works
best for your projects.

Happy coding!