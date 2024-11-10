---
layout: page
title: Mail In Laravel
parent: Framework
grand_parent: FAQ
description: "Mail In Laravel"
---

# Mail in Laravel

Sending emails is a core feature in web applications, whether for sending notifications, password resets, or promotional messages. Laravel, known for its elegant and developer-friendly design, makes email handling straightforward with its built-in **Mail** functionality. This article will explore how Laravel handles email, from configuration to advanced features, ensuring you’re equipped to send emails seamlessly in your Laravel applications.

## Why Use Laravel's Mail System?

Laravel’s Mail system offers several advantages:

- **Simple and Intuitive API**: Laravel provides an expressive API for composing emails.
- **Multiple Drivers**: It supports various mail drivers, such as SMTP, Mailgun, Postmark, and Amazon SES.
- **Templating**: The Blade templating engine allows for crafting beautiful and dynamic email layouts.
- **Queuing**: Laravel supports queuing for emails, allowing you to send emails asynchronously and improve performance.

## Configuring Mail in Laravel

To begin sending emails, you need to configure Laravel's mail settings. The main configuration file is located at `config/mail.php`. Here, you’ll find default configurations, such as the mail driver, host, port, encryption type, and credentials.

### Step 1: Set Up Environment Variables

Open your `.env` file and set up your mail configuration. Below is an example configuration for a typical SMTP setup:

```env
MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=your_mail_username
MAIL_PASSWORD=your_mail_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=noreply@yourapp.com
MAIL_FROM_NAME="${APP_NAME}"
```

Update the values as per your mail provider’s settings (e.g., Mailgun, Gmail, or any other SMTP provider).

### Step 2: Selecting a Mail Driver

Laravel supports multiple mail drivers out of the box, which can be set in the `MAIL_MAILER` environment variable. Here are some of the common drivers:

- **SMTP**: Ideal for sending emails using traditional SMTP servers.
- **Mailgun**: A cloud-based email service provider with additional features for tracking and analytics.
- **Postmark**: Designed for reliable email delivery with tracking and reporting.
- **Amazon SES**: Amazon’s email service for scalable and high-volume email sending.

Each driver has its specific configuration needs, which can be found in the `config/mail.php` file or Laravel’s official documentation.

## Creating and Sending Basic Emails

Laravel makes it easy to send emails using the `Mail` facade. Let’s start by creating a simple email.

### Step 1: Creating a Mailable Class

A **Mailable** class in Laravel represents a single email and contains the email's content, layout, and data. To create a new Mailable, use the following Artisan command:

```bash
php artisan make:mail WelcomeMail
```

This will create a `WelcomeMail` class in the `app/Mail` directory. Open the file, and you’ll see a `build` method where you can define the content and layout of the email.

```php
namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;

class WelcomeMail extends Mailable
{
    use Queueable, SerializesModels;

    public $user;

    public function __construct($user)
    {
        $this->user = $user;
    }

    public function build()
    {
        return $this->from('noreply@yourapp.com')
                    ->subject('Welcome to Our App!')
                    ->view('emails.welcome');
    }
}
```

In this example, we inject a `$user` variable in the `__construct` method to pass data into the view. The `view` method specifies the Blade template we’ll use for this email.

### Step 2: Creating the Email Template

Next, create a Blade template for the email. In the `resources/views/emails` directory, create a new file named `welcome.blade.php`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to Our App!</title>
</head>
<body>
    <h1>Hello, {{ '{{' }} $user->name }}</h1>
    <p>Thank you for joining our platform. We’re thrilled to have you with us.</p>
</body>
</html>
```

Here, we use the `$user` variable passed from the `WelcomeMail` class to personalize the email content.

### Step 3: Sending the Email

Now, to send the email, use the `Mail` facade to call the `send` method, specifying the `WelcomeMail` Mailable:

```php
use App\Mail\WelcomeMail;
use Illuminate\Support\Facades\Mail;

$user = User::find(1);
Mail::to($user->email)->send(new WelcomeMail($user));
```

This code will send the `WelcomeMail` email to the specified user.

## Advanced Email Features in Laravel

Laravel provides several advanced features that enhance the flexibility and control of email sending.

### Using Queued Emails

For time-consuming emails, such as bulk sends, Laravel queues are an efficient solution. Queuing emails allows your application to send them in the background without delaying other processes.

To queue an email, simply use the `queue` method instead of `send`:

```php
Mail::to($user->email)->queue(new WelcomeMail($user));
```

Ensure you have a queue worker running by executing the following Artisan command:

```bash
php artisan queue:work
```

### Delayed Emails

If you want to delay the sending of an email, you can use the `delay` method to specify a wait time:

```php
Mail::to($user->email)->later(now()->addMinutes(10), new WelcomeMail($user));
```

This example schedules the email to be sent 10 minutes after the function call.

### Sending Emails to Multiple Recipients

Laravel allows you to send emails to multiple recipients using `cc` (carbon copy) and `bcc` (blind carbon copy) methods:

```php
Mail::to($primaryEmail)
    ->cc($ccEmails)
    ->bcc($bccEmails)
    ->send(new WelcomeMail($user));
```

This is useful for cases where you want to notify multiple parties about the same event without sending separate emails.

### Testing Email Content

Testing is essential to ensure your emails look correct and contain the right information. Laravel provides a `Mail::fake()` method, which prevents actual emails from being sent and allows you to test email behavior in your application.

```php
use Illuminate\Support\Facades\Mail;
use App\Mail\WelcomeMail;

Mail::fake();

Mail::to($user->email)->send(new WelcomeMail($user));

Mail::assertSent(WelcomeMail::class);
```

Using `Mail::assertSent()`, you can confirm that the `WelcomeMail` was sent, without actually sending an email.

## Real-World Use Cases for Laravel Mail

- **Welcome Emails**: Send a welcome email when a user registers.
- **Password Resets**: Provide secure links for users to reset passwords.
- **Order Confirmations**: Send order details to customers after purchase.
- **Weekly Newsletters**: Engage users with regular content updates.

## Conclusion

Laravel’s Mail system offers a robust, flexible, and intuitive way to handle email sending in your applications. Whether you’re building a simple user registration flow or a complex notification system, Laravel’s Mail tools, combined with features like queuing and Blade templating, make it easy to integrate email capabilities. By mastering these tools, you can ensure a smooth, professional email experience for your users.