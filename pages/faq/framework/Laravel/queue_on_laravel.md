---
layout: default
title: Queue On Laravel
parent: Laravel
grand_parent: Framework
description: "Queue On Laravel"
---

# Queue in Laravel

In web applications, it's common to have tasks that can take time to process, like sending emails, processing images, or handling large database imports. Running these tasks immediately could slow down the user experience or block other critical operations. **Laravel Queues** provide a way to handle these time-consuming tasks in the background, improving the responsiveness of the application.

In this article, we’ll explore how Laravel’s queue system works, how to set it up, and the common use cases that make it a powerful feature for Laravel applications.

## What is a Queue in Laravel?

A **Queue** in Laravel is a way to defer the execution of a task until a later time. Instead of immediately processing a job, Laravel places it in a queue where a background worker will pick it up and complete it at an appropriate time. This approach allows you to offload heavy tasks and keep your application responsive.

For example, instead of making users wait for an email confirmation after registration, you can add the email job to the queue. Laravel will send the email in the background, allowing users to proceed immediately.

### How Laravel Queues Work

Laravel’s queue system consists of three main parts:

1. **Job**: The individual task you want to execute. Each job is a class that contains a `handle` method where the task's logic resides.
2. **Queue**: A list of jobs waiting to be processed. Laravel supports multiple queue connections like database, Redis, Amazon SQS, etc.
3. **Worker**: A background process that fetches jobs from the queue and executes them.

## Setting Up Queues in Laravel

Laravel queues can be set up with various drivers, depending on your environment and requirements. Laravel supports several queue drivers, including:

- **Database** (using a database table to store jobs)
- **Redis** (fast, efficient, suitable for large-scale applications)
- **Amazon SQS** (for distributed, scalable applications)

Let’s walk through a basic setup using the **database** driver.

### Step 1: Configuring the Queue Driver

Open the `config/queue.php` file and set the driver to `database`:

```php
'default' => env('QUEUE_CONNECTION', 'database'),
```

Next, set the environment variable in the `.env` file:

```env
QUEUE_CONNECTION=database
```

### Step 2: Creating a Jobs Table

Laravel uses a jobs table to store pending jobs when using the database driver. Run the following Artisan command to create the migration file for the jobs table:

```bash
php artisan queue:table
php artisan migrate
```

This creates a table named `jobs` where Laravel will store queued jobs.

### Step 3: Creating a Job Class

Laravel makes it easy to create job classes. Run the following command to create a new job:

```bash
php artisan make:job SendEmailJob
```

This will create a `SendEmailJob` class in the `app/Jobs` directory. Open the file, and you’ll see a `handle` method, which is where you can define the job's logic. Here’s a simple example:

```php
namespace App\Jobs;

use App\Mail\WelcomeEmail;
use Illuminate\Support\Facades\Mail;

class SendEmailJob extends Job
{
    protected $email;

    public function __construct($email)
    {
        $this->email = $email;
    }

    public function handle()
    {
        Mail::to($this->email)->send(new WelcomeEmail());
    }
}
```

In this example, the `SendEmailJob` sends a welcome email to a user. The email address is passed in through the constructor and used within the `handle` method.

### Step 4: Dispatching the Job to the Queue

Once the job class is created, you can add it to the queue using the `dispatch` method:

```php
use App\Jobs\SendEmailJob;

$email = 'user@example.com';
SendEmailJob::dispatch($email);
```

This will add the job to the `jobs` table in the database.

### Step 5: Running the Queue Worker

To process jobs from the queue, you need to start a queue worker. This worker will listen for new jobs and execute them as they come in. Run the following command to start a worker:

```bash
php artisan queue:work
```

The queue worker will process jobs as they’re added to the queue. For production environments, you can configure the worker to run as a background service.

## Queue Features and Advanced Usage

Laravel provides several advanced features for working with queues, including:

### Delayed Jobs

Sometimes you may want to delay a job’s execution. Laravel allows you to specify a delay when dispatching a job:

```php
SendEmailJob::dispatch($email)->delay(now()->addMinutes(5));
```

This will delay the job by 5 minutes.

### Job Retries and Failures

You can specify the number of times a job should be retried if it fails. Laravel will automatically retry a job up to a defined number of times before marking it as failed:

```php
public $tries = 5;
```

If a job fails after all retries, you can handle it in a `failed` method:

```php
public function failed()
{
    // Handle job failure logic
}
```

### Rate Limiting Jobs

To prevent overloading your server, you can rate-limit jobs by controlling the number of times a job is processed in a given period.

## Real-World Use Cases of Queues in Laravel

Here are a few scenarios where Laravel queues can be beneficial:

1. **Email Sending**: Send emails to users without delaying the main flow.
2. **Notification Dispatch**: Send notifications or messages to users at specific times.
3. **Image Processing**: Resize or optimize images uploaded by users.
4. **Data Imports/Exports**: Handle large data imports or exports in the background.

## Conclusion

Queues in Laravel offer an efficient way to handle time-intensive tasks in the background, improving the user experience and application performance. By offloading work to background processes, you ensure that your application remains responsive and scalable. Whether you're handling emails, notifications, or heavy data processing, Laravel queues are a robust and flexible solution that every Laravel developer should consider.