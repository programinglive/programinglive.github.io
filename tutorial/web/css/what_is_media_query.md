---
title: What is a Media Query?
layout: default
parent: CSS
grand_parent: Web Development
nav_order: 2
description: "What is a Media Query?"
---

# What is a Media Query?

**Media queries** are a fundamental part of responsive web design, allowing developers to apply different styles to a webpage based on the screen size, resolution, orientation, or other characteristics of the user’s device. This technique helps ensure that websites look great and function well on a wide range of devices, from large desktop monitors to small smartphone screens.

---

## Understanding Media Queries

A **media query** is a CSS rule that applies styles conditionally, depending on the device's properties. The most common use for media queries is to adjust the layout of a webpage based on screen width. For example, you can use media queries to rearrange or resize elements for smaller screens, making a desktop website responsive on mobile devices.

### Basic Syntax of a Media Query

A media query consists of a `@media` rule followed by one or more conditions inside parentheses and a block of CSS code that will apply only if those conditions are met. Here’s the basic structure:

```css
@media (condition) {
    /* CSS rules here will apply when the condition is true */
}
```

---

### Example: Simple Media Query

This media query applies specific styles only when the screen width is less than or equal to 600px (typically mobile devices):

```css
@media (max-width: 600px) {
    body {
        background-color: lightblue;
    }
}
```

In this example, when the screen width is 600 pixels or less, the body background color will change to light blue. For screens larger than 600px, the body will retain its default background color.

---

## Types of Conditions in Media Queries

Media queries can target various conditions and features of the device or viewport. The most commonly used conditions include:

1. **Width and Height**
    - **max-width**: Targets screens with a width less than or equal to a specified value.
    - **min-width**: Targets screens with a width greater than or equal to a specified value.
    - **max-height** and **min-height**: Similar to width conditions but apply to the height of the viewport.

2. **Orientation**
    - **orientation: landscape**: Applies styles when the device is in landscape mode (wider than it is tall).
    - **orientation: portrait**: Applies styles when the device is in portrait mode (taller than it is wide).

3. **Resolution**
    - **min-resolution** and **max-resolution**: Allow you to target devices with specific resolutions, such as Retina displays on Apple devices.

4. **Aspect Ratio**
    - **aspect-ratio**: Sets styles based on the ratio between width and height of the screen.

5. **Other Conditions**
    - **prefers-color-scheme**: Checks if the user prefers a light or dark color scheme.
    - **hover**: Determines if the user’s device can detect hovering (useful for touchscreen devices).

---

## Combining Conditions

You can combine multiple conditions within a single media query using **logical operators**:

- **and**: All conditions must be met.
- **or** (comma): Only one of the conditions must be met.
- **not**: Negates a condition.

For example, to apply styles only if the screen width is between 600px and 900px, you can use:

```css
@media (min-width: 600px) and (max-width: 900px) {
    /* CSS rules for screens between 600px and 900px */
}
```

---

## Practical Examples of Media Queries

### 1. Responsive Navigation Menu

A media query can hide the regular navigation menu on smaller screens and display a hamburger menu instead.

```css
/* Default styles for desktop */
.navbar {
    display: flex;
    justify-content: space-around;
}

/* Hide navbar on smaller screens and show mobile menu */
@media (max-width: 768px) {
    .navbar {
        display: none;
    }
    .mobile-menu {
        display: block;
    }
}
```

---

### 2. Changing Font Size Based on Screen Width

Adjusting font sizes based on screen width can improve readability across different devices:

```css
body {
    font-size: 18px;
}

@media (max-width: 768px) {
    body {
        font-size: 16px;
    }
}

@media (max-width: 480px) {
    body {
        font-size: 14px;
    }
}
```

In this example, the font size decreases as the screen width becomes smaller, improving readability on mobile devices.

---

### 3. Grid Layout Adjustments

You can use media queries to adjust grid layouts for smaller screens, moving from multiple columns to a single-column layout.

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}

/* Change to a two-column layout on medium screens */
@media (max-width: 992px) {
    .grid-container {
        grid-template-columns: repeat(2, 1fr);
    }
}

/* Change to a single-column layout on small screens */
@media (max-width: 600px) {
    .grid-container {
        grid-template-columns: 1fr;
    }
}
```

Here, the layout changes from a three-column layout on large screens to two columns on medium screens and finally to a single column on small screens.

---

## Using Media Queries for Dark Mode

Dark mode has become a popular feature, and media queries can help detect a user’s color scheme preference. The `prefers-color-scheme` condition can be used to apply dark mode styles when the user’s device is set to a dark theme:

```css
/* Default (light mode) styles */
body {
    background-color: white;
    color: black;
}

/* Dark mode styles */
@media (prefers-color-scheme: dark) {
    body {
        background-color: black;
        color: white;
    }
}
```

This media query checks if the user has enabled dark mode on their device and automatically applies dark-themed styles.

---

## Best Practices for Using Media Queries

1. **Mobile-First Approach**: Start with styles for the smallest screens and add media queries for larger screens. This approach usually makes the CSS more efficient and simpler.
2. **Use Relative Units**: Use `em` or `rem` units for font sizes, margins, and padding to make scaling easier.
3. **Optimize for Performance**: Only add media queries when necessary to avoid cluttered and inefficient CSS.
4. **Test on Multiple Devices**: Test your media queries on different screen sizes and orientations to ensure the design is responsive.

---

## Conclusion

Media queries are a powerful tool that enables developers to create responsive websites that look and function well on various devices. By adjusting styles based on screen size, orientation, resolution, and other device characteristics, you can ensure a great user experience regardless of the device your visitors are using.

From responsive navigation menus to dark mode, media queries make it possible to create websites that dynamically adjust to meet user needs. Start experimenting with media queries in your CSS to take your responsive design skills to the next level!