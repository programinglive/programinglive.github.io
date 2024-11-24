---
title: What is XHR?
layout: default
parent: JavaScript
grand_parent: Web Development
description: "What is XHR?"
---

# What is XHR (XMLHttpRequest)?

**XMLHttpRequest** (XHR) is an API in JavaScript that allows web pages to make asynchronous HTTP requests to a server
and receive data without reloading the entire page. This is a fundamental feature of **AJAX** (Asynchronous JavaScript
and XML), enabling the development of more dynamic, responsive web applications.

---

## Table of Contents

- [What is XHR?](#what-is-xhr)
- [How XHR Works](#how-xhr-works)
- [Creating an XHR Request](#creating-an-xhr-request)
- [XHR Methods and Properties](#xhr-methods-and-properties)
- [XHR Example: Simple Request](#xhr-example-simple-request)
- [When to Use XHR](#when-to-use-xhr)
- [XHR vs Fetch API](#xhr-vs-fetch-api)
- [Conclusion](#conclusion)

---

## What is XHR?

XMLHttpRequest (XHR) is an object used to create and send HTTP requests from a client to a server asynchronously. It
allows web applications to fetch data from a server or send data to a server without needing to reload the entire web
page. XHR was originally designed to fetch XML data, but it can handle various types of data formats, such as JSON,
HTML, or plain text.

---

## How XHR Works

The `XMLHttpRequest` object works by sending HTTP requests to the server in the background, receiving the response, and
then processing it without needing to reload the page. This allows for the dynamic updating of a webpage's content.

### Key Steps in XHR Workflow:

1. **Create an XMLHttpRequest object**: This object is used to send requests to the server.
2. **Set up the request**: Define the type of request (e.g., GET, POST), the target URL, and other parameters.
3. **Send the request**: Call the `send()` method to send the request to the server.
4. **Handle the response**: When the server responds, use event handlers or callback functions to process the response
   and update the webpage.

---

## Creating an XHR Request

### Basic Syntax:

```javascript
let xhr = new XMLHttpRequest();  // Create a new XMLHttpRequest object
xhr.open('GET', 'https://api.example.com/data', true);  // Initialize the request
xhr.onreadystatechange = function () {
	if (xhr.readyState === 4 && xhr.status === 200) {  // Check if the request is complete and successful
		let response = xhr.responseText;  // Get the response text
		console.log(response);  // Process the response
	}
};
xhr.send();  // Send the request
```

### `open()` Method

The `open()` method is used to configure the request. It requires three arguments:

- **Method**: The HTTP method (e.g., GET, POST).
- **URL**: The URL to which the request is sent.
- **Asynchronous**: A boolean value (`true` for asynchronous requests, `false` for synchronous).

### `send()` Method

The `send()` method sends the request to the server. If you're making a GET request, this method is called with no
arguments. For POST requests, you can include data in the body of the request.

---

## XHR Methods and Properties

### Methods:

- **open(method, url, async, user, password)**: Initializes the request.
- **send(data)**: Sends the request to the server.
- **setRequestHeader(header, value)**: Sets the value of an HTTP request header.

### Properties:

- **readyState**: Holds the current state of the request (0–4).
- **status**: The HTTP status code returned by the server (e.g., 200 for success).
- **responseText**: Contains the response data in text format.
- **responseXML**: Contains the response data as an XML document (if applicable).

### Example of `setRequestHeader()`:

```javascript
xhr.setRequestHeader("Content-Type", "application/json");  // Set headers for POST requests
```

---

## XHR Example: Simple Request

```javascript
let xhr = new XMLHttpRequest();
xhr.open('GET', 'https://jsonplaceholder.typicode.com/posts/1', true);

xhr.onreadystatechange = function () {
	if (xhr.readyState === 4 && xhr.status === 200) {
		let post = JSON.parse(xhr.responseText);  // Parse JSON response
		document.getElementById('post-title').innerText = post.title;
		document.getElementById('post-body').innerText = post.body;
	}
};

xhr.send();
```

In this example, an XHR request is sent to fetch a post from the JSONPlaceholder API. The response is parsed as JSON,
and the page content is dynamically updated.

---

## When to Use XHR

- **Asynchronous requests**: XHR is useful when you need to send data to or receive data from a server without blocking
  the user interface (UI).
- **Dynamic content updates**: It’s commonly used in web applications to fetch new data or submit data to a server
  without reloading the page.
- **Legacy support**: Although `fetch()` is the modern alternative, XHR is still widely used in legacy applications and
  older browsers.

---

## XHR vs Fetch API

While `XMLHttpRequest` has been around for a long time, the newer **Fetch API** offers a more modern and flexible
approach to making asynchronous requests. Some of the key differences between XHR and Fetch include:

- **Syntax**: The Fetch API uses Promises, which makes it easier to work with asynchronous operations.
- **Return Value**: `XMLHttpRequest` returns a raw response, while the `fetch()` API returns a `Response` object, which
  can be used to handle different data formats like JSON or text.
- **Error Handling**: Fetch simplifies error handling with better support for catching and chaining errors.

### Example Comparison:

#### XHR Example:

```javascript
let xhr = new XMLHttpRequest();
xhr.open('GET', '/data', true);
xhr.onreadystatechange = function () {
	if (xhr.readyState === 4 && xhr.status === 200) {
		console.log(xhr.responseText);
	}
};
xhr.send();
```

#### Fetch Example:

```javascript
fetch('/data')
	.then(response => response.json())
	.then(data => console.log(data))
	.catch(error => console.error('Error:', error));
```

---

## Conclusion

**XMLHttpRequest (XHR)** is a fundamental technology that enables web pages to send and receive data asynchronously. It
is the core of the **AJAX** technique, allowing for dynamic and interactive web applications. Although `XMLHttpRequest`
is still widely used, the **Fetch API** has become the preferred modern solution due to its simplicity and promise-based
syntax. Regardless, understanding XHR is important for working with legacy code and improving your overall understanding
of web development.