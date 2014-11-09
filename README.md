PHP library for Robokassa payment system
===

Create payment:
```php
$payment = new \Idma\Robokassa\Payment(
    'john_doe', 'password1', 'password2', true
);

$payment
    ->setInvoiceId($order->id)
    ->setSum($order->amount)
    ->setDescription('Payment for some goods');

// redirect to payment url
$user->redirect($payment->getPaymentUrl());
```

Check payment result:
```php
// somewere in result url handler...

...
$payment = new \Idma\Robokassa\Payment(
    'john_dow', 'password1', 'password2', true
);

if ($payment->validate($_GET) {
    $order = Orders::find($payment->getInvoiceId());

    if ($payment->getSum() == $order->sum) {

    }

    // send answer
    echo $payment->getSuccessAnswer(); // "OK1254487\n"
}
...
