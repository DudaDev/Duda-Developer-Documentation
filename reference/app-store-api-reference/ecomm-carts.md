---
description: Native Store Only
---

# eComm Carts

## Cart Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
  "mode": "LIVE",
  "status": "IN_PROGRESS",
  "language": "en",
  "email": "john.doe@example.org",
  "currency": "USD",
  "items": [
    {
      "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
      "added": "2023-02-01T18:24:26.700Z",
      "product_id": "string",
      "variation_id": "string",
      "external_product_id": "string",
      "external_variation_id": "string"
      "name": "My product name",
      "image": "https://example.org/image.jpg",
      "options": [
        {
          "name": "Color",
          "value": "Red"
        }
      ],
      "shippable": true,
      "quantity": 3,
      "unit_price": "25.35",
      "unit_weight": "20.16",
      "unit_dimensions": {
        "height": "20",
        "width": "30",
        "length": "30"
      },
      "discounts": [
        {
          "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
          "name": "My discount",
          "savings": "10.25",
          "type": "RATE"
        }
      ],
      "taxes": [
        {
          "name": "Federal tax",
          "rate": "0.15",
          "amount": "10.25"
        }
      ],
      "total": "75.96",
      "combined_weight": "60.48",
      "metadata": {}
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
    "name": "Express shipping",
    "cost": "12.45"
  },
  "shipping_instructions": "string",
  "discounts": [
    {
      "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
      "savings": "42.36",
      "name": "15OFF",
      "type": "RATE"
    }
  ],
  "taxes": [
    {
      "name": "Federal tax",
      "amount": "10.23",
      "rate": "0.15"
    }
  ],
  "subtotal": "10.54",
  "total": "10.54",
  "created": "2023-02-01T18:24:26.700Z",
  "updated": "2023-02-01T18:24:26.700Z",
  "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (HTML, like Gecko) Chrome/105.0.0.0 Safari/537.36",
  "ip_address": "1.1.1.1",
  "metadata": "string"
}
```
{% endtab %}
{% endtabs %}

#### Cart Items

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>The unique identifier for this cart item. note: this is different from the product identifier</td></tr><tr><td><strong>added</strong></td><td><em>string</em></td><td>Datetime stamp of when this item was added to the cart.</td></tr><tr><td><strong>product_id</strong></td><td><em>string</em></td><td>The unique identifier for the product backing this cart item.</td></tr><tr><td><strong>variation_id</strong></td><td><em>string</em></td><td>The unique identifier for the product variation backing this cart item.</td></tr><tr><td><strong>external_product_id</strong></td><td><em>string</em></td><td>The external id of the product backing this cart item.</td></tr><tr><td><strong>external_variation_id</strong></td><td><em>string</em></td><td>The external id of the product variation backing this cart item.</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the product backing this cart item.</td></tr><tr><td><strong>image</strong></td><td><em>string</em></td><td>URL to an image of the product backing this cart item.</td></tr><tr><td><strong>options</strong></td><td><em>array</em></td><td>An array of <a href="ecomm-carts.md#options">options</a> chosen by the cart owner for the product backing this cart item.</td></tr><tr><td><strong>shippable</strong></td><td><em>bool</em></td><td>Indicates if this item requires shipping.</td></tr><tr><td><strong>quantity</strong></td><td><em>integer</em></td><td>The number of this item, variation and option combination in the cart.</td></tr><tr><td><strong>unit_price</strong></td><td><em>string</em></td><td>The price per unit of this cart item.</td></tr><tr><td><strong>unit_weight</strong></td><td><em>float</em></td><td>The weight (in grams) per unit of this cart item.</td></tr><tr><td><strong>unit_dimensions</strong></td><td><em>object</em></td><td>The per unit <code>height</code>, <code>weight</code> and <code>length</code> (in cm) of this cart item.</td></tr><tr><td><strong>discounts</strong></td><td><em>array</em></td><td>An array of <a href="ecomm-carts.md#discounts">discounts</a> for this cart item. This value applies across the entire quantity of the item.</td></tr><tr><td><strong>taxes</strong></td><td><em>array</em></td><td>An array of <a href="ecomm-carts.md#taxes">taxes</a> for this cart item. This value applies across the entire quantity of the item.</td></tr><tr><td><strong>total</strong></td><td><em>string</em></td><td>The total amount for all units in this cart item.</td></tr><tr><td><strong>combined_weight</strong></td><td><em>string</em></td><td>The combined weight (in grams) of all the items in the cart.</td></tr><tr><td><strong>metadata</strong></td><td><em>object</em></td><td></td></tr></tbody></table>

#### Address

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>first_name</strong></td><td><em>string</em></td><td>First Name attached to the address.</td></tr><tr><td><strong>last_name</strong></td><td><em>string</em></td><td>Last Name attached to the address.</td></tr><tr><td><strong>full_name</strong></td><td><em>string</em></td><td>Full Name attached to the address.</td></tr><tr><td><strong>address_1</strong></td><td><em>string</em></td><td>The first line of the address.</td></tr><tr><td><strong>address_2</strong></td><td><em>string</em></td><td>The second line of the address.</td></tr><tr><td><strong>street_number</strong></td><td><em>string</em></td><td>The street number note: this may be part of the address_1 or address_2 values, but is available here as a separate value.</td></tr><tr><td><strong>street_name</strong></td><td><em>string</em></td><td>The street name note: this may be part of the address_1 or address_2 values, but is available here as a separate value.</td></tr><tr><td><strong>city</strong></td><td><em>string</em></td><td>Name of city attached to the address.</td></tr><tr><td><strong>sub_locality</strong></td><td><em>string</em></td><td>Sub-locality attached to the address (ex: county or district name).</td></tr><tr><td><strong>region</strong></td><td><em>string</em></td><td>Region attached to the address (ex. the state or province name).</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>Country attached to the address.</td></tr><tr><td><strong>postal_code</strong></td><td><em>string</em></td><td>Postal code attached to the address.</td></tr><tr><td><strong>phone</strong></td><td><em>string</em></td><td>Phone number of contact located at this address.</td></tr></tbody></table>

#### Shipping Method

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>Name of the shipping method.</td></tr><tr><td><strong>cost</strong></td><td><em>string</em></td><td>Total cost for this shipping method.</td></tr></tbody></table>

#### Discounts

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>The unique identifier for this discount.</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>Descriptive name of the discount.</td></tr><tr><td><strong>savings</strong></td><td><em>string</em></td><td>Total amount saved by this discount.</td></tr><tr><td><strong>type</strong></td><td><em>string</em></td><td>The type of discount. Will be one of RATE (percentage off of the initial price) or AMOUNT (fixed discount amount off the initial price)</td></tr></tbody></table>

#### Taxes

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>Descriptive name of the tax.</td></tr><tr><td><strong>amount</strong></td><td><em>string</em></td><td>The total amount of this tax.</td></tr><tr><td><strong>rate</strong></td><td><em>float</em></td><td>The rate applied for this tax in decimal format (ex: .15 or .05).</td></tr></tbody></table>

#### Options

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>Descriptive name of the option.</td></tr><tr><td><strong>value</strong></td><td><em>string</em></td><td>Value of the specified option.</td></tr></tbody></table>

## List Carts

{% swagger method="get" baseUrl="https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="List Carts" path="/integrationhub/application/sites/multiscreen/{site_name}/ecommerce/carts" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="status" type="string" %}
One of IN_PROGRESS or ABANDONED
{% endswagger-parameter %}

{% swagger-parameter in="query" name="mode" type="string" %}
One of LIVE or TEST
{% endswagger-parameter %}

{% swagger-parameter in="query" name="cursor" type="string" %}
Valid cart id. This value will be used for cursor pagination to return all items in the sort order after this id.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="int32" %}
Number of results to be returned
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "cursor": "string",
  "has_more_results": true,
  "results": [
    {
      "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
      "mode": "LIVE",
      "status": "IN_PROGRESS",
      "language": "en",
      "email": "john.doe@example.org",
      "currency": "USD",
      "items": [
        {
          "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
          "added": "2023-02-01T17:56:28.594Z",
          "product_id": "string",
          "variation_id": "string",
          "external_product_id": "string",
          "external_variation_id": "string"
          "name": "My product name",
          "image": "https://example.org/image.jpg",
          "options": [
            {
              "name": "Color",
              "value": "Red"
            }
          ],
          "shippable": true,
          "quantity": 3,
          "unit_price": 25.35,
          "unit_weight": 20.16,
          "unit_dimensions": {
            "height": 20,
            "width": 30,
            "length": 30
          },
          "discounts": [
            {
              "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
              "name": "My discount",
              "savings": 10.25,
              "type": "RATE"
            }
          ],
          "taxes": [
            {
              "name": "Federal tax",
              "rate": 0.15,
              "amount": 10.25
            }
          ],
          "total": 75.96,
          "combined_weight": 60.48,
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
        "name": "Express shipping",
        "cost": 12.45
      },
      "shipping_instructions": "string",
      "discounts": [
        {
          "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
          "savings": 42.36,
          "name": "15OFF",
          "type": "RATE"
        }
      ],
      "taxes": [
        {
          "name": "Federal tax",
          "amount": 10.23,
          "rate": 0.15
        }
      ],
      "subtotal": 10.54,
      "total": 10.54,
      "created": "2023-02-01T17:56:28.594Z",
      "updated": "2023-02-01T17:56:28.594Z",
      "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (HTML, like Gecko) Chrome/105.0.0.0 Safari/537.36",
      "ip_address": "1.1.1.1",
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/sites/multiscreen/site_name/ecommerce/carts \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Get Cart

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="get" summary="Get Cart" path="/integrationhub/application/sites/multiscreen/{site_name}/ecommerce/carts/{cart_id}" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="cart_id" type="string" required="true" %}
The unique identifier for the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
  "mode": "LIVE",
  "status": "IN_PROGRESS",
  "language": "en",
  "email": "john.doe@example.org",
  "currency": "USD",
  "items": [
    {
      "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
      "added": "2023-02-01T18:24:26.700Z",
      "product_id": "string",
      "variation_id": "string",
      "external_product_id": "string",
      "external_variation_id": "string",
      "name": "My product name",
      "image": "https://example.org/image.jpg",
      "options": [
        {
          "name": "Color",
          "value": "Red"
        }
      ],
      "shippable": true,
      "quantity": 3,
      "unit_price": 25.35,
      "unit_weight": 20.16,
      "unit_dimensions": {
        "height": 20,
        "width": 30,
        "length": 30
      },
      "discounts": [
        {
          "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
          "name": "My discount",
          "savings": 10.25,
          "type": "RATE"
        }
      ],
      "taxes": [
        {
          "name": "Federal tax",
          "rate": 0.15,
          "amount": 10.25
        }
      ],
      "total": 75.96,
      "combined_weight": 60.48,
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
    "name": "Express shipping",
    "cost": 12.45
  },
  "shipping_instructions": "string",
  "discounts": [
    {
      "id": "e40b1abb-af80-4a4e-b6f0-4746c0e8a90a",
      "savings": 42.36,
      "name": "15OFF",
      "type": "RATE"
    }
  ],
  "taxes": [
    {
      "name": "Federal tax",
      "amount": 10.23,
      "rate": 0.15
    }
  ],
  "subtotal": 10.54,
  "total": 10.54,
  "created": "2023-02-01T18:24:26.700Z",
  "updated": "2023-02-01T18:24:26.700Z",
  "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (HTML, like Gecko) Chrome/105.0.0.0 Safari/537.36",
  "ip_address": "1.1.1.1",
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/sites/multiscreen/site_name/ecommerce/carts/cart_id \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
