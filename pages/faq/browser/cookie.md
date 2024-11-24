---
layout: default
title: Cookies in Web Development
parent: Browser
grand_parent: FAQ
description: "Cookies in Web Development"
---

# Cookies in Web Development

In web development, **cookies** are small pieces of data that are stored by a web browser on the user's device. They are
primarily used for maintaining stateful information across multiple requests or sessions. Cookies are an essential part
of web development and play a vital role in user authentication, personalization, and tracking.

---

## Table of Contents

- [What is a Cookie?](#what-is-a-cookie)
- [Types of Cookies](#types-of-cookies)
- [How Cookies Work](#how-cookies-work)
- [Setting Cookies in PHP](#setting-cookies-in-php)
- [Accessing Cookies in PHP](#accessing-cookies-in-php)
- [Cookie Expiration](#cookie-expiration)
- [Cookie Security](#cookie-security)
- [Common Use Cases of Cookies](#common-use-cases-of-cookies)
- [Conclusion](#conclusion)

---

## What is a Cookie?

A **cookie** is a small text file that is stored by a web browser on the user's computer or device. Cookies can store
various pieces of data, such as user preferences, login credentials, session information, and tracking information.

Cookies are set by the web server and sent to the user's browser, which stores them locally. On subsequent requests, the
browser sends the cookie data back to the server, allowing the server to recognize the user or maintain state between
different requests.

---

## Types of Cookies

### 1. **Session Cookies**

Session cookies are temporary cookies that are deleted when the user closes their web browser. They are typically used
for session management, such as maintaining a user's login state or keeping track of items in a shopping cart.

### 2. **Persistent Cookies**

Persistent cookies remain on the user's device for a specified period, even after the browser is closed. These cookies
are used to remember user preferences, language settings, or login credentials across multiple sessions.

### 3. **Secure Cookies**

Secure cookies are only sent over secure HTTPS connections. These cookies are used for storing sensitive data, such as
authentication tokens, to ensure they are transmitted securely.

### 4. **HttpOnly Cookies**

Cookies marked as **HttpOnly** are not accessible via JavaScript. This provides an extra layer of security against
Cross-Site Scripting (XSS) attacks since these cookies cannot be manipulated by client-side scripts.

### 5. **SameSite Cookies**

The **SameSite** attribute allows a cookie to be sent only with requests originating from the same domain that set the
cookie. This helps prevent Cross-Site Request Forgery (CSRF) attacks. There are three types:

- **Strict**: Cookies are sent only for same-site requests.
- **Lax**: Cookies are sent for same-site requests and some cross-site requests.
- **None**: Cookies are sent for all requests, but only if the `Secure` flag is also set.

---

## How Cookies Work

1. **Setting a Cookie**: When a user visits a website, the server sends an HTTP response with a `Set-Cookie` header,
   containing the cookie's name, value, and other attributes like expiration, domain, and path.

2. **Storing the Cookie**: The browser stores the cookie on the user's device based on the information provided in
   the `Set-Cookie` header.

3. **Sending the Cookie**: On subsequent requests to the same domain, the browser automatically sends the cookie back to
   the server with the HTTP request in the `Cookie` header.

4. **Cookie Retrieval**: The server can retrieve the cookie data from the `Cookie` header and use it to personalize the
   user experience or maintain state between requests.

---

## Setting Cookies in PHP

In PHP, cookies are set using the `setcookie()` function. This function must be called before any output is sent to the
browser (i.e., before the HTML starts to render).

### Example of Setting a Cookie in PHP:

```php
<?php
// Set a cookie that expires in 1 hour
setcookie("user", "John Doe", time() + 3600, "/"); // cookie name, value, expiration, path

echo "Cookie has been set!";
?>
```

This will set a cookie named `user` with the value `John Doe` that expires in 1 hour and is available across the entire
website (`/`).

### Cookie Attributes:

- **name**: The name of the cookie.
- **value**: The value stored in the cookie.
- **expiration**: The time when the cookie expires. It is specified in seconds since the Unix epoch. If not set, the
  cookie expires when the browser session ends.
- **path**: The path on the server where the cookie is available. The default is the directory of the calling script.
- **domain**: The domain for which the cookie is valid. By default, the cookie is available only to the domain that set
  it.
- **secure**: If true, the cookie is only sent over HTTPS connections.
- **httponly**: If true, the cookie is not accessible via JavaScript.

---

## Accessing Cookies in PHP

To access a cookie in PHP, you use the global `$_COOKIE` array. This array contains all the cookies sent by the browser
to the server.

### Example of Accessing a Cookie in PHP:

```php
<?php
if(isset($_COOKIE["user"])) {
    echo "Hello, " . $_COOKIE["user"];
} else {
    echo "Cookie not set!";
}
?>
```

This script checks if the `user` cookie is set and, if it is, displays its value.

---

## Cookie Expiration

Cookies can either be **session cookies** or **persistent cookies**.

- **Session Cookies**: These are deleted when the browser is closed. You don't need to specify an expiration time for
  session cookies.
- **Persistent Cookies**: These remain on the user's device for a specified duration. To set the expiration of a
  persistent cookie, you use the `time()` function in PHP, which returns the current time in seconds since the Unix
  epoch.

For example, to create a persistent cookie that expires in 30 days:

```php
setcookie("user", "John Doe", time() + (30 * 24 * 60 * 60), "/");
```

This sets the cookie `user` to expire in 30 days from the current time.

---

## Cookie Security

Cookies can contain sensitive information, so it is important to implement security measures:

### 1. **Use the `Secure` Flag**

When setting cookies, use the `Secure` flag to ensure that cookies are only sent over HTTPS connections. This prevents
cookies from being transmitted over unencrypted connections.

Example:

```php
setcookie("user", "John Doe", time() + 3600, "/", "", true, true); // Secure and HttpOnly flags set
```

### 2. **Use the `HttpOnly` Flag**

The `HttpOnly` flag helps protect cookies from being accessed via JavaScript. This is especially important for
authentication cookies.

Example:

```php
setcookie("auth_token", "xyz123", time() + 3600, "/", "", true, true);
```

### 3. **SameSite Cookies**

Set the `SameSite` attribute to protect against Cross-Site Request Forgery (CSRF) attacks.

Example:

```php
setcookie("user", "John Doe", time() + 3600, "/", "", true, true, [
    'samesite' => 'Strict'
]);
```

---

## Common Use Cases of Cookies

### 1. **User Authentication**

Cookies are often used to store session identifiers for logged-in users. This allows users to stay logged in across
different pages or visits without having to re-enter their credentials.

### 2. **User Preferences**

Cookies are used to remember user preferences such as language settings, theme selection, and display options.

### 3. **Shopping Cart Information**

E-commerce websites use cookies to store information about a user's shopping cart, allowing them to retain the items
even after navigating away from the site.

### 4. **Tracking and Analytics**

Cookies are widely used for tracking user activity and behavior on websites for analytics purposes. Google Analytics,
for example, uses cookies to gather data about user interactions.

---

## Conclusion

Cookies are a powerful tool in web development, allowing websites to maintain state and remember user preferences. They
are integral to features like user authentication, session management, and personalized experiences. However, cookies
must be used securely to avoid potential vulnerabilities, such as **Cross-Site Scripting (XSS)** and **Cross-Site
Request Forgery (CSRF)**. By using the appropriate attributes (e.g., `Secure`, `HttpOnly`, `SameSite`), cookies can be
kept secure while still providing a rich and dynamic user experience.