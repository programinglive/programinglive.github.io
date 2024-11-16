---
title: What is XHR?
layout: default
parent: JavaScript
grand_parent: Web Development
description: "What is XHR?"
---

# What is XHR?

XHR, or **XMLHttpRequest**, is a JavaScript API that allows web developers to interact with servers asynchronously. Introduced in the early 2000s, XHR revolutionized the way web applications were built, enabling the rise of dynamic, responsive web pages. Let’s break down what XHR is and why it’s essential in modern web development.

---

## Understanding XHR
XMLHttpRequest is a built-in browser object that lets you send HTTP or HTTPS requests to a server and process the response without reloading the web page. This ability is at the core of **AJAX (Asynchronous JavaScript and XML)**, a technique used to create seamless user experiences.

While the term includes "XML," you can send and receive other data formats like **JSON**, **HTML**, and plain text, making it versatile for many use cases.

---

## How XHR Works
The XHR workflow can be summarized in these steps:
1. **Create an XHR Object**  
   Use `new XMLHttpRequest()` to create an XHR instance.
2. **Configure the Request**  
   Specify the HTTP method (`GET`, `POST`, etc.) and the URL endpoint using `xhr.open()`.
3. **Send the Request**  
   Call `xhr.send()` with or without data, depending on the request type.
4. **Handle the Response**  
   Listen for the `onreadystatechange` event or the newer `load` event to process the response.

---

## Example of XHR in Action

Here’s a simple example of using XHR to fetch data:

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true); // true for asynchronous
xhr.onload = function () {
  if (xhr.status === 200) {
    console.log('Response:', JSON.parse(xhr.responseText));
  } else {
    console.error('Error:', xhr.statusText);
  }
};
xhr.onerror = function () {
  console.error('Network Error');
};
xhr.send();
```

In this example:
- A `GET` request is sent to `https://api.example.com/data`.
- When the server responds, the data is logged or an error message is displayed.

---

## Advantages of XHR
- **Asynchronous Communication**: Allows parts of a web page to update without refreshing the whole page.
- **Wide Support**: Works across most modern browsers.
- **Flexible Data Formats**: Supports JSON, XML, text, and more.

---

## Limitations of XHR
While powerful, XHR is considered somewhat outdated due to newer alternatives like **Fetch API** and **Axios**. These newer tools provide simpler syntax and better error handling, reducing the boilerplate code often required with XHR.

For example, the same `GET` request using Fetch API looks like this:
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log('Response:', data))
  .catch(error => console.error('Error:', error));
```

---

## When to Use XHR
In most modern projects, XHR is rarely the first choice due to its verbosity. However, it might still be relevant in:
- Legacy systems requiring backward compatibility.
- Environments where the Fetch API or libraries like Axios are unavailable.

---

## Conclusion
XMLHttpRequest paved the way for the interactive web we enjoy today. While newer tools like Fetch and Axios have largely replaced it, understanding XHR helps developers appreciate the evolution of web technologies and troubleshoot legacy codebases. Whether you use XHR directly or prefer modern alternatives, its impact on web development remains undeniable.