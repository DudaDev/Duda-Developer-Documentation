---
description: Native Store Only
---

# eComm Orders

## Order Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "source": "CHECKOUT",
  "mode": "LIVE",
  "id": "string",
  "external_id": "string",
  "status": "IN_PROGRESS",
  "email": "string",
  "invoice_number": "string",
  "items": [
    {
      "id": "string",
      "product_id": "string",
      "variation_id": "string",
      "external_product_id": "string",
      "external_variation_id": "string",
      "name": "string",
      "image": "string",
      "sku": "string",
      "options": [
        {
          "name": "string",
          "value": "string"
        }
      ],
      "quantity": 0,
      "shippable": true,
      "unit_price": 0,
      "unit_weight": 0,
      "unit_dimensions": {
        "height": 0,
        "width": 0,
        "length": 0
      },
      "total": 0,
      "combined_weight": 0,
      "metadata": "string"
    }
  ],
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
  "shipping_method": {
    "name": "string",
    "cost": 0
  },
  "shipping_instructions": "string",
  "discounts": [
    {
      "id": "string",
      "savings": 0,
      "name": "string",
      "type": "string"
    }
  ],
  "taxes": [
    {
      "name": "string",
      "amount": 0,
      "rate": 0
    }
  ],
  "subtotal": 0,
  "total": 0,
  "payment": {
    "transaction_id": "string",
    "status": "PAID",
    "currency": "string",
    "method": "string",
    "card_brand": "NULL",
    "card_last_4": "string"
  },
  "refunds": [
    {}
  ],
  "tracking_url": "string",
  "tracking_number": "string",
  "created": "2023-08-02T14:52:29.729Z",
  "user_agent": "string",
  "ip_address": "string",
  "metadata": "string"
}
```
{% endtab %}
{% endtabs %}

#### order\_details

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>mode</strong></td><td><em>string</em></td><td>Can be "TEST" or "LIVE".</td></tr><tr><td><strong>id</strong></td><td><em>string</em></td><td>Unique identifier of the order.</td></tr><tr><td><strong>status</strong></td><td><em>string</em></td><td>Can be "IN_PROGRESS", "PROCESSED", "DISPUTED", "SHIPPED", "DELIVERED", "PENDING", "CANCELLED", or "DISPATCHED".</td></tr><tr><td><strong>email</strong></td><td><em>string</em></td><td>Email associated with the order.</td></tr><tr><td><strong>invoice_number</strong></td><td><em>string</em></td><td>Invoice number of the order.</td></tr><tr><td><strong>items</strong></td><td><em>object[]</em></td><td>The <a href="ecomm-orders.md#items">items</a> in the order.</td></tr><tr><td><strong>billing_address</strong></td><td><em>object</em></td><td>The <a href="ecomm-orders.md#address">billing address</a> details of the order owner.</td></tr><tr><td><strong>shipping_address</strong></td><td><em>object</em></td><td>The <a href="ecomm-orders.md#address">shipping address</a> details of the order owner.</td></tr><tr><td><strong>shipping_method</strong></td><td><em>object</em></td><td>The <a href="ecomm-orders.md#shipping_method">shipping method</a> of the order.</td></tr><tr><td><strong>discounts</strong></td><td><em>object[]</em></td><td>The <a href="ecomm-orders.md#discounts">discounts</a> applied to the order.</td></tr><tr><td><strong>taxes</strong></td><td><em>object[]</em></td><td>The <a href="ecomm-orders.md#taxes">taxes</a> applied to the order.</td></tr><tr><td><strong>subtotal</strong></td><td><em>number</em></td><td>Cost of the order before any additions (i.e.: Taxes, Shipping, etc.)</td></tr><tr><td><strong>total</strong></td><td><em>number</em></td><td>The total cost of the order.</td></tr><tr><td><strong>payment</strong></td><td><em>object</em></td><td>The <a href="ecomm-orders.md#payment">payment</a> information of the order.</td></tr><tr><td><strong>refunds</strong></td><td><em>object[]</em></td><td>The <a href="ecomm-orders.md#refunds">refunds</a> applied to the order.</td></tr><tr><td><strong>tracking_url</strong></td><td><em>string</em></td><td>Public URL from the shipping provider to get updates on the shipped order.</td></tr><tr><td><strong>tracking_number</strong></td><td><em>string</em></td><td>Public tracking number associated to the order.</td></tr><tr><td><strong>created</strong></td><td><em>string</em></td><td>Date that indicates when the order was completed.</td></tr><tr><td><strong>user_agent</strong></td><td><em>string</em></td><td>User agent of the customer who made the order.</td></tr><tr><td><strong>ip_address</strong></td><td><em>string</em></td><td>IP address of the customer who made the order.</td></tr><tr><td><strong>metadata</strong></td><td><em>string</em></td><td>Metadata associated with the order.</td></tr></tbody></table>

#### items

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the line item.</td></tr><tr><td><strong>product_id</strong></td><td><em>string</em></td><td>The unique identifier for the product backing this order item.</td></tr><tr><td><strong>variation_id</strong></td><td><em>string</em></td><td>The unique identifier for the product variation backing this order item.</td></tr><tr><td><strong>external_product_id</strong></td><td><em>string</em></td><td>The external id of the product backing this order item.</td></tr><tr><td><strong>external_variation_id</strong></td><td><em>string</em></td><td>The external id of the product variation backing this order item.</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>Display name of the line item.</td></tr><tr><td><strong>image</strong></td><td><em>string</em></td><td>Display image of the line item.</td></tr><tr><td><strong>options</strong></td><td><em>object[]</em></td><td>Options selected by the customer associated with the line item.</td></tr><tr><td><strong>shippable</strong></td><td><em>bool</em></td><td>Indicates if this item requires shipping.</td></tr><tr><td><strong>quantity</strong></td><td><em>number</em></td><td>Quantity bought for this item.</td></tr><tr><td><strong>unit_price</strong></td><td><em>number</em></td><td>Price of a single unit of this line item.</td></tr><tr><td><strong>unit_weight</strong></td><td><em>number</em></td><td>Weight of a single unit of this line item.</td></tr><tr><td><strong>unit_dimensions</strong></td><td><em>object</em></td><td>Dimensions of this line item.</td></tr><tr><td><strong>total</strong></td><td><em>number</em></td><td>Total price of this line item (quantity * unit price).</td></tr><tr><td><strong>combined_weight</strong></td><td><em>number</em></td><td>Total weight of this line item (quantity * unit weight).</td></tr></tbody></table>

#### options

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>Name of the option.</td><td>Yes</td></tr><tr><td><strong>value</strong></td><td><em>string</em></td><td>Value of the option.</td><td>Yes</td></tr></tbody></table>

#### unit\_dimensions

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>height</strong></td><td><em>number</em></td><td>Height of a single unit of this line item.</td></tr><tr><td><strong>width</strong></td><td><em>number</em></td><td>Width of a single unit of this line item.</td></tr><tr><td><strong>length</strong></td><td><em>number</em></td><td>Length of a single unit of this line item.</td></tr></tbody></table>

#### address

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>first_name</strong></td><td><em>string</em></td><td>First Name attached to the address.</td></tr><tr><td><strong>last_name</strong></td><td><em>string</em></td><td>Last Name attached to the address.</td></tr><tr><td><strong>full_name</strong></td><td><em>string</em></td><td>Full Name attached to the address.</td></tr><tr><td><strong>address_1</strong></td><td><em>string</em></td><td>The first line of the address.</td></tr><tr><td><strong>address_2</strong></td><td><em>string</em></td><td>The second line of the address.</td></tr><tr><td><strong>street_number</strong></td><td><em>string</em></td><td>The street number note: this may be part of the address_1 or address_2 values, but is available here as a separate value.</td></tr><tr><td><strong>street_name</strong></td><td><em>string</em></td><td>The street name note: this may be part of the address_1 or address_2 values, but is available here as a separate value.</td></tr><tr><td><strong>city</strong></td><td><em>string</em></td><td>Name of city attached to the address.</td></tr><tr><td><strong>sub_locality</strong></td><td><em>string</em></td><td>Sub-locality attached to the address (ex: county or district name).</td></tr><tr><td><strong>region</strong></td><td><em>string</em></td><td>Region attached to the address (ex. the state or province name).</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>Country attached to the address.</td></tr><tr><td><strong>postal_code</strong></td><td><em>string</em></td><td>Postal code attached to the address.</td></tr><tr><td><strong>phone</strong></td><td><em>string</em></td><td>Phone number of contact located at this address.</td></tr></tbody></table>

#### shipping\_method

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>method</strong></td><td><em>string</em></td><td>Name of the shipping method selected on the order.</td></tr><tr><td><strong>cost</strong></td><td><em>number</em></td><td>The cost incurred for the order by the shipping method.</td></tr></tbody></table>

#### discounts

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the discount resource that was added to this order.</td></tr><tr><td><strong>savings</strong></td><td><em>number</em></td><td>The amount of money that was saved on the total of the order using the discount.</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the discount.</td></tr><tr><td><strong>type</strong></td><td><em>string</em></td><td>The type of discount that was applied to the order.</td></tr></tbody></table>

#### taxes

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>Name of the tax.</td></tr><tr><td><strong>amount</strong></td><td><em>number</em></td><td>Amount of the tax when applied to the given order.</td></tr><tr><td><strong>rate</strong></td><td><em>number</em></td><td>Percentage rate of the amount that was added for this tax.</td></tr></tbody></table>

#### payment

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>transaction_id</strong></td><td><em>string</em></td><td>Unique identifier given by the payment provider used to identify the payment made for the order.</td></tr><tr><td><strong>status</strong></td><td><em>string</em></td><td>Can be "PAID", "DEFERRED", "PAID_DEFERRED", "CHARGED_BACK", "REFUNDED", "PAIDOUT", "PENDING", "FAILED", "EXPIRED", "CANCELLED", "OPEN", or "AUTHORIZED".</td></tr><tr><td><strong>currency</strong></td><td><em>string</em></td><td>Currency of the order.</td></tr><tr><td><strong>method</strong></td><td><em>string</em></td><td>Payment method used at checkout for this order.</td></tr><tr><td><strong>card_brand</strong></td><td><em>string</em></td><td>Can be "NULL", "VISA", "MASTERCARD", "AMEX", "DINERS_CLUB", "DISCOVER", "J_C_B", "CARD_BLEUE", "DANKORT", "CARTA_SI", "POSTEPAY", "MAESTRO", "LASER", "UNIONPAY", or "OTHER".</td></tr><tr><td><strong>card_last_4</strong></td><td><em>string</em></td><td>Card last 4 digits used to pay the order.</td></tr></tbody></table>

#### refunds

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the refund.</td></tr><tr><td><strong>amount</strong></td><td><em>number</em></td><td>Refunded amount.</td></tr><tr><td><strong>reason</strong></td><td><em>string</em></td><td>Reason written by the merchant for the refund.</td></tr><tr><td><strong>created</strong></td><td><em>string</em></td><td>Date of the refund.</td></tr></tbody></table>

## List Orders

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Orders" path="/sites/multiscreen/{site_name}/ecommerce/orders" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="int32" %}
Zero-based offset for elements (0..N)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="int32" %}
The size of the page to be returned
{% endswagger-parameter %}

{% swagger-parameter in="query" name="sort" type="string" %}
Property used to sort orders
{% endswagger-parameter %}

{% swagger-parameter in="query" name="direction" type="string" %}
The sort direction, either "asc" or "desc"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "offset": 0,
  "limit": 0,
  "total_responses": 0,
  "results": [
    {
      "mode": "TEST",
      "id": "string",
      "status": "IN_PROGRESS",
      "email": "string",
      "invoice_number": "string",
      "items": [
        {
          "id": "string",
          "product_id": "string",
          "variation_id": "string",
          "external_product_id": "string",
          "external_variation_id": "string",
          "name": "string",
          "image": "string",
          "options": [
            {
              "name": "string",
              "value": "string"
            }
          ],
          "quantity": 0,
          "shippable": true,
          "unit_price": 0,
          "unit_weight": 0,
          "unit_dimensions": {
            "height": 0,
            "width": 0,
            "length": 0
          },
          "total": 0,
          "combined_weight": 0,
          "metadata": "string"
        }
      ],
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
      "shipping_method": {
        "name": "string",
        "cost": 0
      },
      "shipping_instructions": "string",
      "discounts": [
        {
          "id": "string",
          "savings": 0,
          "name": "string",
          "type": "string"
        }
      ],
      "taxes": [
        {
          "name": "string",
          "amount": 0,
          "rate": 0
        }
      ],
      "subtotal": 0,
      "total": 0,
      "payment": {
        "transaction_id": "string",
        "status": "PAID",
        "currency": "string",
        "method": "string",
        "card_brand": "NULL",
        "card_last_4": "string"
      },
      "refunds": [
        {
          "id": "string",
          "amount": 0,
          "reason": "string",
          "created": "2023-02-17T19:01:36.352Z"
        }
      ],
      "tracking_url": "string",
      "tracking_number": "string",
      "created": "2023-02-17T19:01:36.352Z",
      "user_agent": "string",
      "ip_address": "string",
      "metadata": "string"
    }
  ]
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
     --url 'https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/orders?offset=0' \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Order

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Order" path="/sites/multiscreen/{site_name}/ecommerce/orders/{order_id}" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="order_id" type="string" required="true" %}
The unique identifier for the target Order.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "mode": "TEST",
  "id": "string",
  "status": "IN_PROGRESS",
  "email": "string",
  "invoice_number": "string",
  "items": [
    {
      "id": "string",
      "product_id": "string",
      "variation_id": "string",
      "external_product_id": "string",
      "external_variation_id": "string",
      "name": "string",
      "image": "string",
      "options": [
        {
          "name": "string",
          "value": "string"
        }
      ],
      "quantity": 0,
      "shippable": true,
      "unit_price": 0,
      "unit_weight": 0,
      "unit_dimensions": {
        "height": 0,
        "width": 0,
        "length": 0
      },
      "total": 0,
      "combined_weight": 0,
      "metadata": "string"
    }
  ],
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
  "shipping_method": {
    "name": "string",
    "cost": 0
  },
  "shipping_instructions": "string",
  "discounts": [
    {
      "id": "string",
      "savings": 0,
      "name": "string",
      "type": "string"
    }
  ],
  "taxes": [
    {
      "name": "string",
      "amount": 0,
      "rate": 0
    }
  ],
  "subtotal": 0,
  "total": 0,
  "payment": {
    "transaction_id": "string",
    "status": "PAID",
    "currency": "string",
    "method": "string",
    "card_brand": "NULL",
    "card_last_4": "string"
  },
  "refunds": [
    {
      "id": "string",
      "amount": 0,
      "reason": "string",
      "created": "2023-02-17T19:01:36.318Z"
    }
  ],
  "tracking_url": "string",
  "tracking_number": "string",
  "created": "2023-02-17T19:01:36.318Z",
  "user_agent": "string",
  "ip_address": "string",
  "metadata": "string"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/orders/order_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
