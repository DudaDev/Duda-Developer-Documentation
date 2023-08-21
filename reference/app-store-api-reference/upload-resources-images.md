---
description: Upload images to the content library of the website.
---

# Upload Resources (images)

#### Body Params

| Field              | Type     | Description                                                                |
| ------------------ | -------- | -------------------------------------------------------------------------- |
| **resource\_type** | _string_ | Default: image                                                             |
| **src**            | _string_ | The location where Duda copies content from. Must be publically available. |

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/site/{site_name}/resources/upload" summary="" %}
{% swagger-description %}
Upload content to the website. Enables the image to be used while editing or designing the website. Today, we only allow images.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" required="true" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" required="true" %}
Your App Account's username and password, based64'd.
{% endswagger-parameter %}

{% swagger-parameter in="body" type="array of objects" name="RAW_BODY" %}


[See definition for details](upload-resources-images.md#body-params)


{% endswagger-parameter %}

{% swagger-response status="201: Created" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/resources/upload \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4' \
     --data '
[
  {
    "resource_type": "image",
    "src": "https://image.com"
  }
]
'
```
{% endtab %}
{% endtabs %}
