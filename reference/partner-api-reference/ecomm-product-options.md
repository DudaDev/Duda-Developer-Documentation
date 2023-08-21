---
description: Native Store Only
---

# eComm Product Options

## Product Option Object

{% tabs %}
{% tab title="JSON" %}
```json
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
```
{% endtab %}
{% endtabs %}

#### product\_option

| Property    | Type     | Description                                                                                                | Mutable |
| ----------- | -------- | ---------------------------------------------------------------------------------------------------------- | ------- |
| **id**      | _string_ | Unique identifier for the option                                                                           | No      |
| **name**    | _string_ | The name of the option                                                                                     | Yes     |
| **choices** | _string_ | An array of choices for the option. [See the section below for details](ecomm-product-options.md#choices). | Yes     |

#### choices

| Property  | Type     | Description                      | Mutable |
| --------- | -------- | -------------------------------- | ------- |
| **id**    | _string_ | Unique identifier for the choice | No      |
| **value** | _string_ | Value of the choice              | Yes     |

## List Product Options

{% swagger method="get" path="/sites/multiscreen/{site_name}/ecommerce/options" baseUrl="https://api.duda.co/api" summary="List Product Options" expanded="false" fullWidth="false" %}
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
Property on which to sort results
{% endswagger-parameter %}

{% swagger-parameter in="query" name="direction" type="string" %}
\[asc,desc] Order direction for the property specified in sort.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "limit": 0,
  "offset": 0,
  "results": [
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
  "site_name": "string",
  "total_responses": 0
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
     --url 'https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options?offset=0&limit=20&direction=asc' \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Product Option

{% swagger method="post" path="/sites/multiscreen/{site_name}/ecommerce/options" baseUrl="https://api.duda.co/api" summary="Create Product Option" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
Name of the option
{% endswagger-parameter %}

{% swagger-parameter in="body" name="choices" type="array of strings" required="true" %}
List of possible values for the option
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
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
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "choices": [
    "45"
  ],
  "name": "Shirt size"
}
'
```
{% endtab %}
{% endtabs %}

## Get Product Option

{% swagger method="get" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}" baseUrl="https://api.duda.co/api" summary="Get Product Option" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
Unique identifier for the target option

\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
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
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Product Option

{% swagger method="delete" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}" baseUrl="https://api.duda.co/api" summary="Delete Product Option" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
The unique identifier for the target option
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Product Option

{% swagger method="put" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}" baseUrl="https://api.duda.co/api" summary="Update Product Option" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
The unique identifier for the target option
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
Name of the option
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
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
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "name": "Shirt size"
}
'
```
{% endtab %}
{% endtabs %}

## Create Product Option Choice

{% swagger method="post" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}/choices" baseUrl="https://api.duda.co/api" summary="Create Product Option Choice" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
The unique identifier for the target option
{% endswagger-parameter %}

{% swagger-parameter in="body" name="value" type="string" %}
The value of the new option choice
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
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
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id/choices \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '{"value":"45"}'
```
{% endtab %}
{% endtabs %}

## Delete Product Option Choice

{% swagger method="delete" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}/choices/{choice_id}" baseUrl="https://api.duda.co/api" summary="Delete Product Option Choice" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
The unique identifier for the target option
{% endswagger-parameter %}

{% swagger-parameter in="path" name="choice_id" type="string" required="true" %}
The unique identifier for the target choice
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id/choices/choice_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Product Option Choice

{% swagger method="put" path="/sites/multiscreen/{site_name}/ecommerce/options/{option_id}/choices/{choice_id}" baseUrl="https://api.duda.co/api" summary="Update Product Option Choice" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="option_id" type="string" required="true" %}
The unique identifier for the target option
{% endswagger-parameter %}

{% swagger-parameter in="body" name="value" type="string" required="true" %}
The updated value for the choice
{% endswagger-parameter %}

{% swagger-parameter in="path" name="choice_id" type="string" required="true" %}
The unique identifier for the target choice
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "choices": [
    {
      "id": "db3je27rg7",
      "value": "46"
    }
  ],
  "id": "WMd1xylGrp",
  "name": "Shirt size"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/options/option_id/choices/choice_id \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '{"value":"46"}'
```
{% endtab %}
{% endtabs %}
