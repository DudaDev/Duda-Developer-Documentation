---
description: Getting a site via App Store APIs
---

# Get Account Brand

{% tabs %}
{% tab title="JSON" %}
```json
{
  "logo": "urlString",
  "color": {
    "links": "string",
    "button_background": "hexOrRgbString",
    "button_text": "hexOrRgbString",
    "text_on_light": "hexOrRgbString",
    "text_on_dark": "hexOrRgbString",
    "header_background": "hexOrRgbString",
    "preview_background": "hexOrRgbString"
  },
  "preview_background_image": "urlString",
  "dashboard_domain": "urlString"
}
```
{% endtab %}
{% endtabs %}

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/site/{site_name}/branding" summary="" %}
{% swagger-description %}
Get the branding, URL, Logo, and colors of the parent account associated with the website. This can be used to generate similar colors for your App, get the 

[white labeled dashboard domain](https://support.duda.co/hc/en-us/articles/5098283299735-Configure-White-Label-Platform-Domain)

, or understand more about the agency that's installing your App.
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
  "logo": "string",
  "color": {
    "links": "string",
    "button_background": "string",
    "button_text": "string",
    "text_on_light": "string",
    "text_on_dark": "string",
    "header_background": "string",
    "preview_background": "string"
  },
  "preview_background_image": "string",
  "dashboard_domain": "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/branding \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
