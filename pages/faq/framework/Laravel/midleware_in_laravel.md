---
layout: default
title: Middleware in Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Middleware in Laravel"
---

# Middleware in Laravel

## Table of Contents

* [Introduction to Middleware](#introduction-to-middleware)
* [What is Middleware](#what-is-middleware)
* [Types of Middleware](#types-of-middleware)
* [Creating Middleware](#creating-middleware)
* [Registering Middleware](#registering-middleware)
* [Global Middleware](#global-middleware)
* [Route-Specific Middleware](#route-specific-middleware)
* [Middleware Parameters](#middleware-parameters)
* [Middleware Groups](#middleware-groups)
* [Authentication Middleware](#authentication-middleware)
* [Request Modification](#request-modification)
* [Response Modification](#response-modification)
* [Terminating Middleware](#terminating-middleware)
* [Middleware Order and Execution](#middleware-order-and-execution)
* [Advanced Middleware Techniques](#advanced-middleware-techniques)
* [Common Use Cases](#common-use-cases)
* [Best Practices](#best-practices)
* [Conclusion](#conclusion)

## Introduction to Middleware

Middleware provides a mechanism for filtering HTTP requests entering your application. It acts as a bridge between a
request and a response, allowing you to inspect, modify, or halt the request processing.

## What is Middleware

A middleware is a series of "layers" that requests must pass through before reaching their final destination:

```php
Request → Middleware 1 → Middleware 2 → Middleware 3 → Application → Response
```

## Types of Middleware

1. **Built-in Middleware**
    - Authentication
    - CSRF Protection
    - Encryption
    - Throttling

2. **Custom Middleware**
    - User-defined request filters
    - Custom authentication checks
    - Logging and monitoring

## Creating Middleware

Generate middleware using Artisan:

```bash
php artisan make:middleware CheckAge
```

Implement middleware logic:

```php
namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;

class CheckAge
{
    public function handle(Request $request, Closure $next)
    {
        if ($request->age < 18) {
            return redirect('home');
        }

        return $next($request);
    }
}
```

## Registering Middleware

Register in `app/Http/Kernel.php`:

```php
protected $middlewareAliases = [
    'auth' => \App\Http\Middleware\Authenticate::class,
    'age' => \App\Http\Middleware\CheckAge::class,
];
```

## Global Middleware

Applied to every request:

```php
protected $middleware = [
    \App\Http\Middleware\TrustProxies::class,
    \App\Http\Middleware\CheckForMaintenanceMode::class,
];
```

## Route-Specific Middleware

Apply to specific routes:

```php
Route::get('/profile', 'ProfileController@index')
     ->middleware('auth', 'age');

// Or in controller constructor
public function __construct()
{
    $this->middleware('auth')->except(['index']);
}
```

## Middleware Parameters

Pass additional parameters:

```php
class CheckRole
{
    public function handle($request, Closure $next, $role)
    {
        if (!$request->user()->hasRole($role)) {
            return redirect('home');
        }

        return $next($request);
    }
}

// Usage
Route::get('/admin', 'AdminController@index')
     ->middleware('role:admin');
```

## Middleware Groups

Group multiple middleware:

```php
protected $middlewareGroups = [
    'web' => [
        \App\Http\Middleware\EncryptCookies::class,
        \Illuminate\Cookie\Middleware\AddQueuedCookiesToResponse::class,
        \Illuminate\Session\Middleware\StartSession::class,
    ],

    'api' => [
        'throttle:api',
        \Illuminate\Routing\Middleware\SubstituteBindings::class,
    ],
];
```

## Authentication Middleware

Basic authentication check:

```php
public function handle($request, Closure $next)
{
    if (!Auth::check()) {
        return redirect('login');
    }

    // Additional role-based checks
    if (!$request->user()->isAdmin()) {
        abort(403, 'Unauthorized action');
    }

    return $next($request);
}
```

## Request Modification

Modify request before processing:

```php
public function handle($request, Closure $next)
{
    // Transform or validate request
    $request->merge([
        'normalized_email' => strtolower($request->email)
    ]);

    return $next($request);
}
```

## Response Modification

Modify response after processing:

```php
public function handle($request, Closure $next)
{
    $response = $next($request);

    // Add custom headers
    $response->header('X-Custom-Header', 'Value');

    return $response;
}
```

## Terminating Middleware

Perform actions after response:

```php
public function terminate($request, $response)
{
    // Perform cleanup or logging
    Log::info('Request processed');
}
```

## Middleware Order and Execution

Middleware executes in a specific order:

1. Global Middleware
2. Route Middleware
3. Controller Middleware

## Advanced Middleware Techniques

- Dynamic middleware generation
- Conditional middleware application
- Middleware composition
- Dependency injection

## Common Use Cases

- User authentication
- Role-based access control
- Request logging
- CORS handling
- Rate limiting
- HTTPS enforcement

## Best Practices

- Keep middleware focused and single-purpose
- Avoid complex logic in middleware
- Use middleware for cross-cutting concerns
- Leverage dependency injection
- Test middleware thoroughly

## Conclusion

Middleware in Laravel provides a powerful, flexible mechanism for filtering and transforming HTTP requests. By creating
modular, reusable request processors, developers can implement complex application logic with clean, maintainable code.

The middleware system represents Laravel's commitment to providing elegant solutions for common web development
challenges, enabling developers to create robust, secure, and performant applications.