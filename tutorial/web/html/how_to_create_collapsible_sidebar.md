---
title: How to Create a Collapsible Sidebar
layout: default
parent: HTML
grand_parent: Web Development
description: "How to Create a Collapsible Sidebar"
---

# How to Create a Collapsible Sidebar

A collapsible sidebar is a popular UI element that allows users to toggle the sidebar's visibility to gain more screen
space. In this tutorial, we’ll create a simple, collapsible sidebar using HTML, CSS, and JavaScript, with a minimal and
responsive design.

<a href="https://codepen.io/moszes/pen/QWRXVPr?editors=1111" target="_blank" style="text-decoration: none;">
  <button style="background: none; border: none; cursor: pointer;">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-external-link"><title>External Link</title><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V13"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
  </button>
  <span style="margin-left: 5px;">Open in CodePen</span>
</a>

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Step 1: Set Up the HTML Structure](#step-1-set-up-the-html-structure)
3. [Step 2: Style the Sidebar with CSS](#step-2-style-the-sidebar-with-css)
4. [Step 3: Add JavaScript for Toggle Functionality](#step-3-add-javascript-for-toggle-functionality)
5. [Step 4: Make it Responsive](#step-4-make-it-responsive)
6. [Conclusion](#conclusion)

## Prerequisites

To follow this tutorial, you should have basic knowledge of [HTML](index.md), [CSS](../css/index.md),
and [JavaScript](../javascript/index.md).

---

## Step 1: Set Up the HTML Structure

Start by creating the basic structure in HTML. This includes a sidebar, a toggle button, and a main content area.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Collapsible Sidebar</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
<div class="sidebar" id="sidebar">
  <h2>Menu</h2>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Services</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</div>
<div class="content">
  <button class="toggle-btn" onclick="toggleSidebar()">☰</button>
  <h1>Main Content Area</h1>
  <p>This is the main content area where your page content goes.</p>
</div>
<script src="script.js"></script>
</body>
</html>
```

In this structure:

- The `.sidebar` class defines the sidebar.
- The `.content` class represents the main content area.
- The `toggle-btn` button toggles the visibility of the sidebar.

---

## Step 2: Style the Sidebar with CSS

Now, let's style the sidebar and main content in `styles.css`.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    display: flex;
    font-family: Arial, sans-serif;
}

.sidebar {
    width: 250px;
    background-color: #333;
    color: white;
    padding: 20px;
    position: relative;
    transition: width 0.3s;
}

.sidebar h2 {
    margin-bottom: 20px;
}

.sidebar ul {
    list-style-type: none;
}

.sidebar ul li {
    margin: 10px 0;
}

.sidebar ul li a {
    color: white;
    text-decoration: none;
}

.content {
    flex: 1;
    padding: 20px;
}

.toggle-btn {
    font-size: 20px;
    padding: 10px;
    background: #333;
    color: white;
    border: none;
    cursor: pointer;
}
```

In this CSS:

- The `.sidebar` is styled with a width of 250px, a dark background, and padding for spacing.
- The `.toggle-btn` is styled to make it visible on the page.

---

## Step 3: Add JavaScript for Toggle Functionality

Next, add JavaScript to toggle the sidebar's visibility. Create a `script.js` file with the following code:

```javascript
function toggleSidebar() {
	const sidebar = document.getElementById('sidebar');
	if (sidebar.style.width === '250px' || sidebar.style.width === '') {
		sidebar.style.width = '0';
	} else {
		sidebar.style.width = '250px';
	}
}
```

In this function:

- If the sidebar's width is 250px or its default value, it collapses the sidebar to 0 width.
- Otherwise, it expands the sidebar to 250px.

---

## Step 4: Make it Responsive

Finally, we'll add a media query to ensure the sidebar behaves responsively on smaller screens.

Add the following CSS to `styles.css`:

```css
@media (max-width: 768px) {
    .sidebar {
        width: 0;
        padding: 0;
    }

    .content {
        padding: 20px 10px;
    }
}
```

In this media query:

- On screens smaller than 768px, the sidebar is hidden by default (set to width 0).
- The content padding is reduced for a better fit on smaller devices.

---

## Conclusion

You’ve now created a simple, collapsible sidebar that expands and collapses when the user clicks the toggle button. This
layout is responsive, meaning it adjusts to smaller screens by hiding the sidebar by default and offering more space for
content. You can further customize the sidebar with animations, icons, and other interactive features as per your
project requirements.