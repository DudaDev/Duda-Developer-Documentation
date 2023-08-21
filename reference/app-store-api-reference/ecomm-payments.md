---
description: Native Store Only
---

# eComm Payments

## Payment Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "id": "string",
  "mode": "LIVE",
  "cancel_url": "string",
  "invoice": {
    "purchase_id": "string",
    "purchase_type": "string",
    "email": "string",
    "language": "string",
    "currency": "string",
    "total": 0,
    "shipping_address": {
      "first_name": "string",
      "last_name": "string",
      "full_name": "string",
      "address_1": "string",
      "address_2": "string",
      "street_number": "string",
      "street_name": "string",
      "city": "string",
      "sub_locality": "string",
      "region": "string",
      "country": "string",
      "postal_code": "string",
      "phone": "string"
    },
    "billing_address": {
      "first_name": "string",
      "last_name": "string",
      "full_name": "string",
      "address_1": "string",
      "address_2": "string",
      "street_number": "string",
      "street_name": "string",
      "city": "string",
      "sub_locality": "string",
      "region": "string",
      "country": "string",
      "postal_code": "string",
      "phone": "string"
    },
    "items": [
      {
        "type": "PHYSICAL",
        "name": "string",
        "unit_price": 0,
        "quantity": 0,
        "discount_amount": 0,
        "total": 0
      }
    ]
  },
  "site_name": "string",
  "site_external_id": "string"
}
```
{% endtab %}
{% endtabs %}

#### payment\_gateway\_details

<table><thead><tr><th>Property</th><th>Type</th><th width="280">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the payment session.</td></tr><tr><td><strong>mode</strong></td><td><em>string</em></td><td>One of LIVE or TEST</td></tr><tr><td><strong>cancel_url</strong></td><td><em>string</em></td><td>URL to redirect the user to in case of cancellation.</td></tr><tr><td><strong>invoice</strong></td><td><em>object</em></td><td><a href="ecomm-payments.md#invoice">Invoice details.</a></td></tr><tr><td><strong>site_name</strong></td><td><em>string</em></td><td>The name of the site from which this purchase originated.</td></tr><tr><td><strong>site_external_id</strong></td><td><em>string</em></td><td>The external id of the site from which this purchase originated.</td></tr></tbody></table>

#### invoice

<table><thead><tr><th>Property</th><th>Type</th><th width="237">Description</th></tr></thead><tbody><tr><td><strong>purchase_id</strong></td><td><em>string</em></td><td>Reference id to the type of purchase. Currently will always be set to the cart id.</td></tr><tr><td><strong>purchase_type</strong></td><td><em>string</em></td><td>Currently always set to 'CART'.</td></tr><tr><td><strong>email</strong></td><td><em>string</em></td><td>Email address of the customer.</td></tr><tr><td><strong>language</strong></td><td><em>string</em></td><td>Language of the customer.</td></tr><tr><td><strong>currency</strong></td><td><em>string</em></td><td>Currency of the invoice.</td></tr><tr><td><strong>total</strong></td><td><em>number</em></td><td>Total amount of the invoice.</td></tr><tr><td><strong>shipping_address</strong></td><td><em>object</em></td><td>The <a href="ecomm-payments.md#address">shipping address</a> of the payment owner.</td></tr><tr><td><strong>billing_address</strong></td><td><em>object</em></td><td>The <a href="ecomm-payments.md#address">billing address</a> of the payment owner</td></tr><tr><td><strong>items</strong></td><td><em>object[]</em></td><td>All <a href="ecomm-payments.md#items">items</a> associated with this purchase.</td></tr></tbody></table>

#### address

<table><thead><tr><th>Property</th><th>Type</th><th width="348">Description</th></tr></thead><tbody><tr><td><strong>first_name</strong></td><td><em>string</em></td><td>First name of the payment owner.</td></tr><tr><td><strong>last_name</strong></td><td><em>string</em></td><td>Last name of the payment owner.</td></tr><tr><td><strong>full_name</strong></td><td><em>string</em></td><td>Full name of the payment owner.</td></tr><tr><td><strong>address_1</strong></td><td><em>string</em></td><td>Number and Street, concatenated.</td></tr><tr><td><strong>address_2</strong></td><td><em>string</em></td><td>Address complement (apt #, office #, floor level, etc.).</td></tr><tr><td><strong>street_number</strong></td><td><em>string</em></td><td>Standalone street number of the address</td></tr><tr><td><strong>street_name</strong></td><td><em>string</em></td><td>Standalone street name of the address</td></tr><tr><td><strong>city</strong></td><td><em>string</em></td><td>City name</td></tr><tr><td><strong>region</strong></td><td><em>string</em></td><td>The administrative region (depending on country, this can be a state, province, department, etc.).</td></tr><tr><td><strong>sub_locality</strong></td><td><em>string</em></td><td>The sub locality of the address (neighborhood, county, etc.).</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>ISO 3166 2-letters ISO country code. Ref: <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes</a></td></tr><tr><td><strong>postal_code</strong></td><td><em>string</em></td><td>Postal code.</td></tr><tr><td><strong>phone</strong></td><td><em>string</em></td><td>Phone number associated with the address</td></tr></tbody></table>

#### items

<table><thead><tr><th>Property</th><th>Type</th><th width="248">Description</th></tr></thead><tbody><tr><td><strong>type</strong></td><td><em>string</em></td><td>Can be "PHYSICAL", "DIGITAL", "TAX", "SHIPPING", or "DISCOUNT".</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>Name of the invoice line item.</td></tr><tr><td><strong>unit_price</strong></td><td><em>number</em></td><td>Price per unit of the invoice line item.</td></tr><tr><td><strong>quantity</strong></td><td><em>number</em></td><td>Quantity of the invoice line item.</td></tr><tr><td><strong>discover_amount</strong></td><td><em>number</em></td><td>Amount discounted from the original price of the invoice line item.</td></tr><tr><td><strong>total</strong></td><td><em>number</em></td><td>Total for the invoice line item.</td></tr></tbody></table>

## Get Payment Session

{% swagger method="get" baseUrl=" https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="Get Payment Session" path="/integrationhub/application/site/{site_name}/ecommerce/payment-sessions/{session_id}" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="session_id" type="string" required="true" %}
The unique identifier for the payment session
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "id": "string",
  "mode": "LIVE",
  "cancel_url": "string",
  "invoice": {
    "purchase_id": "string",
    "purchase_type": "string",
    "email": "string",
    "language": "string",
    "currency": "string",
    "total": 0,
    "shipping_address": {
      "first_name": "string",
      "last_name": "string",
      "full_name": "string",
      "address_1": "string",
      "address_2": "string",
      "street_number": "string",
      "street_name": "string",
      "city": "string",
      "sub_locality": "string",
      "region": "string",
      "country": "string",
      "postal_code": "string",
      "phone": "string"
    },
    "billing_address": {
      "first_name": "string",
      "last_name": "string",
      "full_name": "string",
      "address_1": "string",
      "address_2": "string",
      "street_number": "string",
      "street_name": "string",
      "city": "string",
      "sub_locality": "string",
      "region": "string",
      "country": "string",
      "postal_code": "string",
      "phone": "string"
    },
    "items": [
      {
        "type": "PHYSICAL",
        "name": "string",
        "unit_price": 0,
        "quantity": 0,
        "discount_amount": 0,
        "total": 0
      }
    ]
  },
  "site_name": "string",
  "site_external_id": "string"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-sessions/session_id \
     --header 'Authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Confirm Payment

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Confirm Payment" path="/integrationhub/application/site/{site_name}/ecommerce/payment-sessions/{session_id}/confirm" %}
{% swagger-description %}
Note that properties can differ based on the state of the payment.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="session_id" type="string" required="true" %}
The unique identifier for the payment
{% endswagger-parameter %}

{% swagger-parameter in="body" name="session_id" type="string" required="true" %}
ID returned by the payment session retrieval
{% endswagger-parameter %}

{% swagger-parameter in="body" name="state" type="string" required="true" %}
PROCESSED or FAILED
{% endswagger-parameter %}

{% swagger-parameter in="body" name="links" type="object" %}
refunds: URL that our servers will POST to when a refund is issued from the merchant dashboard
{% endswagger-parameter %}

{% swagger-parameter in="body" name="transaction_id" type="string" %}
Required only if state is PROCESSED . Unique identifier from your payment gateway to assign to the order
{% endswagger-parameter %}

{% swagger-parameter in="body" name="instructions" type="string" %}
Optionally define if state is PROCESSED. Information text diplayed in the checkout confirmation screen
{% endswagger-parameter %}

{% swagger-parameter in="body" name="icon" type="string" %}
Optionally define if state is PROCESSED. Image url to display in the checkout confirmation screen
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "return_url": "string"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-sessions/session_id/confirm \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
