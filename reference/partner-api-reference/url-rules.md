# URL Rules

## URL Rule Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "id": string,
  "source": "/page-path",
  "target": "page-name-path-or-absolute-url",
  "response_code": 301
}
```
{% endtab %}
{% endtabs %}

| Field              | Type      | Description                                      |
| ------------------ | --------- | ------------------------------------------------ |
| **id**             | _string_  | The internal unique identifier for the URL rule. |
| **source**         | _string_  | Source path of the redirect.                     |
| **target**         | _string_  | Target path, URL or page name.                   |
| **response\_code** | _integer_ | HTTP status code.                                |

## List Rules

{% swagger method="get" path="/sites/multiscreen/site/{site_name}/urlrules" baseUrl="https://api.duda.co/api" summary="List Rules" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get all of the URL rules of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": string,
  "results": [{
    "id": string,
    "source": "/page-path",
    "target": "page-name-path-or-absolulte-url",
    "response_code": 301
  }]
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/urlrules \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Rule

{% swagger method="get" path="/sites/multiscreen/site/{site_name}/urlrules/{id}" baseUrl="https://api.duda.co/api" summary="Get Rule" expanded="false" %}
{% swagger-description %}
Get the details of a specific URL rule.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="string" required="true" %}
The unique identifier of the target URL rule.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": string,
  "results": [{
    "id": string,
    "source": "/page-path",
    "target": "page-name-path-or-absolute-url",
    "response_code": 301
  }]
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/urlrules/id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Rule

{% swagger method="post" path="/sites/multiscreen/site/{site_name}/urlrules" baseUrl="https://api.duda.co/api" summary="Crate Rule" expanded="false" %}
{% swagger-description %}
Create a new URL rule.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="source" type="string" %}
Source path of the redirect
{% endswagger-parameter %}

{% swagger-parameter in="body" name="target" type="string" %}
Target page path, URL or page name.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="response_code" type="int32" %}
HTTP response code.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": string,
  "results": [{
    "id": string,
    "source": "/page-path",
    "target": "page-name-path-or-absolulte-url",
    "response_code": 301
  }]
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/urlrules \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "source": "source",
  "target": "target",
  "response_code": 301
}
```
{% endtab %}
{% endtabs %}

## Update Rule

{% swagger method="put" path="/sites/multiscreen/site/{site_name}/urlrules/{id}" baseUrl="https://api.duda.co/api" summary="Update Rule" expanded="false" %}
{% swagger-description %}
Update an existing URL rule.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="string" required="true" %}
The unique identifier of the URL rule
{% endswagger-parameter %}

{% swagger-parameter in="body" name="source" type="string" %}
Source path of the redirect
{% endswagger-parameter %}

{% swagger-parameter in="body" name="target" type="string" %}
Target page path, URL or page name.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="response_code" type="int32" %}
HTTP response code.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": string,
  "results": [{
    "id": string,
    "source": "/source",
    "target": "/target",
    "response_code": 301
  }]
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/urlrules/id \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "source": "source",
  "target": "target",
  "response_code": 301
}
'
```
{% endtab %}
{% endtabs %}

## Delete Rule

{% swagger method="delete" path="/sites/multiscreen/site/{site_name}/urlrules/{id}" baseUrl="https://api.duda.co/api" summary="Delete Rule" expanded="false" %}
{% swagger-description %}
Update an existing URL rule.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="string" required="true" %}
The unique identifier of the URL rule
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/urlrules/id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
