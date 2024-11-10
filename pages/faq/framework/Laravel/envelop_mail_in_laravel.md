---
layout: default
title: Envelop Mail In Laravel
parent: Laravel
grand_parent: Framework
description: "Envelop Mail In Laravel"
---

# Enveloping Mail in Laravel

Laravel's `Envelope` feature, introduced in Laravel 9, allows developers to set up metadata for emails in a dedicated method, making it easier to organize various parts of an email. With the envelope approach, you can define properties like the subject, recipients, CC, BCC, and other headers in a structured way, rather than scattering them throughout the Mailable class.

## What is the Envelope in Laravel?

The envelope acts as a "wrapper" for your email message, containing metadata for the email. You define it by adding the `envelope` method to your Mailable class. Laravel provides a dedicated `Envelope` class that you can use to specify the subject, sender, recipients, and other metadata.

## Creating a Mailable Class with an Envelope

Let’s go through the process of creating a Mailable class with the envelope functionality.

### Step 1: Create a Mailable Class

First, create a new Mailable class using Laravel’s Artisan command:

```bash
php artisan make:mail OrderShipped
```

This command will create a new Mailable class located in `app/Mail/OrderShipped.php`.

### Step 2: Define the Envelope Metadata

Open the `OrderShipped.php` file and add the `envelope` method. The `envelope` method returns an instance of Laravel's `Envelope` class, which allows you to set up the email’s metadata.

Here’s an example:

```php
namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;
use Illuminate\Mail\Mailables\Envelope;
use Illuminate\Mail\Mailables\Address;

class OrderShipped extends Mailable
{
    use Queueable, SerializesModels;

    public $order;

    public function __construct($order)
    {
        $this->order = $order;
    }

    public function envelope()
    {
        return new Envelope(
            subject: 'Your Order Has Shipped!',
            from: new Address('no-reply@yourapp.com', 'Your App'),
            to: [
                new Address($this->order->user->email, $this->order->user->name)
            ],
            cc: [new Address('support@yourapp.com', 'Support Team')],
            bcc: [new Address('admin@yourapp.com', 'Admin')],
            replyTo: [new Address('support@yourapp.com', 'Support Team')]
        );
    }

    public function build()
    {
        return $this->view('emails.orders.shipped')
                    ->with([
                        'order' => $this->order,
                    ]);
    }
}
```

### Explanation of the `Envelope` Method

In the `envelope` method:

- **subject**: Defines the subject line of the email.
- **from**: Specifies the sender’s email address and name.
- **to**: Sets the primary recipient(s) of the email.
- **cc**: Defines additional recipients to receive a carbon copy of the email.
- **bcc**: Sets recipients who will receive a blind carbon copy.
- **replyTo**: Specifies the reply-to address, which allows the recipient to respond to a different address than the sender’s.

### Step 3: Setting Up the Email Template

Create an email template in `resources/views/emails/orders/shipped.blade.php` to define the content of your email. Here’s a basic template:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Your Order Has Shipped!</title>
</head>
<body>
    <h1>Order Shipped</h1>
    <p>Hello {{ '{{' }} $order->user->name }},</p>
    <p>Your order #{{ '{{' }} $order->id }} has been shipped and is on its way to you!</p>
    <p>Thank you for shopping with us.</p>
</body>
</html>
```

### Step 4: Sending the Email with Envelop Metadata

To send the email, use the `Mail` facade and pass the `OrderShipped` mailable. The metadata specified in the `envelope` method will be automatically applied:

```php
use App\Mail\OrderShipped;
use Illuminate\Support\Facades\Mail;

$order = Order::find(1);
Mail::send(new OrderShipped($order));
```

## Benefits of Using the Envelope Feature

1. **Organization**: All metadata settings are placed in one method, making your Mailable class more organized.
2. **Readability**: It’s easy to see the subject, sender, recipients, and other metadata at a glance.
3. **Maintainability**: Updates to the email metadata are centralized in the `envelope` method, simplifying future changes.
4. **Flexibility**: The `Envelope` class provides flexibility to customize various email headers based on your application’s needs.

## Additional Envelope Options

The `Envelope` class supports additional options, like setting custom headers. Custom headers can be useful for tracking, categorizing, or filtering emails:

```php
public function envelope()
{
    return new Envelope(
        subject: 'Your Order Has Shipped!',
        headers: [
            'X-Priority' => '1 (Highest)',
            'X-Mailer' => 'Laravel Mail'
        ]
    );
}
```

### Conditional Envelopes

You can also conditionally set envelope properties based on specific conditions within your application:

```php
public function envelope()
{
    $subject = $this->order->isUrgent ? 'Urgent Order Shipment!' : 'Your Order Has Shipped!';
    
    return new Envelope(
        subject: $subject,
        to: [new Address($this->order->user->email, $this->order->user->name)]
    );
}
```

## Conclusion

The Envelope feature in Laravel provides a more structured and powerful way to manage email metadata in your Mailable classes. By centralizing email metadata into a single method, you can maintain cleaner, more readable code, making your Mailable classes easier to manage. Whether you're sending simple notifications or complex transactional emails, the Envelope functionality offers a flexible solution for enhancing your email workflows in Laravel.