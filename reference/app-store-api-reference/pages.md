# Pages

{% tabs %}
{% tab title="JSON" %}
```json
{
  "results": [
    {
      "uuid": "string",
      "title": "ABOUT",
      "path": "about/abab",
      "seo": {
        "title": "About Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('woo')</script>"
    },
    {
      "uuid": "string",
      "title": "SERVICES",
      "path": "services",
      "seo": {
        "title": "Services Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('hoo')</script>"
    },
    {
      "uuid": "string",
      "title": "HOME",
      "path": "home",
      "seo": {
        "title": "Home Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('foo')</script>"
    },
    {
      "uuid": "string",
      "title": "CONTACT",
      "path": "contact",
      "seo": {
        "title": "Contact Us",
        "description": null,
        "no_index": false
      },
      "header_html": "<script>console.log('bar')</script>"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

## Get Pages

{% swagger method="get" baseUrl="https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="Get Pages" path="/integrationhub/application/site/{site_name}/v2/pages" %}
{% swagger-description %}
Get details of all the Pages of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "results": [
    {
      "uuid": "string",
      "title": "ABOUT",
      "path": "about/abab",
      "seo": {
        "title": "About Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('woo')</script>"
    },
    {
      "uuid": "string",
      "title": "SERVICES",
      "path": "services",
      "seo": {
        "title": "Services Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('hoo')</script>"
    },
    {
      "uuid": "string",
      "title": "HOME",
      "path": "home",
      "seo": {
        "title": "Home Page",
        "description": null,
        "no_index": false,
        "og_image": "https://example.org/path/to/image.png"
      },
      "header_html": "<script>console.log('foo')</script>"
    },
    {
      "uuid": "string",
      "title": "CONTACT",
      "path": "contact",
      "seo": {
        "title": "Contact Us",
        "description": null,
        "no_index": false
      },
      "header_html": "<script>console.log('bar')</script>"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/v2/pages \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update Page

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="put" summary="Update Page" path="/integrationhub/application/site/{site_name}/v2/pages/{page_uuid}" %}
{% swagger-description %}
Update an existing Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_uuid" type="string" required="true" %}
The uuid of the target page.

\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/v2/pages/page_uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
