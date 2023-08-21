# Create New Access Token

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/{app_uuid}/token/refresh" summary="" %}
{% swagger-description %}
Create a new access token wtih an existing refresh token, from an App Install

Request a new authorization code for this App Install. This is used to authenticate against a specific site/app install area.
{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="app_uuid" type="string" %}
UUID of the App
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" required="true" %}
Your App Account's username and password, based64'd.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="refreshToken" type="string" %}
A refresh token you received when the App was installed.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "authorization_code": "string",
  "expiration_date": 0,
  "refresh_token": "string",
  "type": "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/app_uuid/token/refresh \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
