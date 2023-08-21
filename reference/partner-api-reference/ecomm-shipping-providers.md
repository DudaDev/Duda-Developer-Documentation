---
description: Native Store Only
---

# eComm Shipping Providers

## Shipping Provider Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "id": "string",
  "live_shipping_methods_url": "string",
  "test_shipping_methods_url": "string"
}
```
{% endtab %}
{% endtabs %}

#### shipping\_provider\_info

<table><thead><tr><th width="292">Property</th><th>Type</th><th width="291">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the external shipping providers.</td></tr><tr><td><strong>live_shipping_methods_url</strong></td><td><em>string</em></td><td>Url that duda eCommerce's service will contact to retrieve the available shipping methods for a cart in live mode.</td></tr><tr><td><strong>test_shipping_methods_url</strong></td><td><em>string</em></td><td>Url that duda eCommerce's service will contact to retrieve the available shipping methods for a cart in test mode.</td></tr></tbody></table>

## List Shipping Providers

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Shipping Providers" path="/sites/multiscreen/{site_name}/ecommerce/shipping-rates/external" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "offset": 0,
  "limit": 0,
  "total_responses": 0,
  "results": [
    {
      "id": "string",
      "live_shipping_methods_url": "string",
      "test_shipping_methods_url": "string"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/shipping-rates/external \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Shipping Providers

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Create Shipping Providers" path="/sites/multiscreen/{site_name}/ecommerce/shipping-rates/external" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="live_shipping_rates_url" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="test_shipping_rates_url" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="201: Created" description="object" %}
```json
{
  "id": "string",
  "live_shipping_methods_url": "string",
  "test_shipping_methods_url": "string"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/shipping-rates/external \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Get Shipping Provider

{% swagger method="get" path="/sites/multiscreen/{site_name}/ecommerce/shipping-rates/external/{id}" baseUrl="https://api.duda.co/api" summary="Get Shipping Provider" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="string" required="true" %}
The unique identifier for the target Shipping Rate.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "id": "string",
  "live_shipping_methods_url": "string",
  "test_shipping_methods_url": "string"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/shipping-rates/external/id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Shipping Provider

{% swagger method="patch" path="/sites/multiscreen/{site_name}/ecommerce/shipping-rates/external/{id}" baseUrl="https://api.duda.co/api" summary="Update Shipping Provider" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="product_id" type="string" required="true" %}
The unique identifier for the target Shipping Rate.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="live_shipping_rates_url" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="test_shipping_rates_url" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "description": "The most amazing t shirt ever sold",
  "external_id": "KTP9XGbSg2",
  "id": "IakdKbiUiK",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "options": [
    {
      "choices": [
        {
          "id": "db3je27rg7",
          "value": "45"
        }
      ],
      "id": "WMd1xylGrp",
      "name": "Shirt size"
    }
  ],
  "prices": [
    {
      "compare_at_price": "19.99",
      "currency": "USD",
      "price": "12.34"
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE",
  "variations": [
    {
      "external_id": "KTP9XGbSg2",
      "id": "KTP9XGbSg2",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "options": [
        {
          "choice_id": "db3je27rg7",
          "choice_value": "45",
          "option_id": "WMd1xylGrp",
          "option_name": "Shirt size"
        }
      ],
      "price_difference": "string",
      "quantity": 25,
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "stock_status": "IN_STOCK, OUT_OF_STOCK"
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
curl --request PATCH \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/shipping-rates/external/id \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
    "live_shipping_rates_url": "string"
}
'
```
{% endtab %}
{% endtabs %}

## Delete Shipping Provider

{% swagger method="delete" path="/sites/multiscreen/{site_name}/ecommerce/shipping-rates/external/{id}" baseUrl="https://api.duda.co/api" summary="Delete Shipping Provider" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="string" required="true" %}
The unique identifier for the target Shipping Rate.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/shipping-rates/external/id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
