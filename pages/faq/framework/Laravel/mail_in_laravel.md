---
layout: default
title: Mail In Laravel
parent: Laravel
grand_parent: Framework
ancestor: FAQ
description: "Mail In Laravel"
---

# Mail in Laravel

## Table of Contents

* [Introduction to Laravel Mail](#introduction-to-laravel-mail)
* [Mail Configuration](#mail-configuration)
* [Sending Basic Emails](#sending-basic-emails)
* [Mailable Classes](#mailable-classes)
* [Email Templates](#email-templates)
* [Customizing Emails](#customizing-emails)
* [Attachments](#attachments)
* [Inline Attachments](#inline-attachments)
* [Markdown Emails](#markdown-emails)
* [Queueing Emails](#queueing-emails)
* [Mail Testing](#mail-testing)
* [Handling Mail Failures](#handling-mail-failures)
* [Advanced Mail Features](#advanced-mail-features)
* [Drivers and Providers](#drivers-and-providers)
* [Best Practices](#best-practices)
* [Conclusion](#conclusion)

## Introduction to Laravel Mail

Laravel provides a clean, simple API over the popular Symfony Mailer component, offering a robust email sending solution
with support for multiple drivers and extensive customization options.

## Mail Configuration

Configure mail settings in `config/mail.php`:

```php
return [
    'default' => env('MAIL_MAILER', 'smtp'),
    'mailers' => [
        'smtp' => [
            'transport' => 'smtp',
            'host' => env('MAIL_HOST', 'smtp.mailgun.org'),
            'port' => env('MAIL_PORT', 587),
            'encryption' => env('MAIL_ENCRYPTION', 'tls'),
            'username' => env('MAIL_USERNAME'),
            'password' => env('MAIL_PASSWORD'),
        ],
    ],
];
```

## Sending Basic Emails

Multiple ways to send emails:

```php
// Simple send
Mail::to('user@example.com')->send(new WelcomeMail());

// With additional recipients
Mail::to($user)
    ->cc($manager)
    ->bcc($admin)
    ->send(new NotificationMail());
```

## Mailable Classes

Create dedicated mailable classes:

```php
class WelcomeMail extends Mailable
{
    use Queueable, SerializesModels;

    public $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function build()
    {
        return $this->view('emails.welcome')
                    ->subject('Welcome to Our Platform');
    }
}
```

## Email Templates

Create email views in `resources/views/emails`:

```php
// Plain text email
<p>Hello, {{ $user->name }}!</p>
<p>Welcome to our application.</p>

// HTML email with styling
<!DOCTYPE html>
<html>
<head>
    <style>
        .email-content { font-family: Arial, sans-serif; }
    </style>
</head>
<body>
    <div class="email-content">
        <h1>Welcome {{ $user->name }}</h1>
        <p>Thanks for joining!</p>
    </div>
</body>
</html>
```

## Customizing Emails

Extensive customization options:

```php
public function build()
{
    return $this->view('emails.welcome')
                ->from('support@example.com', 'Support Team')
                ->replyTo('support@example.com')
                ->subject('Welcome Aboard')
                ->with([
                    'welcomeMessage' => 'Thank you for signing up!'
                ]);
}
```

## Attachments

Adding file attachments:

```php
public function build()
{
    return $this->view('emails.report')
                ->attach('/path/to/file.pdf', [
                    'as' => 'report.pdf',
                    'mime' => 'application/pdf'
                ]);
}
```

## Inline Attachments

Embedding images directly in emails:

```php
public function build()
{
    return $this->view('emails.newsletter')
                ->attachFromStorage('/images/logo.png', 'logo', 'inline');
}
```

## Markdown Emails

Leverage Markdown for email templates:

```php
public function build()
{
    return $this->markdown('emails.welcome', [
        'user' => $this->user,
        'actionText' => 'Verify Account',
        'actionUrl' => route('verification.verify')
    ]);
}
```

## Queueing Emails

Defer email sending for performance:

```php
class WelcomeMail extends Mailable implements ShouldQueue
{
    use Queueable;

    public function handle()
    {
        // Email sending logic
    }
}
```

## Mail Testing

Built-in testing helpers:

```php
public function testWelcomeEmail()
{
    Mail::fake();

    // Trigger email send
    $user = User::factory()->create();

    // Assert email was sent
    Mail::assertSent(WelcomeMail::class, function ($mail) use ($user) {
        return $mail->user->id === $user->id;
    });
}
```

## Handling Mail Failures

Implement error handling:

```php
try {
    Mail::to($user)->send(new WelcomeMail($user));
} catch (\Exception $e) {
    Log::error('Email sending failed: ' . $e->getMessage());
}
```

## Advanced Mail Features

- Localized emails
- Dynamic subject lines
- Conditional content
- Email tracking
- Personalization

## Drivers and Providers

Supported mail drivers:

- SMTP
- Mailgun
- Postmark
- Amazon SES
- Sendmail
- Array (for testing)

## Best Practices

- Use dedicated Mailable classes
- Leverage queueing for performance
- Implement comprehensive error handling
- Use environment-based configurations
- Test email functionality thoroughly

## Conclusion

Laravel's Mail system provides a powerful, flexible approach to sending emails. By offering an elegant API, multiple
driver support, and extensive customization options, Laravel simplifies email communication in web applications.

The framework's comprehensive mail features enable developers to create sophisticated, reliable email solutions with
minimal complexity, making email handling an intuitive and efficient process.