---
description: Native Store Only
---

# eComm

## Settings Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "default_currency": "string",
  "business_name": "string",
  "business_address": {
    "address_1": "string",
    "address_2": "string",
    "city": "string",
    "sub_locality": "string",
    "region": "string",
    "country": "string",
    "postal_code": "string"
  },
  "time_zone": "string",
  "enabled_countries": [
    "string"
  ],
  "send_email_notifications": true,
  "cart_settings": {
    "split_name_field": true,
    "split_address_1_field": true,
    "display_instruction_field": true,
    "display_phone_field": true
  }
}
```
{% endtab %}
{% endtabs %}

#### settings

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>default_currency</strong></td><td><em>string</em></td><td>ISO 4217 3-letters currency code. Ref: <a href="https://en.wikipedia.org/wiki/ISO_4217">https://en.wikipedia.org/wiki/ISO_4217</a>.</td></tr><tr><td><strong>business_name</strong></td><td><em>string</em></td><td>The full name of the business.</td></tr><tr><td><strong>business_address</strong></td><td><em>object</em></td><td>The <a href="ecomm.md#business_address">address</a> if the business.</td></tr><tr><td><strong>time_zone</strong></td><td><em>string</em></td><td>Time zone settings.</td></tr><tr><td><strong>enabled_countries</strong></td><td><em>string</em></td><td>Enabled countries ISO 3166 2-letters country code. Ref: <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes</a>.</td></tr><tr><td><strong>send_email_notifications</strong></td><td><em>bool</em></td><td>Activate/deactivate automatic email delivery to customers when they complete an order or receive a refund.</td></tr><tr><td><strong>cart_settings</strong></td><td><em>object</em></td><td>The settings applied to user carts.</td></tr></tbody></table>

#### business\_address

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>address_1</strong></td><td><em>string</em></td><td>Number and Street, concatenated.</td></tr><tr><td><strong>address_2</strong></td><td><em>string</em></td><td>Address complement (apt #, office #, floor level, etc.).</td></tr><tr><td><strong>city</strong></td><td><em>string</em></td><td>City name.</td></tr><tr><td><strong>sub_locality</strong></td><td><em>string</em></td><td>Sub-locality attached to the address (ex: county or district name).</td></tr><tr><td><strong>region</strong></td><td><em>string</em></td><td>The administrative region (depending on country, this can be a state, province, department, etc.).</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>ISO 3166 2-letters ISO country code. Ref: <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes</a>.</td></tr><tr><td><strong>postal_code</strong></td><td><em>string</em></td><td>Postal code.</td></tr></tbody></table>

#### cart\_settings

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>split_name_field</strong></td><td><em>bool</em></td><td>Should the full name of the cart owner be split into first and last name fields.</td></tr><tr><td><strong>split_address_1_field</strong></td><td><em>bool</em></td><td>Should addresses associated with the cart be split into street number and street name fields.</td></tr><tr><td><strong>display_instruction_field</strong></td><td><em>bool</em></td><td>Should the cart display an instruction field.</td></tr><tr><td><strong>display_phone_field</strong></td><td><em>bool</em></td><td>Should the cart display a phone field.</td></tr></tbody></table>

## Get Settings

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="Get Settings" path="/sites/multiscreen/{site_name}/ecommerce" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "default_currency": "string",
  "business_name": "string",
  "business_address": {
    "address_1": "string",
    "address_2": "string",
    "city": "string",
    "sub_locality": "string",
    "region": "string",
    "country": "string",
    "postal_code": "string"
  },
  "time_zone": "string",
  "enabled_countries": [
    "string"
  ],
  "send_email_notifications": true,
  "cart_settings": {
    "split_name_field": true,
    "split_address_1_field": true,
    "display_instruction_field": true,
    "display_phone_field": true
  }
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Settings

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="patch" summary="Update Settings" path="/sites/multiscreen/{site_name}/ecommerce" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="default_currency" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="business_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="business_address" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="time_zone" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="enabled_countries" type="array of strings" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="send_email_notifications" type="boolean" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "default_currency": "string",
  "business_name": "string",
  "business_address": {
    "name": "string",
    "address_1": "string",
    "address_2": "string",
    "city": "string",
    "region": "string",
    "sub_locality": "string",
    "country": "string",
    "postal_code": "string"
  },
  "time_zone": "string",
  "enabled_countries": [
    "string"
  ],
  "send_email_notifications": true
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}
