---
title: Understanding Scrollbar in CSS
layout: default
parent: CSS
grand_parent: Web Development
nav_order: 1
description: "Understanding Scrollbar in CSS"
---

# Understanding Scrollbar in CSS

A scrollbar is an essential UI element that allows users to scroll through content that exceeds the visible area of a
container. In web development, CSS provides several ways to control the appearance and behavior of scrollbars.
Understanding how to manipulate scrollbars can significantly improve the user experience, especially when dealing with
long content or dynamic page layouts.

<a href="https://codepen.io/moszes/pen/PovEYGZ" target="_blank" style="text-decoration: none;">
<button style="background: none; border: none; cursor: pointer;">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-external-link"><title>External Link</title><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V13"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
</button>
<span style="margin-left: 5px;">Open in CodePen</span>
</a>

---

## Table of Contents

- [What is a Scrollbar in CSS?](#what-is-a-scrollbar-in-css)
- [Default Scrollbar Behavior](#default-scrollbar-behavior)
- [Customizing Scrollbar with CSS](#customizing-scrollbar-with-css)
    - [::-webkit-scrollbar](#webkit-scrollbar)
    - [::-webkit-scrollbar-thumb](#webkit-scrollbar-thumb)
    - [::-webkit-scrollbar-track](#webkit-scrollbar-track)
    - [::-webkit-scrollbar-button](#webkit-scrollbar-button)
- [Cross-Browser Compatibility](#cross-browser-compatibility)
- [When to Use Custom Scrollbars](#when-to-use-custom-scrollbars)
- [Best Practices for Scrollbar Design](#best-practices-for-scrollbar-design)
- [Conclusion](#conclusion)

---

## What is a Scrollbar in CSS?

A scrollbar is a graphical control element used to navigate through content that doesn't fit in the container's
viewport. It is usually displayed when the content overflows the boundaries of the container, either horizontally or
vertically. CSS allows developers to control both the appearance and behavior of scrollbars within elements.

---

## Default Scrollbar Behavior

By default, a scrollbar appears automatically when the content inside a container exceeds its size. The behavior can be
influenced by the following properties:

- **`overflow`**: Controls when scrollbars appear.
    - `overflow: auto;` - Displays a scrollbar when the content overflows the container.
    - `overflow: scroll;` - Always shows the scrollbar, whether needed or not.
    - `overflow: hidden;` - Hides the scrollbar and prevents scrolling.
    - `overflow-x` / `overflow-y` - Controls horizontal and vertical overflow separately.

Example:

```css
.container {
    width: 300px;
    height: 200px;
    overflow: auto; /* Adds scrollbar when content overflows */
}
```

---

## Customizing Scrollbar with CSS

With modern browsers, you can customize the appearance of scrollbars to match the design of your website. The
customization is achieved using pseudo-elements and properties targeting the `::-webkit-scrollbar` and related
selectors. These are supported in most webkit-based browsers like Chrome, Safari, and newer versions of Edge.

### webkit-scrollbar

This pseudo-element is used to target the scrollbar itself.

```css
/* Custom scrollbar width */
::-webkit-scrollbar {
    width: 12px; /* Vertical scrollbar */
    height: 12px; /* Horizontal scrollbar */
}
```

### webkit-scrollbar-thumb

The thumb is the draggable part of the scrollbar. It allows users to scroll the content by dragging the thumb.

```css
/* Custom thumb appearance */
::-webkit-scrollbar-thumb {
    background-color: #888;
    border-radius: 10px;
    border: 3px solid #fff;
}
```

### webkit-scrollbar-track

The track is the background area of the scrollbar where the thumb slides. It can be customized to match the overall
design.

```css
/* Custom track appearance */
::-webkit-scrollbar-track {
    background-color: #f1f1f1;
    border-radius: 10px;
}
```

### webkit-scrollbar-button

Scrollbar buttons are the arrows at the top and bottom of vertical scrollbars or left and right on horizontal
scrollbars. These are rarely used in modern design, but they can still be styled.

```css
/* Custom button appearance */
::-webkit-scrollbar-button {
    background-color: #f1f1f1;
    display: block;
    height: 20px;
    width: 20px;
}
```

---

## Cross-Browser Compatibility

Customizing scrollbars with CSS is mainly supported by browsers that use the WebKit engine, such as Chrome, Safari, and
newer versions of Microsoft Edge. Firefox supports scrollbar styling, but it uses a different approach:

### Firefox:

Firefox uses the `scrollbar-width` and `scrollbar-color` properties to customize scrollbars.

```css
/* Customizing scrollbar in Firefox */
scrollbar-width: thin

; /* Options: auto, thin, none */
scrollbar-color: #888 #f1f1f1

; /* thumb and track colors */
```

For full cross-browser compatibility, you may need to apply a combination of `::-webkit-scrollbar` for WebKit browsers
and `scrollbar-*` properties for Firefox.

---

## When to Use Custom Scrollbars

Custom scrollbars are particularly useful when you want to match the design of your site or improve the user experience
in specific use cases, such as:

- **Minimalist Design**: Hiding or reducing the prominence of scrollbars for cleaner layouts.
- **Branding**: Matching scrollbars to the color scheme or style of your website.
- **Mobile Experiences**: Creating responsive, touch-friendly scrollbars.

However, it's important not to overdo it, as non-standard scrollbars can confuse users if they’re not familiar with how
they function.

---

## Best Practices for Scrollbar Design

- **Visibility**: Ensure that custom scrollbars remain visible when needed, and don't obscure important content.
- **Accessibility**: Provide enough contrast between the scrollbar and the background for easy visibility. Also,
  consider adding hover states to improve interaction.
- **Performance**: Avoid excessive customization that could lead to performance issues, especially on devices with lower
  processing power.
- **Consistency**: Maintain consistency across your design. If you customize one scrollbar, consider doing so across the
  entire site.

---

## Conclusion

Scrollbars are a fundamental part of web design that allows users to navigate through content. By understanding how to
manipulate them with CSS, you can enhance the user experience and create visually appealing, functional interfaces.
Customizing scrollbars should be done thoughtfully to ensure they don’t disrupt usability and are compatible across
different browsers and devices. By using the appropriate properties, you can tailor scrollbars to fit seamlessly into
your website's design.