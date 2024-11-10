---
title: CSS
layout: default
parent: Web Development
nav_order: 2
description: "Tutorial CSS"
---

# What is CSS?

CSS, or **Cascading Style Sheets**, is a stylesheet language used to describe the presentation of a document written in HTML. CSS allows you to control the layout, colors, fonts, and overall look of your web pages, helping you create visually appealing and user-friendly websites.

---

## **How CSS Works**

CSS works by selecting HTML elements and applying styles to them. A CSS file or CSS rules are usually linked to HTML documents so that browsers know how to display the content.

---

## **Basic Syntax of CSS**

CSS has a simple syntax:
```css
selector {
  property: value;
}
```

### **Explanation:**
- **Selector**: Specifies the HTML element(s) to style.
- **Property**: Defines the style attribute you want to change (like `color`, `font-size`, etc.).
- **Value**: Specifies the value of the property.

For example:
```css
h1 {
  color: blue;
  font-size: 24px;
}
```
This rule changes the color of `<h1>` elements to blue and sets their font size to 24 pixels.

---

## **Ways to Add CSS**

There are three main ways to apply CSS to HTML:

### 1. **Inline CSS**
Add styles directly to an HTML element using the `style` attribute:
   ```html
   <p style="color: red;">This is a red paragraph.</p>
   ```

### 2. **Internal CSS**
Add a `<style>` block within the `<head>` section of your HTML document:
   ```html
   <head>
     <style>
       p {
         color: red;
       }
     </style>
   </head>
   ```

### 3. **External CSS**
Link an external CSS file to your HTML document:
   ```html
   <link rel="stylesheet" href="styles.css">
   ```
Then, in `styles.css`:
   ```css
   p {
     color: red;
   }
   ```

---

## **CSS Selectors**

CSS selectors are used to "select" HTML elements for styling. Here are a few basic selectors:

### 1. **Type Selector**
Selects all elements of a specific type.
   ```css
   h1 {
     color: green;
   }
   ```

### 2. **Class Selector**
Selects elements with a specific class. Add a period (`.`) before the class name.
   ```css
   .example {
     color: blue;
   }
   ```
In HTML:
   ```html
   <p class="example">This is blue text.</p>
   ```

### 3. **ID Selector**
Selects an element with a specific ID. Add a hashtag (`#`) before the ID name.
   ```css
   #unique {
     color: purple;
   }
   ```
In HTML:
   ```html
   <p id="unique">This is purple text.</p>
   ```

### 4. **Universal Selector**
Selects all elements.
   ```css
   * {
     margin: 0;
     padding: 0;
   }
   ```

### 5. **Attribute Selector**
Selects elements with a specific attribute.
   ```css
   input[type="text"] {
     background-color: lightyellow;
   }
   ```

---

## **CSS Properties**

There are hundreds of CSS properties available. Here are some of the most commonly used:

### 1. **Color**
   ```css
   color: red; /* Text color */
   background-color: yellow; /* Background color */
   ```

### 2. **Font and Text**
   ```css
   font-size: 20px; /* Font size */
   font-family: Arial, sans-serif; /* Font family */
   text-align: center; /* Text alignment */
   ```

### 3. **Margin and Padding**
- **Margin**: Creates space outside an element.
- **Padding**: Creates space inside an element, between the content and its border.
   ```css
   margin: 10px;
   padding: 20px;
   ```

### 4. **Border**
   ```css
   border: 2px solid black; /* Sets border width, style, and color */
   border-radius: 10px; /* Rounds the corners */
   ```

### 5. **Width and Height**
   ```css
   width: 300px;
   height: 200px;
   ```

---

## **CSS Layout: Flexbox and Grid**

### 1. **Flexbox**
Flexbox is useful for arranging items in a row or column. Here's a basic example:
   ```css
   .container {
     display: flex;
     justify-content: center; /* Aligns items horizontally */
     align-items: center; /* Aligns items vertically */
   }
   ```
   ```html
   <div class="container">
     <div>Box 1</div>
     <div>Box 2</div>
   </div>
   ```

### 2. **Grid**
CSS Grid is a two-dimensional layout system, allowing control over both rows and columns.
   ```css
   .grid-container {
     display: grid;
     grid-template-columns: auto auto auto; /* Creates three columns */
     gap: 10px;
   }
   ```
   ```html
   <div class="grid-container">
     <div>Box 1</div>
     <div>Box 2</div>
     <div>Box 3</div>
   </div>
   ```

---

## **Responsive Design with Media Queries**

Media queries allow you to apply styles based on the device's screen size.
```css
/* Styles for screens 600px wide or less */
@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
}
```

---

## **Example: Putting It All Together**

Let’s create a simple CSS file for an HTML structure:

**HTML:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>CSS Tutorial</title>
</head>
<body>
  <header>
    <h1>Welcome to CSS Basics</h1>
  </header>
  <section class="content">
    <p class="intro">Learn how to style your website using CSS!</p>
    <button class="cta-button">Get Started</button>
  </section>
</body>
</html>
```

**CSS (`styles.css`):**
```css
/* Basic Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Styling header */
header {
  background-color: #4CAF50;
  padding: 20px;
  text-align: center;
}

header h1 {
  color: white;
  font-size: 2em;
}

/* Styling the content section */
.content {
  margin: 20px;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 8px;
}

/* Styling the intro paragraph */
.intro {
  font-size: 1.2em;
  color: #333;
}

/* Button styling */
.cta-button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1em;
}

.cta-button:hover {
  background-color: #45a049;
}
```

### **Explanation of CSS Example:**
- **Header Styling**: The header has a green background, centered text, and a white font color.
- **Content Section**: The content has a light gray background with padding and rounded corners.
- **Button**: The button has a green background, white text, and changes color on hover.

---

## **Conclusion**

This CSS tutorial provides a foundation for styling web pages. By learning how to apply CSS rules, use selectors, and utilize layout tools like Flexbox and Grid, you’ll be able to create more visually appealing and functional websites. Start experimenting, and soon CSS will become a powerful tool in your web development toolkit!