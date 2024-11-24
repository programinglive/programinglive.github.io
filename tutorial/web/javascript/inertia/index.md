---
title: InertiaJS
layout: default
parent: JavaScript
grand_parent: Web Development
description: "InertiaJS"
---

# InertiaJS

InertiaJS is a modern framework that connects server-side frameworks (like Laravel) with JavaScript-based frontend
frameworks (like Vue, React, or Svelte). It simplifies the process of building single-page applications (SPAs) without
the need for a separate API layer.

---

## Table of Contents

- [What is InertiaJS?](#what-is-inertiajs)
- [How InertiaJS Works](#how-inertiajs-works)
- [Setting Up InertiaJS](#setting-up-inertiajs)
    - [Server-Side Installation](#server-side-installation)
    - [Frontend Installation](#frontend-installation)
- [Basic Usage](#basic-usage)
    - [Rendering Pages](#rendering-pages)
    - [Linking Between Pages](#linking-between-pages)
    - [Sharing Data](#sharing-data)
- [Benefits of Using InertiaJS](#benefits-of-using-inertiajs)
- [Conclusion](#conclusion)

---

## What is InertiaJS?

InertiaJS is a framework for building SPAs without requiring a full API backend. It provides a seamless way to:

- Deliver frontend components from the server.
- Handle routing on the server while maintaining SPA behavior on the frontend.
- Use familiar server-side frameworks to build complex SPAs.

---

## How InertiaJS Works

InertiaJS acts as a **glue** between the server and the client.

1. The server delivers views (frontend components) along with data.
2. The frontend updates dynamically using JavaScript without reloading the page.

This approach eliminates the need for APIs or JSON endpoints, as Inertia handles data transfer in the background.

---

## Setting Up InertiaJS

### Server-Side Installation

For Laravel:

1. Install the Inertia server-side package:
   ```bash
   composer require inertiajs/inertia-laravel
   ```  

2. Add the middleware to your `App\Http\Kernel.php`:
   ```php
   protected $middlewareGroups = [
       'web' => [
           \Inertia\Middleware::class,
       ],
   ];
   ```  

3. Create a basic route:
   ```php
   Route::get('/', function () {
       return Inertia::render('Home', [
           'message' => 'Welcome to InertiaJS!'
       ]);
   });
   ```  

### Frontend Installation

For Vue.js:

1. Install the required packages:
   ```bash
   npm install @inertiajs/inertia @inertiajs/inertia-vue vue
   ```  

2. Set up the `app.js` file:
   ```javascript
   import { createApp, h } from 'vue';
   import { createInertiaApp } from '@inertiajs/inertia-vue';

   createInertiaApp({
       resolve: name => require(`./Pages/${name}`),
       setup({ el, App, props, plugin }) {
           createApp({ render: () => h(App, props) })
               .use(plugin)
               .mount(el);
       },
   });
   ```  

3. Create a Vue component in `resources/js/Pages/Home.vue`:
   ```vue
   <template>
       <div>
           <h1>{{ message }}</h1>
       </div>
   </template>

   <script>
   export default {
       props: {
           message: String,
       },
   };
   </script>
   ```  

---

## Basic Usage

### Rendering Pages

In Laravel, use `Inertia::render` to send a frontend component and data:

```php
Route::get('/about', function () {
    return Inertia::render('About', [
        'title' => 'About Us',
    ]);
});
```  

### Linking Between Pages

In the frontend, use the `<inertia-link>` component to navigate:

```vue

<template>
  <div>
    <inertia-link href="/">Home</inertia-link>
    <inertia-link href="/about">About</inertia-link>
  </div>
</template>
```  

### Sharing Data

Share data globally using middleware. For example, share authenticated user information:

1. In `AppServiceProvider.php`:
   ```php
   use Inertia\Inertia;

   public function boot()
   {
       Inertia::share('auth', function () {
           return [
               'user' => auth()->user(),
           ];
       });
   }
   ```  

2. Access the data in your Vue component:
   ```vue
   <template>
       <div v-if="auth.user">
           Welcome, {{ auth.user.name }}!
       </div>
   </template>

   <script>
   export default {
       props: {
           auth: Object,
       },
   };
   </script>
   ```  

---

## Benefits of Using InertiaJS

- **Simplified SPA Development**: No need for APIs or JSON endpoints.
- **SEO-Friendly**: Routing is handled on the server side.
- **Ease of Use**: Developers can use their favorite backend and frontend frameworks together.
- **Improved Performance**: No full-page reloads, providing a smooth user experience.

---

## Conclusion

InertiaJS bridges the gap between server-side and client-side development, offering the best of both worlds. By
leveraging InertiaJS, you can build modern SPAs with less complexity, making it an excellent choice for developers
familiar with frameworks like Laravel and Vue.js.

Start exploring InertiaJS today and simplify your SPA workflow!