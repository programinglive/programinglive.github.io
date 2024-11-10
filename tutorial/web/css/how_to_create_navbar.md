---
title: How to Create a Navigation Bar
layout: default
parent: CSS
grand_parent: Web Development
nav_order: 2
description: "How to Create a Navigation Bar"
---

# How to Create a Navigation Bar

A **navigation bar** is an essential component of any website, allowing users to navigate different sections with ease. In this article, we’ll go through creating a responsive and modern navigation bar using HTML, CSS, and JavaScript.

## Step 1: Setting Up HTML Structure

To start, let’s create the basic structure of our navigation bar in HTML. This includes setting up links to different pages or sections and organizing them into a menu.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Navigation Bar</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Navigation Bar -->
    <nav class="navbar">
        <div class="navbar-logo">
            <a href="#">MyWebsite</a>
        </div>
        <ul class="navbar-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <!-- Hamburger Icon for Mobile View -->
        <div class="navbar-toggle" id="mobile-menu">
            <span class="bar"></span>
            <span class="bar"></span>
            <span class="bar"></span>
        </div>
    </nav>

    <!-- Placeholder Content -->
    <div id="home"><h2>Home Section</h2></div>
    <div id="about"><h2>About Section</h2></div>
    <div id="services"><h2>Services Section</h2></div>
    <div id="contact"><h2>Contact Section</h2></div>

    <script src="script.js"></script>
</body>
</html>
```

In this HTML, the `navbar` is the main container. Inside it, we have:
- **Logo** link that acts as the home button.
- **Links** to various sections (Home, About, Services, Contact).
- A **hamburger icon** that will appear on smaller screens.

## Step 2: Styling the Navigation Bar with CSS

Next, we’ll use CSS to style the navigation bar and make it responsive.

Create a `styles.css` file and add the following styles:

```css
/* Reset some default browser styling */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Basic styling for the body */
body {
    font-family: Arial, sans-serif;
}

/* Styling for the navbar */
.navbar {
    background-color: #333;
    color: #fff;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
}

.navbar-logo a {
    font-size: 1.5rem;
    color: #fff;
    text-decoration: none;
}

.navbar-links {
    list-style: none;
    display: flex;
}

.navbar-links li {
    margin-left: 1.5rem;
}

.navbar-links a {
    color: #fff;
    text-decoration: none;
    font-size: 1rem;
}

/* Hover effect on links */
.navbar-links a:hover {
    color: #ddd;
}

/* Styling the hamburger icon */
.navbar-toggle {
    display: none;
    flex-direction: column;
    cursor: pointer;
}

.navbar-toggle .bar {
    height: 3px;
    width: 25px;
    background-color: #fff;
    margin: 4px 0;
    transition: 0.4s;
}

/* Responsive styling */
@media (max-width: 768px) {
    .navbar-links {
        display: none;
        position: absolute;
        top: 60px;
        left: 0;
        width: 100%;
        background-color: #333;
        flex-direction: column;
        text-align: center;
    }

    .navbar-links li {
        margin: 1rem 0;
    }

    .navbar-toggle {
        display: flex;
    }

    .navbar-links.active {
        display: flex;
    }
    .section {
        display: none; /* Hide all sections by default */
    }

    .section.active {
        display: block; /* Show only the active section */
    }

}
```

### Explanation of CSS Styling:

1. **Desktop View**: In larger screens, the navigation bar displays the logo, links horizontally, and hides the hamburger menu.
2. **Responsive View**: For screens narrower than 768px, the links are hidden initially and shown when the `active` class is added (we'll handle this in JavaScript). The hamburger icon appears, and the links are styled to take up the entire width of the screen.

## Step 3: Adding JavaScript for the Mobile Toggle

To make the navigation bar responsive, we need to add JavaScript that toggles the display of the links when the hamburger icon is clicked.

Create a `script.js` file and add the following code:

```javascript
// Select all navigation links and sections
const navLinks = document.querySelectorAll('.navbar-links a');
const sections = document.querySelectorAll('.section');

// Function to hide all sections and show the selected one
function showSection(sectionId) {
	sections.forEach((section) => {
		section.classList.remove('active');
	});
	document.getElementById(sectionId).classList.add('active');
}

// Add click event listeners to each navigation link
navLinks.forEach((link) => {
	link.addEventListener('click', (e) => {
		e.preventDefault();
		const targetSection = link.getAttribute('href').substring(1); // Get section ID
		showSection(targetSection); // Show the selected section
	});
});
```

### Explanation of JavaScript Code:

1. **Selecting Elements**: We select the hamburger menu (`mobileMenu`) and the navigation links (`navbarLinks`).
2. **Event Listener**: We add an event listener on the `mobileMenu` element that toggles the `active` class on `navbarLinks`. This triggers the display of the links in mobile view.

## Final Touches: Adding Smooth Scroll and Hover Effects

For a polished experience, let’s add smooth scrolling to each section link.

Add this CSS for smooth scrolling in `styles.css`:

```css
html {
    scroll-behavior: smooth;
}
```

Now, when a user clicks on a link, the page scrolls smoothly to the relevant section.

## Complete Code

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Navigation Bar</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav class="navbar">
        <div class="navbar-logo">
            <a href="#">MyWebsite</a>
        </div>
        <ul class="navbar-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="navbar-toggle" id="mobile-menu">
            <span class="bar"></span>
            <span class="bar"></span>
            <span class="bar"></span>
        </div>
    </nav>

    <div id="home" class="section active"><h2>Home Section</h2></div>
    <div id="about" class="section"><h2>About Section</h2></div>
    <div id="services" class="section"><h2>Services Section</h2></div>
    <div id="contact" class="section"><h2>Contact Section</h2></div>

    <script src="script.js"></script>
</body>
</html>
```

### `styles.css`

Copy the CSS from the previous section, adding it to this file.

### `script.js`

Copy the JavaScript code from the previous section, adding it to this file.

---

## Demo

[Link Demo](https://codepen.io/moszes/pen/QWXVrmz?editors=1111)

---

## Conclusion

Creating a responsive navigation bar involves HTML for structure, CSS for styling and responsiveness, and JavaScript for toggle functionality in mobile view. Following this approach, you can create a versatile navigation bar that adapts well to various screen sizes, providing a seamless experience for users on both desktop and mobile devices.

{:toc}