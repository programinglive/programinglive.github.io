---
title: HTML
layout: default
parent: Web Development
nav_order: 1
description: "Tutorial HTML"
---

# HTML

**HTML** (Hypertext Markup Language) is the standard language used to create and design webpages. It is the backbone of
web development, providing the structure and content of a webpage. HTML allows web developers to create and organize
elements like headings, paragraphs, links, images, forms, and more.

---

## Table of Contents

1. [Introduction to HTML](#introduction-to-html)
2. [Basic Structure of an HTML Document](#basic-structure-of-an-html-document)
3. [HTML Elements](#html-elements)
4. [HTML Tags](#html-tags)
5. [Commonly Used HTML Tags](#commonly-used-html-tags)
6. [HTML Attributes](#html-attributes)
7. [HTML Syntax](#html-syntax)
8. [Conclusion](#conclusion)

---

## 1. Introduction to HTML

HTML is the foundation of all web pages. It defines the layout and structure of the content on the web, using a series
of elements represented by tags. These elements form the building blocks of a webpage, determining how text, images, and
links are presented.

HTML files typically have the `.html` file extension and can be opened in any web browser. It’s important to note that
HTML only provides the structure; to style and add interactivity, **CSS** (Cascading Style Sheets) and **JavaScript**
are used in conjunction with HTML.

---

## 2. Basic Structure of an HTML Document

An HTML document follows a basic structure, with specific elements required to ensure proper rendering in a web browser.
Here’s a simple example of the basic structure of an HTML document:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Web Page</title>
</head>
<body>
<h1>Welcome to My Web Page</h1>
<p>This is a paragraph of text.</p>
</body>
</html>
```

- **`<!DOCTYPE html>`**: Declares the document type and version of HTML.
- **`<html>`**: The root element that wraps all the content of the webpage.
- **`<head>`**: Contains metadata about the webpage, such as the title, character encoding, and links to stylesheets or
  scripts.
- **`<body>`**: Contains the main content of the webpage that is visible to the user.

---

## 3. HTML Elements

An **HTML element** consists of a start tag, content, and an end tag. For example:

```html
<p>This is a paragraph.</p>
```

Here:

- `<p>` is the start tag, indicating the beginning of a paragraph.
- `This is a paragraph.` is the content of the element.
- `</p>` is the end tag, closing the paragraph element.

Some elements, like images and links, may be self-closing, meaning they don’t have separate closing tags.

---

## 4. HTML Tags

**Tags** in HTML are used to define the structure and content of a webpage. Tags are typically written in angle
brackets, and most HTML elements use both a start and an end tag.

- **Start tag**: `<tag>`
- **End tag**: `</tag>`  
  The end tag has a forward slash (`/`) before the tag name to indicate the closing of the element.

Examples:

- **`<h1>`, `<h2>`, `<h3>`, etc.**: Heading tags used to define headings of various levels.
- **`<p>`**: Paragraph tag used to define a block of text.
- **`<a>`**: Anchor tag used to create hyperlinks.

---

## 5. Commonly Used HTML Tags

Here are some commonly used HTML tags and their purposes:

- **`<h1>` to `<h6>`**: Header tags for defining headings (e.g., `<h1>` is the largest, and `<h6>` is the smallest).
- **`<p>`**: Defines a paragraph of text.
- **`<a>`**: Creates a hyperlink to another webpage.
- **`<img>`**: Embeds an image on the webpage.
- **`<ul>`, `<ol>`, `<li>`**: List tags for creating unordered or ordered lists.
- **`<div>`**: A generic container used to group elements.
- **`<span>`**: A generic inline container used for styling parts of text.
- **`<form>`**: Defines a form for user input, often containing `<input>`, `<select>`, `<textarea>`, and `<button>`
  tags.

---

## 6. HTML Attributes

**Attributes** provide additional information about HTML elements. They are usually placed inside the start tag and are
written in the form of `name="value"`.

### Examples of attributes:

- **`href`**: Defines the destination URL for a hyperlink (used with `<a>`).

  ```html
  <a href="https://www.example.com">Visit Example</a>
  ```

- **`src`**: Specifies the source of an image (used with `<img>`).

  ```html
  <img src="image.jpg" alt="An example image">
  ```

- **`alt`**: Provides alternative text for images (used with `<img>`).

  ```html
  <img src="image.jpg" alt="A descriptive text about the image">
  ```

- **`class`**: Defines the class name for styling with CSS.

  ```html
  <div class="container">Content goes here</div>
  ```

---

## 7. HTML Syntax

HTML syntax is simple and follows a set of rules. Here are some key points to remember:

- **Tags are case-insensitive** but it’s common practice to use lowercase letters.
- **Nesting of elements**: HTML elements can be nested within other elements, but they must be properly opened and
  closed.
- **Self-closing tags**: Some elements, like `<img>`, `<br>`, and `<input>`, do not have separate closing tags and are
  written as self-closing elements.

Example:

```html
<img src="logo.png" alt="Company Logo">
<br>
```

- **Comments**: Comments can be added using `<!-- -->` to explain parts of the code.

  ```html
  <!-- This is a comment -->
  ```

---

## 8. Conclusion

HTML is the foundational language of the web, providing structure to all webpages. Whether you are building a simple
personal site or a complex web application, HTML plays a central role in organizing content and making it accessible to
users. Understanding HTML is the first step in web development, and it is essential to master its basic elements, tags,
and syntax to create effective and responsive websites.