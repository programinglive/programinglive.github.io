---
layout: default
title: Repository Pattern On Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Repository Pattern On Laravel"
---

# Repository Pattern in Laravel

The Repository Pattern is a design pattern that mediates between the domain and data mapping layers, providing a
centralized way to interact with data sources. In Laravel, implementing this pattern can enhance the maintainability,
testability, and scalability of your application.

## Table of Contents

- [What is the Repository Pattern?](#what-is-the-repository-pattern)
- [Why Use the Repository Pattern?](#why-use-the-repository-pattern)
- [Setting Up the Repository Pattern in Laravel](#setting-up-the-repository-pattern-in-laravel)
- [Creating a Repository Interface](#creating-a-repository-interface)
- [Implementing the Repository](#implementing-the-repository)
- [Using the Repository in Controllers](#using-the-repository-in-controllers)
- [Testing with the Repository Pattern](#testing-with-the-repository-pattern)
- [Conclusion](#conclusion)

---

## What is the Repository Pattern?

The Repository Pattern provides an abstraction layer over data access logic. It acts as a middle layer between the
application's domain and data source, ensuring that the business logic does not depend on the data access logic.

## Why Use the Repository Pattern?

The benefits of using the Repository Pattern include:

- **Separation of Concerns**: Keeps business logic separate from data access logic.
- **Improved Testability**: Facilitates unit testing by allowing mock repositories.
- **Centralized Data Access**: Provides a single point of interaction with the data source.
- **Flexibility**: Makes it easier to switch or modify data sources.

## Setting Up the Repository Pattern in Laravel

To implement the Repository Pattern in Laravel:

- Create a folder structure for `Repositories` and `Interfaces`.
- Use dependency injection to integrate repositories into controllers.

## Creating a Repository Interface

1. Create an interface for your repository in the `App\Repositories\Interfaces` directory:

   ```php
   namespace App\Repositories\Interfaces;

   interface UserRepositoryInterface
   {
       public function all();
       public function find($id);
       public function create(array $data);
       public function update($id, array $data);
       public function delete($id);
   }
   ```

## Implementing the Repository

1. Create a concrete implementation of the interface in the `App\Repositories` directory:

   ```php
   namespace App\Repositories;

   use App\Models\User;
   use App\Repositories\Interfaces\UserRepositoryInterface;

   class UserRepository implements UserRepositoryInterface
   {
       public function all()
       {
           return User::all();
       }

       public function find($id)
       {
           return User::findOrFail($id);
       }

       public function create(array $data)
       {
           return User::create($data);
       }

       public function update($id, array $data)
       {
           $user = User::findOrFail($id);
           $user->update($data);
           return $user;
       }

       public function delete($id)
       {
           $user = User::findOrFail($id);
           return $user->delete();
       }
   }
   ```

2. Bind the interface to the implementation in a service provider (e.g., `AppServiceProvider`):

   ```php
   use App\Repositories\UserRepository;
   use App\Repositories\Interfaces\UserRepositoryInterface;

   public function register()
   {
       $this->app->bind(UserRepositoryInterface::class, UserRepository::class);
   }
   ```

## Using the Repository in Controllers

1. Inject the repository into your controller:

   ```php
   namespace App\Http\Controllers;

   use App\Repositories\Interfaces\UserRepositoryInterface;

   class UserController extends Controller
   {
       protected $userRepository;

       public function __construct(UserRepositoryInterface $userRepository)
       {
           $this->userRepository = $userRepository;
       }

       public function index()
       {
           $users = $this->userRepository->all();
           return view('users.index', compact('users'));
       }
   }
   ```

## Testing with the Repository Pattern

Mock repositories to test controllers independently of the database:

```php
use App\Repositories\Interfaces\UserRepositoryInterface;

public function testIndex()
{
    $mockRepo = Mockery::mock(UserRepositoryInterface::class);
    $mockRepo->shouldReceive('all')->once()->andReturn([]);

    $this->app->instance(UserRepositoryInterface::class, $mockRepo);

    $response = $this->get('/users');

    $response->assertStatus(200);
}
```

## Conclusion

The Repository Pattern is an excellent way to manage your application's data access layer. By implementing this pattern
in Laravel, you can make your codebase cleaner, more testable, and easier to maintain. Start applying it to your
projects for a better development experience!

