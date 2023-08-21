# How to integrate a payment gateway

## How to integrate your own payment gateway with Duda eCommerce

This step-by-step tutorial is designed to get you started with the core concepts of Duda native eCommerce’s custom payment gateway feature. You will learn how to create an App inside Duda that allows merchants to offer their own gateway.

### Prerequisites

To follow along you’ll need:

* Access to the [Sandbox Environment](https://editor-sandbox.duda.co/login)
* App Store API Credentials
* An App UUID
* Access to Duda native eCommerce

If you don't have these, please contact [app-developer-support@duda.co](mailto:app-developer-support@duda.co).

### 1. Setup your Duda app

[https://developer.duda.co/docs/app-getting-started](getting-started-tutorial.md)

### 2. Create an account on app installation

When users install your custom payment gateway app on their website, you should create a record containing all the settings, auth details, `site_name` etc. that you will need to process payments for a website.

### 3. Create a settings page to link the app account to your merchant payment gateway account

The settings page will allow merchants to connect their merchant accounts to your payment gateway. You can also expose a user interface on this page if you have settings the merchant might want to configure directly in Duda.

### 4. Register the custom payment gateway to the website

Once the merchant has fully configured his information account and your app is ready to process payments, you will need to register your gateway on the merchant’s website using our [Create Payment Gateway](../../reference/partner-api-reference/ecomm-payment-gateways.md#create-payment-gateway-1) API endpoint. Registering your gateway to the merchant’s site will automatically appear as connected in the merchant’s dashboard payment gateway settings page.

<figure><img src="https://files.readme.io/0a0f8e3-Untitled.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="curl" %}
```shell
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/{site_name}/ecommerce/payment-gateways \
     --header 'accept: application/json' \
     --header 'authorization: Basic {app_credentials}' \
     --header 'content-type: application/json' \
     --header 'X-DUDA-ACCESS-TOKEN: {access_token}' \
     --data '
{
  "live_payment_methods_url": "https://example.org/live",
  "test_payment_methods_url": "https://example.org/test",
	"name": "My custom payment gateway",
	"description": "This is a description of my custom payment gateway",
	"image": "https://example.org/image.png",
	"icons": [
		"https://example.org/icon1.png",
		"https://example.prg/icon2.png"
	]
}
'
```
{% endtab %}
{% endtabs %}

Our API will return a custom payment gateway object in it’s response. You need to persist the custom payment gateway id in your app account settings record to use later (logging, uninstallment process, etc.).

{% tabs %}
{% tab title="JSON" %}
```json
{
	"id": "cpg_12345"
	"live_payment_methods_url": "https://example.org/live",
  "test_payment_methods_url": "https://example.org/test",
	"name": "My custom payment gateway",
	"description": "This is a description of my custom payment gateway",
	"image": "https://example.org/image.png",
	"icons": [
		"https://example.org/icon1.png",
		"https://example.prg/icon2.png"
	]
}
```
{% endtab %}
{% endtabs %}

### 5. Handle available payment methods for an invoice

Payment lifecycle with a custom payment gateway:

<figure><img src="https://files.readme.io/d71b8f7-Untitled_1.png" alt=""><figcaption></figcaption></figure>

Every time a customer is in the checkout process and is at the payment step, our servers will make a POST request to your `live_payment_methods_url` or `test_payment_methods_url` to retrieve your available payment methods.

{% hint style="warning" %}
**Heads up: Validate same as step 5**

This step is the best opportunity your app will have to assert that the incoming invoice will be able to process payments. Depending on your gateway’s restrictions, some gateways can have limitations regarding these invoice’s properties:

* Test or Live transactions
* Invoice’s currency
* Invoice’s total amount
* Customer’s billing address
* Merchant’s configuration with your app
* Invoice’s purchase type
* etc.
{% endhint %}

You need to respond with an array of payment methods compatible with the customer’s cart, or an empty array if your gateway can’t handle this particular payment. Each payment method returned will create a button on the payment step. e.g.:

<figure><img src="https://files.readme.io/48760e2-Untitled_2.png" alt=""><figcaption></figcaption></figure>

Example POST payload we will send to your `live_payment_methods_url` or `test_payment_methods_url`

{% tabs %}
{% tab title="JSON" %}
```json
{
	"mode": "TEST",
	"site_name": "abc123",
	"invoice": {
		"shipping_address": {
			"first_name": "John",
			"last_name": "Doe",
			"full_name": "John Doe",
			"address_1": "577 College Ave.",
			"address_2": null,
			"city": "Palo Alto",
			"region": "CA",
			"country": "US",
			"postal_code": "94306",
			"phone": null,
			"sub_locality": null,
			"street_address": null,
			"street_name": null
		},
		"billing_address": {
			"first_name": "John",
			"last_name": "Doe",
			"full_name": "John Doe",
			"address_1": "577 College Ave.",
			"address_2": null,
			"city": "Palo Alto",
			"region": "CA",
			"country": "US",
			"postal_code": "94306",
			"phone": null,
			"sub_locality": null,
			"street_address": null,
			"street_name": null
		},
		"email": "john.doe@example.org",
		"language": "en",
		"currency": "USD",
		"total": "30.75",
		"purchase_id": "cart_123",
		"purchase_type": "CART",
		"items": [
			{
				"name": "Red t-shirt",
				"amount": "10.25",
				"quantity": 3,
				"type": "PHYSICAL",
				"discount_amount": "0.00",
				"total": "30.75"
			},
			{
				"name": "Federal tax",
				"amount": "10.25",
				"quantity": 1,
				"type": "TAX",
				"discount_amount": "0.00",
				"total": "10.25"
			}
		]
	}
}
```
{% endtab %}
{% endtabs %}

Example payment method response to create the payment methods buttons

{% tabs %}
{% tab title="JSON" %}
```json
[
    {
				"id": "my-custom-payment-method", // unique id between your availaible payment methods
        "name": "My custom payment method", // display name visible to customers
				"checkout_url": "https://example.org/checkout", // URL that the customer will get redirected to in order to checkout in your hosted payment page
				"icon": "https://example.org/icon.png" // (optional) image url to display in our cart next to the checkout button
    },
		{
				"id": "my-second-custom-payment-method",
        "name": "My second custom payment method",
				"checkout_url": "https://example.org/alternative-checkout",
				"icon": "https://example.org/alternative-icon.png"
    },
		...
]
```
{% endtab %}
{% endtabs %}

### 6. Handle checkout intent on your hosted payment page

Once the customer has selected your payment method in the checkout, we will redirect them to your `checkout_url` with a `session_id` and a `site_name` query string parameters appended to your provided `checkout_url`.

Once the customer is on your external checkout, the rest of the payment sequence is up to you. Generally, this is where you collect customer's payment information and process the charge through the payment gateway platform you integrate.

With these two parameters, you will be able to retrieve the customer’s payment session by making this API call using our [Get Payment Session](../../reference/partner-api-reference/ecomm-payments.md#get-payment-session-1) endpoint:

{% tabs %}
{% tab title="curl" %}
```shell
curl --request GET \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/{site_name}/ecommerce/payment-sessions/{session_id} \
     --header 'accept: application/json' \
     --header 'authorization: Basic {app_credentials}' \
     --header 'X-DUDA-ACCESS-TOKEN: {access_token}'
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="JSON" %}
```json
{
	"id": "123",
	"mode": "LIVE",
	"cancel_url": "https://example.org/#checkout",
	"invoice": {
		"purchase_id": "123456",
		"purchase_type": "CART",
		"email": "john.doe@example.org",
		"language": "en",
		"currency": "CAD",
		"total": "20.00",
		"shipping_address": {
			"first_name": "John",
			"last_name": "Doe",
			"full_name": "John Doe",
			"address_1": "577 College Ave.",
			"address_2": null,
			"city": "Palo Alto",
			"region": "CA",
			"country": "US",
			"postal_code": "94306",
			"phone": null,
			"sub_locality": null,
			"street_address": null,
			"street_name": null
		},
		"billing_address": {
			"first_name": "John",
			"last_name": "Doe",
			"full_name": "John Doe",
			"address_1": "577 College Ave.",
			"address_2": null,
			"city": "Palo Alto",
			"region": "CA",
			"country": "US",
			"postal_code": "94306",
			"phone": null,
			"sub_locality": null,
			"street_address": null,
			"street_name": null
		},
		"items": [
			{
				"type": "PHYSICAL",
				"name": "Red T-shirt",
				"unit_price": "10.00",
				"discount_amount": "0.00",
				"quantity": 1,
				"total": "10.00"
			},
			{
				"type": "TAX",
				"name": "Federal Tax",
				"unit_price": "5.00",
				"discount_amount": "0.00",
				"quantity": 1,
				"total": "5.00"
			},
			{
				"type": "TAX",
				"name": "State Tax",
				"unit_price": "2.00",
				"discount_amount": "0.00",
				"quantity": 1,
				"total": "2.00"
			},
			{
				"type": "SHIPPING",
				"name": "Shipping fees",
				"unit_price": "3.00",
				"discount_amount": "0.00",
				"quantity": 1,
				"total": "3.00"
			}
		]
	}
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Heads up: Validate paymentgateway can perform transaction**

If you made validations on step 5 that the invoice can be processed by your gateway, these checks should be done before displaying the payment form too.

In the very unlikely case a customer would be redirected to your checkout page, you should update the payment session with an error state (see step #7). You will then be able to redirect the user to our checkout page with a clear message indicating that the payment cannot be processed.
{% endhint %}

{% hint style="info" %}
**Good to know: Return to cart best practices**

Your user interface should include a return to cart button if your customers want to go back and edit their carts, or cancel the payment. This button should use the `cancel_url` in the payment session retrieval. This url will automatically re-open the cart for the customer once the redirection is complete.
{% endhint %}

### 7. Confirm the payment session with your payment result

Once the payment is made, successful **or not**, your app will need to update the payment session with its result. This update will trigger the order creation in the merchant’s dashboard, and redirect the user to the order confirmation page or it will redirect the customer to the checkout page with the error message you specified in the payment session update.

Example of a successful payment:

{% tabs %}
{% tab title="curl" %}
```shell
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/{site_name}/ecommerce/payment-sessions/{payment_session_id}/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic {app_credentials}' \
     --header 'content-type: application/json' \
     --header 'X-DUDA-ACCESS-TOKEN: {access_token}' \
     --data '
{
  "state": "PROCESSED",
	"transaction_id": "my-unique-transaction-id",
	"name": "My custom payment gateway name",
	"icon": "https://example.org/my-gateway-logo.png",
	"instructions": "Optional string to display extra instructions to your customers",
	"links": {
		"refunds": null
	}
}
'
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="JSON" %}
```json
{
	"return_url": "https://redirect.multiscreensite.com/..."
}
```
{% endtab %}
{% endtabs %}

<figure><img src="https://files.readme.io/32b3f6f-Untitled_3.png" alt="" width="375"><figcaption></figcaption></figure>

Example of a failed payment:

{% tabs %}
{% tab title="curl" %}
```shell
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/{site_name}/ecommerce/payment-sessions/{payment_session_id}/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic {app_credentials}' \
     --header 'content-type: application/json' \
     --header 'X-DUDA-ACCESS-TOKEN: {access_token}' \
     --data '
{
  "state":"FAILED",
	"error": {
		"code": "my-unique-error-message-code",
		"message": "A mysterious error happend while processing your payment"
	}
}
'
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="JSON" %}
```json
{
	"return_url": "https:://redirect.multiscreensite.com/..."
}
```
{% endtab %}
{% endtabs %}

<figure><img src="https://files.readme.io/4fefab5-Untitled_4.png" alt=""><figcaption></figcaption></figure>

### 8. Handling refunds (future)

**will be documented once the feature is developed on Duda’s side**

### 9. Unregister the payment gateway

If a merchant wants to remove your payment gateway, the app will need to remove its gateway registration from the specific website. When the merchant uninstall the app, our servers will make a HTTP call to the `uninstallation_endpoint` specified in the app manifest. The call to this URL should trigger the deletion of the payment gateway on the website.

{% tabs %}
{% tab title="curl" %}
```shell
curl --request DELETE \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/{site_name}/ecommerce/payment-gateways/{gateway_id} \
     --header 'accept: application/json' \
     --header 'authorization: Basic {app_credentials}' \
     --header 'content-type: application/json' \
     --header 'X-DUDA-ACCESS-TOKEN: {access_token}'
```
{% endtab %}
{% endtabs %}
