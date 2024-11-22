---
title: HTML Basic
layout: default
parent: HTML
grand_parent: Web Development
nav_order: 1
description: "HTML Basic"
---

# HTML Basic

**HTML (Hypertext Markup Language)** is the core building block of web development. It structures content on the web,
allowing browsers to render text, images, videos, and interactive forms. Understanding the basics of HTML is essential
for anyone looking to create websites or web applications.

---

## Table of Contents

1. [What is HTML?](#what-is-html)
2. [Basic Structure of an HTML Document](#basic-structure-of-an-html-document)
3. [Common HTML Tags](#common-html-tags)
4. [HTML Elements and Attributes](#html-elements-and-attributes)
5. [How to Create a Simple Web Page](#how-to-create-a-simple-web-page)
6. [Conclusion](#conclusion)

---

## 1. What is HTML?

HTML is the standard markup language for creating webpages. It provides a framework to structure content using various
tags. Browsers read and interpret HTML code to display a webpage. Every webpage you see on the internet is created using
HTML to define its structure.

---

## 2. Basic Structure of an HTML Document

An HTML document is composed of various elements. The basic structure of an HTML document consists of:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Web Page</title>
</head>
<body>
<h1>Welcome to My Website</h1>
<p>This is a paragraph of text.</p>
</body>
</html>
```

### Key components:

- **`<!DOCTYPE html>`**: Declares the document type and tells the browser to expect HTML5 code.
- **`<html>`**: The root element that wraps the entire HTML document.
- **`<head>`**: Contains meta-information such as the title, character encoding, and links to external files (like CSS
  or JavaScript).
- **`<body>`**: Contains the content visible to the user, such as text, images, and links.

---

## 3. Common HTML Tags

Here are some of the most commonly used HTML tags:

- **`<h1>` to `<h6>`**: Heading tags for creating titles and subtitles. `<h1>` is the largest heading, while `<h6>` is
  the smallest.
  ```html
  <h1>Main Heading</h1>
  <h2>Subheading</h2>
  ```

- **`<p>`**: Paragraph tag, used to define text paragraphs.
  ```html
  <p>This is a paragraph.</p>
  ```

- **`<a>`**: Anchor tag, used to create hyperlinks.
  ```html
  <a href="https://www.example.com">Visit Example</a>
  ```

- **`<img>`**: Image tag, used to embed images. It is self-closing, meaning it doesn't require an end tag.
  ```html
  <img src="image.jpg" alt="Description of the image">
  ```

- **`<ul>`** and **`<ol>`**: List tags used for unordered (bulleted) and ordered (numbered) lists, respectively.
  ```html
  <ul>
      <li>Item 1</li>
      <li>Item 2</li>
  </ul>
  ```

- **`<br>`**: Line break tag, used to create a line break within text. It’s self-closing.
  ```html
  Line one.<br>Line two.
  ```

---

## 4. HTML Elements and Attributes

**HTML Elements**: An HTML element is a combination of an opening tag, content, and a closing tag. For example:

```html
<h1>This is a heading</h1>
<p>This is a paragraph of text.</p>
```

Each tag defines the type of content (e.g., a heading or a paragraph).

**HTML Attributes**: Tags can have additional information attached to them via attributes. Attributes are written within
the opening tag. Some common attributes include:

- **`href`**: Specifies the URL in a hyperlink (`<a>` tag).
  ```html
  <a href="https://www.example.com">Visit Example</a>
  ```

- **`src`**: Specifies the source of an image or video (`<img>`, `<video>` tags).
  ```html
  <img src="logo.png" alt="Website Logo">
  ```

- **`alt`**: Provides alternative text for an image if it fails to load.
  ```html
  <img src="logo.png" alt="Description of the logo">
  ```

- **`class`**: Specifies the class of an element for CSS styling.
  ```html
  <div class="container">Content here</div>
  ```

- **`id`**: Defines a unique identifier for an element, often used in JavaScript.
  ```html
  <p id="unique-paragraph">This paragraph has a unique ID.</p>
  ```

---

## 5. How to Create a Simple Web Page

Let’s combine the basic HTML structure and tags to create a simple webpage. Below is an example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Web Page</title>
</head>
<body>
<h1>Welcome to My Website</h1>
<p>This is my very first webpage!</p>
<p>HTML is simple, and learning it is fun!</p>
<a href="https://www.example.com">Click here to visit Example</a>
<img src="image.jpg" alt="An example image">
</body>
</html>
```

This page contains:

- A main heading (`<h1>`).
- Two paragraphs (`<p>`).
- A hyperlink (`<a>`).
- An image (`<img>`).

---

## 6. Conclusion

**HTML** is the backbone of web pages, providing the structure and content that browsers interpret and display. Learning
HTML basics is the first step to becoming a web developer, and it is essential for building and designing websites. Once
comfortable with HTML, you can begin integrating **CSS** for styling and **JavaScript** for interactivity, creating
fully functional and responsive websites.