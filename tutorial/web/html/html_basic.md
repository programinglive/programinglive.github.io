---
title: HTML Basic
layout: default
parent: HTML
grand_parent: Web Development
nav_order: 1
description: "HTML Basic"
---

# HTML Basics

HTML, or HyperText Markup Language, is the foundation of every website you visit. It is the core language that structures content on the web, from simple text to multimedia. Whether you're new to web development or brushing up on basics, this guide will walk you through the essentials of HTML.

---

## **What is HTML?**
HTML is a markup language used to create and structure the content of web pages. It uses *tags* to define elements like headings, paragraphs, images, and links. These tags tell the browser how to display the content.

---

## **Basic Structure of an HTML Document**
Every HTML document follows a standard structure:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My First HTML Page</title>
  </head>
  <body>
    <h1>Welcome to My Page!</h1>
    <p>This is my first HTML document.</p>
  </body>
</html>
```

Here’s a breakdown:
- **`<!DOCTYPE html>`**: Declares the document as HTML5.
- **`<html>`**: The root element of the HTML document.
- **`<head>`**: Contains metadata like the title and links to stylesheets.
- **`<title>`**: Sets the page title shown on the browser tab.
- **`<body>`**: Holds all the visible content of the webpage.

---

## **Common HTML Tags and Their Uses**

| Tag           | Description                             | Example                                      |
|---------------|-----------------------------------------|----------------------------------------------|
| `<h1> to <h6>`| Headings (h1 is the largest, h6 smallest)| `<h1>Welcome</h1>`                          |
| `<p>`         | Paragraph                              | `<p>This is a paragraph.</p>`               |
| `<a>`         | Hyperlink                              | `<a href="https://example.com">Visit</a>`   |
| `<img>`       | Image                                  | `<img src="image.jpg" alt="Description">`   |
| `<ul>` & `<ol>`| Unordered and Ordered Lists           | `<ul><li>Item 1</li></ul>`                  |
| `<div>`       | Sectioning content                    | `<div>Section</div>`                        |
| `<span>`      | Inline container                      | `<span>Inline text</span>`                  |

---

## **Attributes in HTML**
Tags can have attributes to define additional properties. Attributes are added inside the opening tag.  
**Example**:
```html
<a href="https://example.com" target="_blank">Open Link</a>
```
- **`href`**: Specifies the URL.
- **`target="_blank"`**: Opens the link in a new tab.

---

## **Best Practices**
1. **Use semantic tags**: Tags like `<header>`, `<footer>`, and `<main>` enhance accessibility and SEO.
2. **Close your tags**: Always close tags like `<p>` and `<div>` to avoid rendering issues.
3. **Indent your code**: Proper indentation improves readability.

---

## **Next Steps**
Once you’ve mastered the basics, explore advanced topics like CSS for styling and JavaScript for interactivity. HTML is just the beginning of your web development journey!