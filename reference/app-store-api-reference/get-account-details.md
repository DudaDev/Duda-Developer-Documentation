---
description: Get Account Details of the account owner who installed the App.
---

# Get Account Details

{% tabs %}
{% tab title="JSON" %}
```json
{
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "uuid": "string"
}
```
{% endtab %}
{% endtabs %}

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/site/{site_name}/account/details" summary="" %}
{% swagger-description %}
Get the email address, name, and UUID of the account which installed the App. Enables you to get contact details if needed for the agency/web pro that installed the App.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" required="true" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" required="true" %}
Your App Account's username and password, based64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```
{
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "uuid": "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/account/details \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
