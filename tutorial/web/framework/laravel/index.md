---
title: Laravel
layout: default
parent: Framework
grand_parent: Web Development
nav_order: 5
description: "Tutorial Laravel"
---


### Getting Started with Laravel

Laravel is a robust PHP framework that simplifies web development by providing tools for routing, templating, database interaction, authentication, and more. Created by Taylor Otwell, Laravel follows the *Model-View-Controller* (MVC) architecture, making it easier to organize and manage code. In this tutorial, you’ll learn how to set up Laravel, understand its basic structure, and create a simple app.

---

### Why Use Laravel?

Laravel is widely adopted for its developer-friendly syntax and powerful features that streamline common tasks:
- **Database Management**: Laravel’s *Eloquent ORM* makes database interactions simple and expressive.
- **Authentication & Authorization**: Built-in tools make handling user authentication a breeze.
- **Routing & Templating**: Laravel provides a clean way to define routes and build responsive, reusable views.
- **Task Scheduling**: With Artisan commands, you can schedule tasks like sending out email reminders or cleanup routines.

### Installing Laravel

To get started, make sure you have **PHP**, **Composer** (PHP’s package manager), and a server environment like **XAMPP** or **Laravel Valet** installed.

1. **Install Composer**: If you haven’t already, download and install Composer from [getcomposer.org](https://getcomposer.org/).
2. **Create a Laravel Project**: Run the following command in your terminal to create a new Laravel project:

   ```bash
   composer create-project --prefer-dist laravel/laravel myApp
   ```

3. **Navigate to the Project Directory**:

   ```bash
   cd myApp
   ```

4. **Start the Development Server**:

   ```bash
   php artisan serve
   ```

   This will start a local server at `http://localhost:8000`. Open this URL in your browser to see the default Laravel welcome page.

### Laravel’s Folder Structure

Laravel’s structure is organized to follow best practices for MVC:

- **app/**: Contains your application code, including Models, Controllers, and other core classes.
- **routes/**: Holds all route definitions. `web.php` is where you define routes for web requests.
- **resources/views/**: Contains the view files, often written in Laravel’s templating language, *Blade*.
- **database/**: Houses migrations, seeders, and factory files, making it easy to manage databases.
- **public/**: This is the web root. Assets such as images, CSS, and JavaScript files are stored here.

---

### Creating Routes

Routes define how different URLs on your site are handled. Open `routes/web.php` and add a basic route:

```php
Route::get('/hello', function () {
    return "Hello, Laravel!";
});
```

When you go to `http://localhost:8000/hello`, you should see “Hello, Laravel!” displayed.

### Working with Controllers

In Laravel, Controllers are used to group related request-handling logic into a single class.

1. **Create a Controller**:

   ```bash
   php artisan make:controller WelcomeController
   ```

2. **Define a Method**: Open `app/Http/Controllers/WelcomeController.php` and add a method:

   ```php
   <?php

   namespace App\Http\Controllers;

   use Illuminate\Http\Request;

   class WelcomeController extends Controller
   {
       public function greet()
       {
           return "Hello from the WelcomeController!";
       }
   }
   ```

3. **Add a Route for the Controller Method** in `web.php`:

   ```php
   Route::get('/greet', [App\Http\Controllers\WelcomeController::class, 'greet']);
   ```

   Now, navigating to `http://localhost:8000/greet` should display the message from the `greet` method in `WelcomeController`.

---

### Using Blade Templating Engine

Laravel’s Blade templating engine lets you create clean, reusable HTML templates.

1. **Create a Blade File**: In `resources/views`, create a file called `welcome.blade.php`:

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Welcome Page</title>
   </head>
   <body>
       <h1>{{'{{'}} $message }}</h1>
   </body>
   </html>
   ```

2. **Update the Controller to Use Blade**:

   In `WelcomeController`, modify the `greet` method:

   ```php
   public function greet()
   {
       $message = "Hello, Laravel from Blade!";
       return view('welcome', compact('message'));
   }
   ```

3. This code uses the `compact` function to pass data to the view. Now, when you go to `http://localhost:8000/greet`, you’ll see the message displayed through Blade.

### Database Connection and Migrations

Laravel makes it easy to connect to databases and create tables using migrations.

1. **Set Up the Database**: In `.env`, update the database connection details:

   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=your_database_name
   DB_USERNAME=your_username
   DB_PASSWORD=your_password
   ```

2. **Create a Migration**:

   ```bash
   php artisan make:migration create_tasks_table
   ```

3. **Define the Table Schema**: Open the migration file in `database/migrations` and define the columns:

   ```php
   public function up()
   {
       Schema::create('tasks', function (Blueprint $table) {
           $table->id();
           $table->string('name');
           $table->timestamps();
       });
   }
   ```

4. **Run the Migration**:

   ```bash
   php artisan migrate
   ```

   This will create a `tasks` table with an `id`, `name`, and timestamp columns.

### Working with Eloquent ORM

Laravel’s Eloquent ORM makes it easy to work with database records using models.

1. **Create a Model**:

   ```bash
   php artisan make:model Task
   ```

2. **Using the Model**: In `WelcomeController`, add code to insert a record into the `tasks` table.

   ```php
   use App\Models\Task;

   public function addTask()
   {
       $task = new Task();
       $task->name = "Learn Laravel";
       $task->save();

       return "Task added!";
   }
   ```

3. **Create a Route** to test the method in `web.php`:

   ```php
   Route::get('/add-task', [App\Http\Controllers\WelcomeController::class, 'addTask']);
   ```

   Visiting `http://localhost:8000/add-task` will insert a new task into the database.

---

### Conclusion: Building Web Apps with Laravel

With Laravel’s powerful features and simple syntax, you can easily develop web applications that are well-organized, secure, and easy to maintain. This tutorial introduces you to basic concepts like routing, controllers, Blade templating, and database interactions. As you advance, Laravel offers additional tools for building more complex apps, such as authentication, APIs, and middleware. Happy coding!