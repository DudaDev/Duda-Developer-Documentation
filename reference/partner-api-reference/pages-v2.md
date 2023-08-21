# Pages v2

## Page Object v2

{% tabs %}
{% tab title="JSON" %}
```json
{
  "uuid": "string",
  "title": "string",
  "path": "string",
  "seo": {
    "title": "string",
    "description": "string",
    "no_index": true,
    "og_image": "string"
  },
  "header_html": "string"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>uuid</strong></td><td><em>string</em></td><td>The internal unique identifier of a specific page. This value is used to update or delete a page with other API calls.</td></tr><tr><td><strong>title</strong></td><td><em>string</em></td><td>The title of a page. It's used in the navigation of the site and pages menu.</td></tr><tr><td><strong>path</strong></td><td><em>string</em></td><td>The path / URL to a page on the website.</td></tr><tr><td><strong>seo</strong></td><td><em>object</em></td><td><a href="pages-v2.md#seo">See the section below for details</a>.</td></tr><tr><td><strong>header_html</strong></td><td><em>string</em></td><td>Contains the custom header HTML set for a specific page.</td></tr></tbody></table>

#### seo

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>title</strong></td><td><em>string</em></td><td>Set the title on this page. Should be less than 60 characters in length.</td></tr><tr><td><strong>description</strong></td><td><em>string</em></td><td>The meta description of the page. Should be around 155 characters in length.</td></tr><tr><td><strong>no_index</strong></td><td><em>bool</em></td><td>Set if this page should be indexed by search engines or not. This will apply a meta robots noindex tag to this page.</td></tr><tr><td><strong>og_image</strong></td><td><em>string</em></td><td>URL to the image to be used as the Open Graph sharing image.</td></tr></tbody></table>

## List Pages

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Pages" path="/sites/multiscreen/{site_name}/pages" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/pages \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Page" path="/sites/multiscreen/{site_name}/pages/{page_uuid}" %}
{% swagger-description %}
Get the details of an individual Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_uuid" type="string" required="true" %}
The uuid of the target page.

\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "title": "Blog",
  "path": "blog",
  "seo": {
    "title": "Blog Page Title",
    "description": "Read our blog! We have great info and you'll learn a lot.",
    "no_index": false,
    "og_image": "https://example.org/path/to/image.png"
  },
  "header_html": "<script>console.log('foo')</script>"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/pages/page_uuid \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="put" summary="Update Page" path="/sites/multiscreen/{site_name}/pages/{page_uuid}" %}
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

{% swagger-parameter in="body" name="title" type="string" %}
The new title to assign to the page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="path" type="string" %}
The new url path to assign to the page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="seo" type="object" %}
The new SEO settings to assign to the page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="header_html" type="string" %}
The new page header HTML to assign to the page.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** The page\_path of the home page cannot be updated
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api.duda.co/api/sites/multiscreen/site_name/pages/page_uuid \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Duplicate Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Duplicate Page" path="/sites/multiscreen/{site_name}/pages/{page_uuid}/duplicate" %}
{% swagger-description %}
Duplicate an existing Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_uuid" type="string" required="true" %}
The uuid of the target page.

\



{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}
The title to assign to the new page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="path" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="seo" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="header_html" type="string" %}
The new page header HTML to assign to the page.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/pages/page_uuid/duplicate \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="delete" summary="Delete Page" path="/sites/multiscreen/{site_name}/pages/{page_uuid}" %}
{% swagger-description %}
Delete a Page from a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_uuid" type="string" required="true" %}
The uuid of the target page.

\



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
     --url https://api.duda.co/api/sites/multiscreen/site_name/pages/page_uuid \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
