# Pages v1

## Page Object v1

{% tabs %}
{% tab title="JSON" %}
```json
{
  "page_title": "Contact",
  "page_path": "contact",
  "page_seo": {
    "title": "Contact",
    "description": "Contact us",
    "no_index": false,
  },
  "page_name": "Y29udGFjdA==",
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>page_title</strong></td><td><em>string</em></td><td>The title of a page. It's used in the navigation of the site and pages menu.</td></tr><tr><td><strong>page_path</strong></td><td><em>string</em></td><td>The path / URL to a page on the website.</td></tr><tr><td><strong>page_seo</strong></td><td><em>object</em></td><td><a href="pages-v1.md#page_seo">See the section below for details</a>.</td></tr><tr><td><strong>page_name</strong></td><td><em>string</em></td><td>The base64 encoded page_page.</td></tr></tbody></table>

#### page\_seo

<table><thead><tr><th width="269">Property</th><th width="223">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>title</strong></td><td><em>string</em></td><td>Set the &#x3C;title>  on this page. Should be less than 60 characters in length.</td></tr><tr><td><strong>description</strong></td><td><em>string</em></td><td>The meta description of the page. Should be around 155 characters in length.</td></tr><tr><td><strong>no_index</strong></td><td><em>bool</em></td><td>Set if this page should be indexed by search engines or not. This will apply a meta robots noindex tag to this page.</td></tr></tbody></table>

## List Pages

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Pages" path="/sites/multiscreen/site/{site_name}/pages" %}
{% swagger-description %}
Get details of all the Pages of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
[
  {
    "page_title": "ABOUT",
    "page_path": "about/abab",
    "page_seo": {
      "title": "About Page",
      "description": null,
      "no_index": false
    },
    "page_name": "YWJvdXQvYWJhYg"
  },
  {
    "page_title": "SERVICES",
    "page_path": "services",
    "page_seo": {
      "title": "Services Page",
      "description": null,
      "no_index": false
    },
    "page_name": "c2VydmljZXM"
  },
  {
    "page_title": "HOME",
    "page_path": "home",
    "page_seo": {
      "title": "Home Page",
      "description": null,
      "no_index": false
    },
    "page_name": "aG9tZQ"
  },
  {
    "page_title": "CONTACT",
    "page_path": "contact",
    "page_seo": {
      "title": "Contact Us",
      "description": null,
      "no_index": false
    },
    "page_name": "Y29udGFjdA"
  }
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/pages \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Page" path="/sites/multiscreen/site/{site_name}/pages/{page_name}" %}
{% swagger-description %}
Get the details of an individual Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_name" type="string" required="true" %}
The name of the target page.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "page_title": "Blog",
  "page_path": "blog",
  "page_seo": {
    "title": "Blog Page Title",
    "description": "Read our blog! We have great info and you'll learn a lot.",
    "no_index": false
  },
  "page_name": "YmxvZw=="
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/pages/page_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Update Page" path="/sites/multiscreen/site/{site_name}/pages/{page_name}/update" %}
{% swagger-description %}
Update an existing Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_name" type="string" required="true" %}
The name of the target page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page_title" type="string" %}
The new title to assign to the page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page_path" type="string" %}
The new url path to assign to the page.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page_seo" type="object" %}
The new SEO settings to assign to the page.
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
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/pages/page_name/update \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Duplicate Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Duplicate Page" path="/sites/multiscreen/site/{site_name}/pages/{page_name}/duplicate" %}
{% swagger-description %}
Duplicate an existing Page of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_name" type="string" required="true" %}
The name of the target page.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="pageTitle" type="string" required="true" %}
The title to assign to the new page.
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/pages/page_name/duplicate \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Page

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="delete" summary="Delete Page" path="/sites/multiscreen/site/{site_name}/pages/{page_name}/delete" %}
{% swagger-description %}
Delete a Page from a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="page_name" type="string" required="true" %}
The name of the target page.
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
     --url https://api.duda.co/api/sites/multiscreen/site/site_name/pages/page_name/delete \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
