---
title: Laravel Echo
layout: default
parent: Framework
grand_parent: Web Development
description: "Laravel Echo"
---

# Laravel Echo

Building modern web applications often requires real-time features like notifications, live updates, and chats. Laravel
Echo makes it easy to integrate these capabilities seamlessly into your Laravel projects. In this article, we'll explore
Laravel Echo in detail, providing a step-by-step guide to its setup and usage.

---

## Table of Contents

- [What is Laravel Echo?](#what-is-laravel-echo)
- [Why Use Laravel Echo?](#why-use-laravel-echo)
- [Setting Up Laravel Echo](#setting-up-laravel-echo)
    - [Installing Laravel Echo](#installing-laravel-echo)
    - [Configuring Broadcasting in Laravel](#configuring-broadcasting-in-laravel)
    - [Choosing a Broadcaster](#choosing-a-broadcaster)
- [Using Laravel Echo](#using-laravel-echo)
    - [Listening for Events](#listening-for-events)
    - [Broadcasting Events](#broadcasting-events)
    - [Secure Channels](#secure-channels)
- [Examples of Real-Time Features](#examples-of-real-time-features)
- [Common Issues and Debugging Tips](#common-issues-and-debugging-tips)
- [Conclusion](#conclusion)

---

## What is Laravel Echo?

Laravel Echo is a JavaScript library that simplifies real-time event broadcasting in Laravel applications. It works
alongside Laravel's broadcasting feature to listen for events on the client side. Whether you're building a live
dashboard, chat app, or real-time notification system, Laravel Echo is your go-to solution.

Supported broadcasters include:

- **Pusher**: A managed WebSocket service.
- **Laravel WebSockets**: A self-hosted alternative to Pusher.
- **Socket.IO**: A widely-used real-time library.

---

## Why Use Laravel Echo?

Here are the top reasons to integrate Laravel Echo into your projects:

- **Simplified Real-Time Features**: It provides a clean API to manage real-time events.
- **Flexible Broadcasters**: Compatible with multiple broadcasting services, giving you flexibility.
- **Secure Communication**: Supports private and presence channels with authentication.
- **Improved User Experience**: Enables dynamic updates without page reloads.

---

## Setting Up Laravel Echo

### Installing Laravel Echo

To install Laravel Echo, first ensure your Laravel application is set up with the broadcasting feature. Then, install
Laravel Echo and its dependencies on the front end:

```bash
npm install --save laravel-echo pusher-js
```

If you're using Laravel WebSockets, install the required server package as well:

```bash
composer require beyondcode/laravel-websockets
```

### Configuring Broadcasting in Laravel

Update your `.env` file to set the desired broadcaster:

```env
BROADCAST_DRIVER=pusher
```

Then, configure the `config/broadcasting.php` file:

```php
'connections' => [
    'pusher' => [
        'driver' => 'pusher',
        'key' => env('PUSHER_APP_KEY'),
        'secret' => env('PUSHER_APP_SECRET'),
        'app_id' => env('PUSHER_APP_ID'),
        'options' => [
            'cluster' => env('PUSHER_APP_CLUSTER'),
            'useTLS' => true,
        ],
    ],
],
```

Finally, run the following command to enable broadcasting:

```bash
php artisan queue:work
```

### Choosing a Broadcaster

Laravel Echo works with multiple broadcasters:

- **Pusher**: Ideal for quick setups and scalability.
- **Laravel WebSockets**: Best for cost-saving self-hosted solutions.
- **Socket.IO**: Preferred if you already use Socket.IO in your stack.

---

## Using Laravel Echo

### Listening for Events

To listen for events on the client side, initialize Laravel Echo in your JavaScript file:

```javascript
import Echo from "laravel-echo";
import Pusher from "pusher-js";

window.Echo = new Echo({
	broadcaster: "pusher",
	key: process.env.MIX_PUSHER_APP_KEY,
	cluster: process.env.MIX_PUSHER_APP_CLUSTER,
	encrypted: true,
});
```

Now, you can subscribe to channels and listen for events:

```javascript
Echo.channel('orders')
	.listen('OrderShipped', (e) => {
		console.log(e.order);
	});
```

### Broadcasting Events

On the server side, create an event and broadcast it:

```php
php artisan make:event OrderShipped
```

In the event class, implement the `ShouldBroadcast` interface:

```php
use Illuminate\Contracts\Broadcasting\ShouldBroadcast;

class OrderShipped implements ShouldBroadcast {
    public $order;

    public function __construct($order) {
        $this->order = $order;
    }

    public function broadcastOn() {
        return ['orders'];
    }
}
```

Dispatch the event wherever necessary:

```php
event(new OrderShipped($order));
```

### Secure Channels

Laravel Echo supports two types of secure channels:

- **Private Channels**: Restrict access to authenticated users.
- **Presence Channels**: Allow user-specific data and track active users.

For private channels, define an authorization route in `routes/channels.php`:

```php
Broadcast::channel('orders.{userId}', function ($user, $userId) {
    return $user->id === (int) $userId;
});
```

---

## Examples of Real-Time Features

### Notifications

Broadcast notifications to users:

```php
Notification::send($user, new OrderShippedNotification($order));
```

### Live Dashboard Updates

Display real-time metrics by broadcasting data to a dashboard channel:

```php
Echo.channel('dashboard')
    .listen('MetricsUpdated', (e) => {
        updateDashboard(e.metrics);
    });
```

---

## Common Issues and Debugging Tips

- **Authentication Errors**: Ensure your Laravel app's broadcasting and Echo configurations match.
- **Connection Problems**: Verify that your WebSocket server or Pusher credentials are correct.
- **CORS Issues**: Add appropriate CORS headers to your Laravel application.

---

## Conclusion

Laravel Echo brings real-time interactivity to your web applications, enhancing user experience with features like
notifications, chat, and live updates. By following this guide, you can quickly set up Laravel Echo and start building
dynamic and responsive applications.

Real-time functionality has become a key component of modern web development, and Laravel Echo makes it simpler than
ever to implement.