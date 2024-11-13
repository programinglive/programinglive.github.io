---
layout: default
title: Slot In Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Slot In Laravel"
---

# Using Slots in Laravel Blade

Laravel’s Blade templating engine allows developers to build dynamic, reusable views. One powerful feature of Blade is the ability to create *components* with *slots*, which allows developers to define custom, reusable templates with flexible content areas. In this article, we’ll dive into how to create components, use slots effectively, and explore practical examples for web applications.

---

### What are Blade Components and Slots?

Blade components are reusable UI pieces that help simplify your code by breaking complex templates into smaller parts. Slots are placeholders within these components where custom content can be inserted. They are ideal for cases like cards, alerts, modals, and other UI elements that share a similar structure but may need different content.

- **Components**: Blade components are similar to functions that return HTML content. They are stored in the `resources/views/components` directory.
- **Slots**: Slots allow you to pass different content into different parts of a Blade component. Laravel provides a `slot` directive to define these areas.

### Creating a Blade Component with Slots

1. **Create a Blade Component**: You can use Artisan commands to generate a component. Let’s create a `Card` component as an example.

   ```bash
   php artisan make:component Card
   ```

   This command creates two files:
    - `app/View/Components/Card.php` — the class file for your component.
    - `resources/views/components/card.blade.php` — the Blade file where you define the component’s template.

2. **Define the Component Structure with Slots**:

   Open `resources/views/components/card.blade.php` and structure your component with slots. Let’s say we want this card to have a `title`, `body`, and `footer`.

   ```html
   <div class="card">
       <div class="card-header">
           {{'{{'}} $title }}
       </div>
       <div class="card-body">
           {{'{{'}} $slot }}
       </div>
       <div class="card-footer">
           {{'{{'}} $footer }}
       </div>
   </div>
   ```

   Here:
    - `{{'{{'}} $slot }}` is the main slot, a placeholder for the primary content of the card.
    - `$title` and `$footer` are *named slots* where custom content can be added.

3. **Using the Component in a Blade File**:

   To use this component, you’ll add it to another Blade template, such as `resources/views/welcome.blade.php`. Here’s how you’d pass content into the slots:

   ```html
   @component('components.card')
       @slot('title')
           Welcome to Laravel
       @endslot

       This is the main content inside the card. You can customize it to fit your needs.

       @slot('footer')
           Thank you for visiting!
       @endslot
   @endcomponent
   ```

    - `@slot('title')` and `@slot('footer')` insert content into the respective slots in the `Card` component.
    - Any content between `@component('components.card')` and `@endcomponent` goes into the default `$slot` (body section).

### Practical Example: Creating a Reusable Alert Component

Let’s create a component for displaying alerts, with dynamic content for the alert message and an optional slot for additional information.

1. **Generate the Component**:

   ```bash
   php artisan make:component Alert
   ```

2. **Define the Alert Structure** in `resources/views/components/alert.blade.php`:

   ```html
   <div class="alert alert-{{'{{'}} $type }}">
       {{'{{'}} $slot }}
       @if(isset($details))
           <div class="alert-details">
               {{'{{'}} $details }}
           </div>
       @endif
   </div>
   ```

    - Here, `{{'{{'}} $slot }}` is the main alert message.
    - `{{'{{'}} $type }}` is a variable that controls the alert’s appearance (e.g., `success`, `error`).
    - `{{'{{'}} $details }}` is an optional slot for extra information, shown only if `$details` is set.

3. **Passing Data to the Component**:

   In the `app/View/Components/Alert.php` file, modify the constructor to accept `$type` and `$details`.

   ```php
   <?php

   namespace App\View\Components;

   use Illuminate\View\Component;

   class Alert extends Component
   {
       public $type;
       public $details;

       public function __construct($type = 'info', $details = null)
       {
           $this->type = $type;
           $this->details = $details;
       }

       public function render()
       {
           return view('components.alert');
       }
   }
   ```

4. **Using the Alert Component in a Blade Template**:

   Now, you can use the `Alert` component with different alert types and optional details.

   ```html
   <x-alert type="success">
       This is a success message!
       <x-slot name="details">
           You successfully completed the action.
       </x-slot>
   </x-alert>

   <x-alert type="warning">
       This is a warning message!
   </x-alert>
   ```

   In this example:
    - The first alert has a `type` of `success` and additional `details`.
    - The second alert only provides a main message and omits `details`.

### Default Slot and Named Slots

- **Default Slot** (`{{'{{'}} $slot }}`): Used for the main content inside the component.
- **Named Slots**: Use `@slot` in traditional Blade components or `<x-slot name="slotName">` in tag-based components. Named slots allow you to specify unique sections of content within a component.

### When to Use Slots

Slots make components more flexible and modular. Here are some cases where slots are particularly useful:

- **Reusable Cards**: Where each card can display a different title, body, and footer.
- **Alert Boxes**: To display various messages, icons, or call-to-actions within a consistent design.
- **Layouts and Headers**: Where you want custom content for each page but a common structure.

### Conclusion

Laravel’s slots are a powerful way to enhance the flexibility of your Blade components. By defining reusable components with slots, you can manage layouts more efficiently, reduce code duplication, and create dynamic sections in your web applications. This approach helps you keep your code modular, organized, and maintainable as your application grows.
