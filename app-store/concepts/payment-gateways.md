# Payment Gateways

Duda enables 3rd party payment gateways to be integrated into the platform so that shoppers can check out using a different payment gateway. This enables 3rd party payment gateways, alternative payment methods, local payment services, and more.

Payment Gateways can be integrated in one of two ways:

1. **As an App** (Recommended): Leverage the App Store APIs to make a 3rd party payment gateway available directly inside of Duda. This can be done only for your customers as a Private App or be made public to all Duda customers. An App enables the best user experience, as it can allow the configuration of the payment gateway into the editor experience of Duda. For example, the App can have a UI where customers set specific settings for that store, like API keys, color settings, and more (depending on the payment gateway being built-in)
2. **Using the Partner APIs**: You can leverage most of the same APIs described in this doc to add a custom payment gateway to a specific website. There will be no in-editor experience to manage the payment gateway, though.

## High-Level Flow

Custom payment gateways work by adding a new checkout method into the cart/checkout flow that allows the shopper to select that payment gateway. The way this work is:

<figure><img src="https://files.readme.io/d164207-Untitled_1.png" alt=""><figcaption></figcaption></figure>

### Configure payment gateway

The developer/API configures a payment-gateway URL via the Duda API on a specific website/store. This URL is pinged every time the checkout is loaded and sends details about the order. Your App/URL can respond with the available payment gateway if the gateway is supported for that order.

### Shopper selects custom payment gateway

The shopper can select the payment gateway that is returned from your backend.

### Shopper is redirected to payment gateway

When the user clicks on the custom payment gateway banner, the browser gets redirected to your backend, along with the details of the order. You should process the order details and redirect or display the hosted payment gateway page at this point.

### Confirm order

After the shopper is with the checkout, your backend should notify Duda of the successful order and redirect the user back to the website where the order started from.

## Key Concepts

### Payment gateway

Can be a 3rd party payment gateway, a local payment provider or an alternative payment method. This payment gateway must have a **hosted payment page** which site visitors get redirected to in order to complete the payment.

### Payment Session

Before an order is created, your backend will the details of a payment session. Think of this like a payment, which has not been completed yet. It has all the details of line items in the order, tax, shipping, and other details you might need.

### Refunds

This feature is still in development by Duda, but in the future, Duda expects custom-integrated payment gateways to allow refunds from the order management dashboard inside of the Duda platform. This will tell the payment gateway when an order is refunded (fully or partially) and instruct it to issue that refund to the shopper.

## Further reading

* Learn about [building an app](../technical-requirements.md)
* See our [step-by-step how to integrate a payment gateway](../how-to-guides/how-to-integrate-a-payment-gateway.md) with an App
