---
layout: default
title: What is HTTP Response?
parent: Software Development
grand_parent: FAQ
description: "What is HTTP Response?"
---

# What is WebSocket?

WebSocket is a communication protocol that provides full-duplex, real-time communication between a client and a server
over a single persistent connection. Unlike traditional HTTP, where a request-response model is used, WebSocket allows
for bi-directional data exchange without the need to repeatedly open and close connections.

---

## Table of Contents

- [Key Features of WebSocket](#key-features-of-websocket)
- [How Does WebSocket Work?](#how-does-websocket-work)
- [Advantages of WebSocket](#advantages-of-websocket)
- [Common Use Cases for WebSocket](#common-use-cases-for-websocket)
- [WebSocket vs HTTP](#websocket-vs-http)
- [Implementing WebSocket](#implementing-websocket)
    - [Example: Using WebSocket in Node.js](#example-using-websocket-in-nodejs)
- [Conclusion](#conclusion)

---

## Key Features of WebSocket

- **Full-Duplex Communication**: Both client and server can send and receive messages simultaneously.
- **Persistent Connection**: Reduces overhead by maintaining a continuous connection instead of creating new ones for
  each interaction.
- **Low Latency**: Enables faster communication, ideal for real-time applications.
- **Lightweight Protocol**: Uses a small amount of data for communication, making it efficient.

---

## How Does WebSocket Work?

1. **Handshake**:  
   WebSocket begins with an HTTP request to establish a connection. The client sends an upgrade request, and if the
   server supports WebSocket, the connection is upgraded.

   Example HTTP upgrade request:

   ```http
   GET /chat HTTP/1.1
   Host: example.com
   Upgrade: websocket
   Connection: Upgrade
   Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
   Sec-WebSocket-Version: 13
   ```

2. **Open Connection**:  
   After a successful handshake, the connection remains open. Both the server and client can now exchange messages
   without the need for additional handshakes.

3. **Message Exchange**:  
   Messages can be sent in text or binary format, depending on the application's requirements.

4. **Connection Close**:  
   Either the client or server can close the connection by sending a close frame.

---

## Advantages of WebSocket

- **Efficient Communication**: Reduces latency and overhead compared to traditional HTTP.
- **Real-Time Applications**: Ideal for chat apps, live notifications, gaming, financial tickers, and collaborative
  tools.
- **Event-Driven Architecture**: Makes it easier to handle asynchronous data updates.

---

## Common Use Cases for WebSocket

1. **Chat Applications**: Real-time text, audio, or video messaging.
2. **Live Notifications**: Push notifications for updates like stock prices or sports scores.
3. **Collaborative Tools**: Real-time editing in apps like Google Docs.
4. **Gaming**: Multiplayer games where low latency is critical.
5. **IoT (Internet of Things)**: Communication between connected devices.

---

## WebSocket vs HTTP

| Feature    | WebSocket              | HTTP                               |  
|------------|------------------------|------------------------------------|  
| Connection | Persistent             | Stateless (new request per action) |  
| Data Flow  | Bi-Directional         | Request-Response                   |  
| Latency    | Low                    | Higher due to repeated handshakes  |  
| Use Case   | Real-Time Applications | Traditional web applications       |  

---

## Implementing WebSocket

### Example: Using WebSocket in Node.js

**Server-Side**:

```javascript
const WebSocket = require('ws');
const wss = new WebSocket.Server({port: 8080});

wss.on('connection', (ws) => {
	console.log('New client connected');
	ws.on('message', (message) => {
		console.log(`Received: ${message}`);
		ws.send(`Hello, you sent -> ${message}`);
	});
	ws.on('close', () => console.log('Client disconnected'));
});
```

**Client-Side**:

```javascript
const socket = new WebSocket('ws://localhost:8080');

socket.onopen = () => {
	console.log('Connected to the server');
	socket.send('Hello Server!');
};

socket.onmessage = (event) => {
	console.log(`Message from server: ${event.data}`);
};

socket.onclose = () => console.log('Connection closed');
```

---

## Conclusion

WebSocket is a game-changer for building interactive and dynamic web applications. Its ability to maintain a persistent
connection and facilitate low-latency, full-duplex communication makes it the backbone of real-time applications. As you
integrate WebSocket into your projects, you'll unlock the power of real-time user experiences.  