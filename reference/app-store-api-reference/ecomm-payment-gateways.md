---
description: Native Store Only
---

# eComm Payment Gateways

## Payment Gateway Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "id": "string",
  "live_payment_methods_url": "string",
  "test_payment_methods_url": "string"
}
```
{% endtab %}
{% endtabs %}

#### payment\_gateway

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>System identifier of the custom payment gateway.</td><td>No</td></tr><tr><td><strong>live_payment_methods_url</strong></td><td><em>string</em></td><td>The payment methods API endpoint that will be called to retrieve the available payment methods for the cart in LIVE mode.</td><td>Yes</td></tr><tr><td><strong>test_payment_methods_url</strong></td><td><em>string</em></td><td>The payment methods API endpoint that will be called to retrieve the available payment methods for the cart in TEST mode. This URL can be the same as live_payment_methods_url.</td><td>Yes</td></tr></tbody></table>

## List Payment Gateways

{% swagger method="get" baseUrl=" https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="List Payment Gateways" path="/integrationhub/application/site/{site_name}/ecommerce/payment-gateways" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="int32" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="int32" %}

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
  "offset": 0,
  "limit": 0,
  "total_responses": 0,
  "results": [
    {
      "id": "string",
      "live_payment_methods_url": "string",
      "test_payment_methods_url": "string"
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
     --url 'https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-gateways?offset=0&limit=50' \
     --header 'accept: application/json' \
     --header 'authorization: Basic cnVzc1dhczpoZXJlIQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Get Payment Gateway

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="get" summary="Get Payment Gateway" path="/integrationhub/application/site/{site_name}/ecommerce/payment-gateways/{id}" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="gateway_id" type="string" required="true" %}
The unique identifier for the target Payment Gateway.
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
  "live_payment_methods_url": "string",
  "test_payment_methods_url": "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-gateways/id \
     --header 'accept: application/json' \
     --header 'authorization: Basic cnVzc1dhczpoZXJlIQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Create Payment Gateway

{% swagger method="post" path="/integrationhub/application/site/{site_name}/ecommerce/payment-gateways" baseUrl=" https://api-sandbox.duda.co/api" summary="Create Payment Gateway" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="live_payment_methods_url" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="test_payment_methods_url" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="image" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="icons" type="array of strings" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="object" %}
```json
{
  "id": "string",
  "live_payment_methods_url": "string",
  "test_payment_methods_url": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "icons": [
    "string"
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
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-gateways \
     --header 'accept: application/json' \
     --header 'authorization: Basic cnVzc1dhczpoZXJlIQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update Payment Gateway

{% swagger method="patch" path="/integrationhub/application/site/{site_name}/ecommerce/payment-gateways/{id}" baseUrl=" https://api-sandbox.duda.co/api" summary="Update Payment Gateway" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="gateway_id" type="string" required="true" %}
The unique identifier for the target Payment Gateway.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="live_payment_methods_url" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="test_payment_methods_url" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="image" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="icons" type="array of strings" %}

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
  "live_payment_methods_url": "string",
  "test_payment_methods_url": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "icons": [
    "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-gateways/id \
     --header 'accept: application/json' \
     --header 'authorization: Basic cnVzc1dhczpoZXJlIQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Delete Payment Gateway

{% swagger method="delete" path="/integrationhub/application/site/{site_name}/ecommerce/payment-gateways/{id}" baseUrl=" https://api-sandbox.duda.co/api" summary="Delete Payment Gateway" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="gateway_id" type="string" required="true" %}
The unique identifier for the target Payment Gateway.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/payment-gateways/id \
     --header 'accept: application/json' \
     --header 'authorization: Basic cnVzc1dhczpoZXJlIQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
