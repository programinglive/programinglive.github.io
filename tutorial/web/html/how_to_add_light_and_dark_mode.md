---
title: How to Add Light and Dark Mode to Your Website
layout: default
parent: HTML
grand_parent: Web Development
description: "How to Add Light and Dark Mode to Your Website"
---

# How to Add Light and Dark Mode to Your Website?

Light and dark modes are essential features in modern web design. They enhance user experience by offering flexibility
for different lighting conditions and personal preferences. In this tutorial, you’ll learn how to add a light/dark mode
toggle to your website using HTML, CSS, and JavaScript. Let’s dive in!

<a href="https://codepen.io/moszes/pen/LYovrEL" target="_blank" style="text-decoration: none;">
  <button style="background: none; border: none; cursor: pointer;">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-external-link"><title>External Link</title><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V13"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
  </button>
  <span style="margin-left: 5px;">Open in CodePen</span>
</a>

---

## Table of Contents

1. [Step 1: Setting Up Your Project](#step-1-setting-up-your-project)
2. [Step 2: Styling Light and Dark Modes in CSS](#step-2-styling-light-and-dark-modes-in-css)
3. [Step 3: Adding JavaScript for Theme Switching](#step-3-adding-javascript-for-theme-switching)
4. [Step 4: Enhancing the User Experience](#step-4-enhancing-the-user-experience)
5. [Step 5: Testing Your Implementation](#step-5-testing-your-implementation)
6. [Step 6: Optional Improvements](#step-6-optional-improvements)
7. [Conclusion](#conclusion)

---

## Step 1: Setting Up Your Project

First, create the basic structure of your project. You’ll need three files:

- `index.html`: The HTML file.
- `style.css`: The CSS file for styling.
- `script.js`: The JavaScript file for functionality.

Here’s the folder structure:

```
/project-folder
    index.html
    style.css
    script.js
```

### `index.html`

Add the following code to your HTML file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Light & Dark Mode</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
<header>
  <h1>Light and Dark Mode</h1>
  <button id="theme-toggle">Switch Mode</button>
</header>
<p>Toggle between light and dark themes to see the difference!</p>
<script src="script.js"></script>
</body>
</html>
```

---

## Step 2: Styling Light and Dark Modes in CSS

Now, define the styles for both light and dark modes.

### `style.css`

```css
/* Default light mode */
body {
    background-color: white;
    color: black;
    font-family: Arial, sans-serif;
    transition: background-color 0.3s, color 0.3s;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background-color: #f0f0f0;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

button {
    padding: 0.5rem 1rem;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    background-color: #007BFF;
    color: white;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}

/* Dark mode styles */
body.dark-mode {
    background-color: #121212;
    color: #e0e0e0;
}

body.dark-mode header {
    background-color: #c0392b;
}

body.dark-mode button {
    background-color: #444;
}
```

---

## Step 3: Adding JavaScript for Theme Switching

Now, create the JavaScript logic to toggle themes and save user preferences.

### `script.js`

```javascript
// Select the toggle button and body element
const toggleButton = document.getElementById('theme-toggle');
const body = document.body;

// Load the saved theme from localStorage
const savedTheme = localStorage.getItem('theme');
if (savedTheme) {
	body.classList.add(savedTheme);
	toggleButton.textContent = savedTheme === 'dark-mode' ? 'Switch to Light Mode' : 'Switch to Dark Mode';
}

// Event listener for the button
toggleButton.addEventListener('click', () => {
	// Toggle the dark-mode class
	const isDarkMode = body.classList.toggle('dark-mode');
	// Save the current theme in localStorage
	const theme = isDarkMode ? 'dark-mode' : '';
	localStorage.setItem('theme', theme);
	// Update button text
	toggleButton.textContent = isDarkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode';
});
```

---

## Step 4: Enhancing the User Experience

### Adding Smooth Transitions

Ensure smooth transitions when switching between modes using the `transition` property in CSS:

```css
body {
    transition: background-color 0.3s, color 0.3s;
}
```

### Auto-Detect System Preferences

Use the `prefers-color-scheme` media query to automatically set the theme based on the user’s system preference:

```css
@media (prefers-color-scheme: dark) {
    body {
        background-color: #121212;
        color: #e0e0e0;
    }
}
```

---

## Step 5: Testing Your Implementation

1. Open the `index.html` file in a browser.
2. Click the "Switch Mode" button to toggle between themes.
3. Refresh the page to verify that your theme preference is saved.

---

## Step 6: Optional Improvements

1. **Customizable Theme Colors:** Allow users to choose custom colors for each theme.
2. **Dynamic Button Design:** Replace the text button with an icon (e.g., a sun/moon toggle).
3. **Accessibility:** Ensure color contrast meets accessibility standards.

---

## Conclusion

By following this tutorial, you’ve created a functional light/dark mode toggle for your website. This feature not only
enhances usability but also demonstrates your attention to user preferences.

What’s next? Experiment with more advanced theme-switching techniques or integrate this functionality into a real
project.