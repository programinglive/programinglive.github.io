---
title: CSS Fundamental
layout: default
parent: CSS
grand_parent: Web Development
nav_order: 1
description: "CSS Fundamental"
---

# CSS Fundamentals: Styling the Web Like a Pro

CSS, or Cascading Style Sheets, is the design language of the web. While HTML structures your content, CSS is what makes it visually appealing. From fonts to layouts, CSS gives you the tools to create stunning, responsive designs. Let’s dive into the basics of CSS and how you can use it to elevate your web development projects.

---

## **What is CSS?**
CSS is a stylesheet language used to control the presentation of HTML elements. It allows you to define styles such as colors, fonts, spacing, and layout for web pages.

**Why Use CSS?**
1. **Separation of Content and Style**: Keeps HTML for structure and CSS for design.
2. **Consistency**: Apply the same style across multiple pages.
3. **Efficiency**: Easily update styles by changing one CSS file.

---

## **Ways to Add CSS to a Web Page**
There are three main ways to include CSS in your HTML documents:

1. **Inline CSS**:  
   Directly applied to an HTML element using the `style` attribute.
   ```html
   <p style="color: blue;">This text is blue.</p>
   ```

2. **Internal CSS**:  
   Defined within a `<style>` tag inside the `<head>` section.
   ```html
   <style>
     p {
       color: blue;
     }
   </style>
   ```

3. **External CSS**:  
   Saved in a separate `.css` file and linked using the `<link>` tag.
   ```html
   <link rel="stylesheet" href="styles.css">
   ```
   **styles.css**:
   ```css
   p {
     color: blue;
   }
   ```

---

## **CSS Syntax**
CSS uses a simple syntax:
```css
selector {
  property: value;
}
```

**Example**:
```css
h1 {
  color: red;
  font-size: 24px;
}
```
- **Selector**: Targets the HTML element (`h1`).
- **Property**: The aspect of the element to style (`color`).
- **Value**: The style you’re applying (`red`).

---

## **Selectors in CSS**
Selectors are used to target HTML elements.

| Selector        | Description                              | Example              |
|------------------|------------------------------------------|----------------------|
| `*`             | Selects all elements                    | `* { margin: 0; }`  |
| `element`        | Selects all elements of a type          | `p { color: black; }`|
| `.class`         | Selects elements with a class           | `.box { padding: 10px; }` |
| `#id`           | Selects an element with a specific ID    | `#header { height: 60px; }` |
| `element, element` | Selects multiple elements             | `h1, h2 { font-weight: bold; }` |

---

## **CSS Properties to Know**
1. **Color and Background**:
    - `color`: Sets text color.
    - `background-color`: Sets background color.
    - `background-image`: Adds a background image.

   ```css
   body {
     background-color: lightgray;
     color: darkblue;
   }
   ```

2. **Typography**:
    - `font-family`: Sets the font.
    - `font-size`: Adjusts text size.
    - `text-align`: Aligns text (e.g., left, center, right).

   ```css
   h1 {
     font-family: Arial, sans-serif;
     text-align: center;
   }
   ```

3. **Box Model**:  
   CSS treats every element as a box with:
    - `margin`: Space outside the element.
    - `border`: Surrounds the element.
    - `padding`: Space between the content and the border.

   ```css
   div {
     margin: 10px;
     padding: 20px;
     border: 1px solid black;
   }
   ```

4. **Flexbox and Grid**:
    - `display: flex`: For flexible layouts.
    - `display: grid`: For grid-based designs.

---

## **CSS Best Practices**
1. **Use External Stylesheets**: Keeps HTML clean and reusable.
2. **Organize Your Code**: Group similar styles and comment sections.
3. **Avoid Inline Styles**: They’re hard to maintain and overwrite.
4. **Responsive Design**: Use media queries to ensure your design works on all devices.

**Example**:
```css
@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
}
```

---

## **Next Steps**
After mastering the basics, explore CSS animations, variables, and frameworks like Bootstrap or Tailwind CSS. With CSS, you can transform plain HTML into visually captivating web experiences.