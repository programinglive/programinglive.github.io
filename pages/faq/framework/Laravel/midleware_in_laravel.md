---
layout: default
title: Middleware in Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Middleware in Laravel"
---


# Middleware in Laravel

Laravel, one of the most popular PHP frameworks, is known for its elegant syntax and robust features. One of these essential features is **middleware**. Middleware acts as a filter for HTTP requests, enabling us to implement functionality that sits between the request and response lifecycle. In this article, we'll dive deep into how middleware works in Laravel, why it's useful, and how to implement it.

## What is Middleware?

In Laravel, middleware provides a convenient mechanism for filtering HTTP requests that enter your application. For instance, you may want to check if the user is authenticated before allowing them to access certain pages, or log each request for analytics purposes. Middleware can help achieve this by intercepting the request, performing the necessary checks or modifications, and then either passing it to the next layer or stopping it.

Common examples of middleware include:
- **Authentication**: Checking if a user is logged in.
- **Authorization**: Ensuring the user has permission to access a specific resource.
- **Logging**: Recording request data for analytics.
- **CORS Handling**: Enabling cross-origin resource sharing.
- **Maintenance Mode**: Temporarily preventing access to the site during maintenance.

## How Middleware Works

In Laravel, middleware operates at the HTTP kernel level. The HTTP kernel is the core component that handles incoming requests, and middleware sits within its pipeline. When a request enters the Laravel application, it goes through this pipeline, with each middleware either modifying the request, performing an action, or even halting the process.

Laravel executes middleware in the order they are defined, which gives developers control over the sequence of operations.

### Global vs. Route-Specific Middleware

- **Global Middleware**: Runs on every request your application receives. This is useful for operations that need to be applied universally, such as logging or handling CORS.
- **Route-Specific Middleware**: Runs only on specific routes. For instance, you may only want certain routes accessible to authenticated users.

## Creating Middleware in Laravel

Laravel makes it easy to create custom middleware. You can create a new middleware by running the following Artisan command:

```bash
php artisan make:middleware ExampleMiddleware
```

This command generates a new file in the `app/Http/Middleware` directory. Open the newly created middleware file, and you'll see the following structure:

```php
namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;

class ExampleMiddleware
{
    public function handle(Request $request, Closure $next)
    {
        // Perform action before request is handled

        return $next($request);

        // Perform action after request is handled
    }
}
```

The `handle` method is where you define the middleware's logic. You can add conditions, modify the request, or even terminate it before it reaches the controller.

### Example: Middleware for Checking User Roles

Suppose we want to create a middleware that only allows users with the `admin` role to access certain routes. We could set up our middleware like this:

```php
public function handle(Request $request, Closure $next)
{
    if ($request->user()->role !== 'admin') {
        return redirect('home');
    }

    return $next($request);
}
```

This middleware checks the user's role and redirects them if they’re not an admin.

## Registering Middleware

After creating your middleware, you need to register it with the application. This can be done in the `app/Http/Kernel.php` file.

- **Global Middleware**: Add it to the `$middleware` array.
- **Route Middleware**: Add it to the `$routeMiddleware` array.

For example:

```php
protected $routeMiddleware = [
    'admin' => \App\Http\Middleware\AdminMiddleware::class,
];
```

Now, you can apply it to routes as follows:

```php
Route::middleware(['admin'])->group(function () {
    Route::get('/admin', function () {
        // Admin-only routes
    });
});
```

## Middleware Parameters

Laravel allows you to pass parameters to middleware. This is particularly useful when creating reusable middleware that performs similar checks but with different parameters. To do this, add parameters after the middleware in the route definition:

```php
Route::get('/posts', function () {
    // ...
})->middleware('role:admin');
```

Then, in your middleware, retrieve these parameters like so:

```php
public function handle(Request $request, Closure $next, $role)
{
    if ($request->user()->role !== $role) {
        return redirect('home');
    }

    return $next($request);
}
```

## Common Middleware Use Cases

1. **Authentication**: Laravel includes built-in authentication middleware to restrict access to authenticated users.
2. **CORS**: Adding headers to allow cross-origin requests, making your API accessible from different domains.
3. **Rate Limiting**: Restricting the number of requests a user can make to protect against abuse.
4. **Localization**: Setting locale based on user preferences or request parameters.
5. **Logging and Analytics**: Capturing request data to help analyze traffic and usage patterns.

## Conclusion

Middleware is a powerful tool in Laravel, enabling developers to handle various aspects of HTTP requests in a clean, modular way. By understanding how middleware works and learning to implement it, you can take your Laravel application to the next level in terms of security, flexibility, and maintainability.

Whether you're a Laravel novice or a seasoned pro, mastering middleware is essential. So, next time you need to handle a request in a unique way, consider creating middleware and making your application more robust and efficient!