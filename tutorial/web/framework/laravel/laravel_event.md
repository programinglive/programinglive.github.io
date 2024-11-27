---
title: Laravel Events
layout: default
parent: Framework
grand_parent: Web Development
description: "Laravel Events"
---

# Laravel Events

## Table of Contents

* [Introduction](#introduction)
* [Why Use Events?](#why-use-events)
* [Key Concepts](#key-concepts)
* [Creating and Dispatching Events](#creating-and-dispatching-events)
* [Listening for Events](#listening-for-events)
* [Event Subscribers](#event-subscribers)
* [Queueable Events](#queueable-events)
* [Broadcasting Events](#broadcasting-events)
* [Event Discovery](#event-discovery)
* [Conclusion](#conclusion)

## Introduction

Events are a powerful feature in Laravel that allow you to create decoupled and maintainable applications. They provide
a way for different parts of your application to communicate with each other without being directly dependent on one
another. Essentially, events are actions or occurrences that happen within your application, and listeners are the
components that react to those occurrences.

## Why Use Events?

* **Decoupling:** Events promote a loosely coupled architecture, making your code more flexible and easier to maintain.
  Components can react to events without knowing the specifics of the component that triggered the event.
* **Extensibility:** Events provide a simple way to extend your application's functionality. You can easily add new
  features by creating listeners for existing events without modifying the core application logic.
* **Code Organization:** Events help organize your code by separating concerns. Instead of having large, monolithic
  classes, you can break down your logic into smaller, more manageable pieces.
* **Testability:**  Events make testing easier. You can isolate and test individual listeners without needing to
  simulate the entire application flow.

## Key Concepts

* **Event:** An event represents a specific action or occurrence within your application.
* **Listener:** A listener is a class that contains the logic to be executed when a specific event is dispatched.
* **Dispatcher:** The event dispatcher is responsible for managing the registration of listeners and dispatching events
  to the appropriate listeners.

## Creating and Dispatching Events

1. **Create an Event Class:**  Use the `php artisan make:event <EventName>` command to generate an event class. This
   class can hold any data related to the event.
2. **Dispatch the Event:** Use the `event()` helper function or the `Event` facade to dispatch the event. For
   example: `event(new NewOrderPlaced($order));`

## Listening for Events

1. **Create a Listener Class:** Use the `php artisan make:listener <ListenerName> --event=<EventName>` command to
   generate a listener class.
2. **Implement the `handle` method:** This method will contain the logic to be executed when the event is received.
3. **Register the Listener:**  Register the listener in the `EventServiceProvider`'s `$listen` array.

## Event Subscribers

Subscribers provide a more convenient way to register multiple listeners for a single class. They allow you to define
a `subscribe` method that returns an array of event-listener mappings.

## Queueable Events

You can queue the execution of event listeners using the `ShouldQueue` interface. This is useful for long-running tasks
that you don't want to block the main request.

## Broadcasting Events

Laravel allows you to broadcast events over websockets, enabling real-time updates in your application. This is often
used for features like notifications and chat applications.

## Event Discovery

Laravel can automatically discover and register your events and listeners. This simplifies the process of registering
listeners and reduces boilerplate code.

## Conclusion

Laravel Events are a fundamental building block for creating well-structured, maintainable, and extensible applications.
By decoupling different parts of your application, events promote cleaner code, easier testing, and greater flexibility.
Understanding and utilizing events effectively is crucial for any Laravel developer.
