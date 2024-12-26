---
layout: default
title: Slot In Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Slot In Laravel"
---

# What is Slot in Laravel Component

## Table of Contents

* [Introduction to Slots](#introduction-to-slots)
* [Basic Slot Usage](#basic-slot-usage)
* [Named Slots](#named-slots)
* [Default Slot Content](#default-slot-content)
* [Slot Attributes](#slot-attributes)
* [Conditional Slot Rendering](#conditional-slot-rendering)
* [Slot Scoping](#slot-scoping)
* [Practical Examples](#practical-examples)
* [Common Slot Patterns](#common-slot-patterns)
* [Best Practices](#best-practices)
* [Conclusion](#conclusion)

## Introduction to Slots

In Laravel Components, slots are a powerful mechanism that allow you to pass and inject content into a component from
its parent view. They provide a flexible way to create reusable components with customizable content areas.

## Basic Slot Usage

At its core, a slot is a placeholder within a component where parent content can be inserted:

```php
// Component view (resources/views/components/card.blade.php)
<div class="card">
    {{"{{"}} $slot }}
</div>

// Usage in a parent view
<x-card>
    This content will be rendered inside the slot
</x-card>
```

## Named Slots

Named slots allow you to create multiple content areas within a single component:

```php
// Component view
<div class="card">
    <div class="card-header">
        {{"{{"}} $header }}
    </div>
    <div class="card-body">
        {{"{{"}} $slot }}
    </div>
    <div class="card-footer">
        {{"{{"}} $footer }}
    </div>
</div>

// Usage
<x-card>
    <x-slot:header>Card Title</x-slot:header>
    Main content goes here
    <x-slot:footer>Footer information</x-slot:footer>
</x-card>
```

## Default Slot Content

You can provide default content for slots that may not always be filled:

```php
// Component view
<div class="alert">
    {{"{{"}} $slot ?? 'Default alert message' }}
</div>
```

## Slot Attributes

Slots can have additional attributes for more dynamic rendering:

```php
// Component view
<div {{"{{"}} $attributes->merge(['class' => 'default-class']) }}>
    {{"{{"}} $slot }}
</div>
```

## Conditional Slot Rendering

Implement conditional logic for slot content:

```php
@if($slot->isNotEmpty())
    <div class="content">
        {{"{{"}} $slot }}
    </div>
@endif
```

## Slot Scoping

Advanced slot scoping allows passing data back to the parent:

```php
// Component
<div>
    {{"{{"}} $slot($user) }}
</div>

// Usage
<x-user-list>
    @foreach($users as $user)
        <x-slot:default="$user">
            {{"{{"}} $user->name }}
        </x-slot:default>
    @endforeach
</x-user-list>
```

## Practical Examples

### Modal Component

```php
// resources/views/components/modal.blade.php
<div class="modal">
    <div class="modal-header">
        {{"{{"}} $title }}
    </div>
    <div class="modal-body">
        {{"{{"}} $slot }}
    </div>
    <div class="modal-footer">
        {{"{{"}} $footer }}
    </div>
</div>

// Usage
<x-modal>
    <x-slot:title>Confirmation</x-slot:title>
    Are you sure you want to proceed?
    <x-slot:footer>
        <button>Confirm</button>
        <button>Cancel</button>
    </x-slot:footer>
</x-modal>
```

## Common Slot Patterns

- Flexible layout components
- Reusable modal dialogs
- Dynamic form elements
- Customizable card interfaces
- Adaptive navigation menus

## Best Practices

- Keep slot content semantically meaningful
- Use named slots for complex components
- Provide default content when appropriate
- Leverage slot attributes for additional flexibility
- Avoid overcomplicating component structure

## Conclusion

Slots in Laravel Components are a sophisticated feature that bridges the gap between component reusability and content
flexibility. They allow developers to create highly adaptable UI components that can be easily customized without
modifying the component's core structure.

By understanding and effectively implementing slots, you can create more modular, maintainable, and intuitive
component-based interfaces in your Laravel applications. They represent a powerful technique for separating concerns
while maintaining the ability to inject dynamic content seamlessly.