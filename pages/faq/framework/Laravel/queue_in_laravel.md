---
layout: default
title: Queue In Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Queue In Laravel"
---

# Queue in Laravel

Laravel provides a robust queueing system that helps developers handle time-consuming tasks asynchronously, allowing web
applications to remain responsive. This article will guide you through the concept, setup, and usage of queues in
Laravel.

## Table of Contents

1. [What is a Queue?](#what-is-a-queue)
2. [Why Use Queues?](#why-use-queues)
3. [Setting Up Queues in Laravel](#setting-up-queues-in-laravel)
4. [Creating a Queue Job](#creating-a-queue-job)
5. [Processing the Queue](#processing-the-queue)
6. [Queue Drivers](#queue-drivers)
7. [Monitoring Queues](#monitoring-queues)
8. [Conclusion](#conclusion)

---

## What is a Queue?

A queue is a data structure that stores tasks to be processed later. In Laravel, queues allow you to defer
time-consuming operations such as sending emails, generating reports, or processing large datasets to improve the
responsiveness of your application.

## Why Use Queues?

Using queues helps to:

- **Improve Performance**: Offload heavy tasks to be executed in the background.
- **Ensure Reliability**: Retry failed tasks without user intervention.
- **Scalability**: Handle a large number of tasks efficiently.

## Setting Up Queues in Laravel

To set up queues in Laravel:

1. **Install a Queue Driver**: Laravel supports drivers like `database`, `Redis`, `Beanstalkd`, `Amazon SQS`, etc. You
   need to choose and configure one.

2. **Set the Default Driver**:
   Open the `config/queue.php` file and set the `default` option to your preferred driver. For example, to use the
   database driver:

   ```php
   'default' => env('QUEUE_CONNECTION', 'database'),
   ```

3. **Migrate the Queue Table**:
   For the database driver, run the following commands to create the necessary table:

   ```bash
   php artisan queue:table
   php artisan migrate
   ```

## Creating a Queue Job

Queue jobs in Laravel are simple to create:

1. Run the Artisan command to generate a job:
   ```bash
   php artisan make:job SendEmailJob
   ```

2. Open the generated file in the `app/Jobs` directory and define the `handle` method to process the task.

3. Dispatch the job using the `dispatch` method:
   ```php
   use App\Jobs\SendEmailJob;

   SendEmailJob::dispatch($emailDetails);
   ```

## Processing the Queue

To process queued jobs, run the queue worker:

```bash
php artisan queue:work
```

You can also use `queue:listen` to monitor changes in real-time.

## Queue Drivers

Laravel supports several queue drivers:

- **Database**: Uses a database table to store jobs.
- **Redis**: A fast, in-memory data structure store.
- **Beanstalkd**: A simple, fast work queue.
- **Amazon SQS**: A scalable message queuing service.

Configure these drivers in the `.env` file:

```env
QUEUE_CONNECTION=redis
```

## Monitoring Queues

To monitor queue jobs, Laravel provides tools like:

- **Failed Jobs Table**: Track failed jobs by creating a failed jobs table:
  ```bash
  php artisan queue:failed-table
  php artisan migrate
  ```

- **Horizon**: For Redis queues, Laravel Horizon offers a dashboard to monitor queue jobs.

## Conclusion

Queues in Laravel are powerful tools for handling time-consuming tasks efficiently. By leveraging Laravel's queueing
system, developers can ensure their applications are performant, reliable, and scalable.

Start integrating queues in your Laravel projects today and experience the benefits firsthand!

