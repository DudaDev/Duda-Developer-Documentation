# Site Wide HTML

Site-wide HTML allows an App Developer to install code across all pages of the website. This is a powerful feature where you can embed analytics, chatbot, accessibility and many other different tools. It is important to use it wisely and ensure that you're not slowing the performance of the website, respecting privacy of visitors, and more.

## Site Wide HTML Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "location": "BODY",
  "markup": "<script>console.log('hello from site-wide html')</script>"
}
```
{% endtab %}
{% endtabs %}

| Attribute    | Description                                                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------- |
| **location** | An ENUM with the options of: BODY, HEAD, CONTENT\_END, BEFORE\_SCRIPTS. See note below about using it correctly. |
| **markup**   | The raw HTML markup you want to be embedded into the website. Make sure to escape properly.                      |

### Using location correctly

In most cases, you should use the `BODY` location. This places your code at the bottom of the page and respects performance best practices. Here are some other best practices for specific locations:

* `BEFORE_SCRIPTS` is great if you have a cookie or consent banner, and you need your script to load before any other scripts/trackers/cookies load on the page. Duda has created this specifically to load before scripts, but, after critical visual content. This ensures that content loads as-fast-as-possible and is not blocked by render-blocking scripts.
* `HEAD` should be used for meta tags, schema, link tags & other data. Avoid loading anything here that has an `src` attribute.
* `BODY` places the script at the end of the tag of the page.

## Create Site Wide HTML

{% swagger method="post" path="/integrationhub/application/site/{site_name}/sitewidehtml" baseUrl=" https://api-sandbox.duda.co/api" summary="Create Site Wide HTML" %}
{% swagger-description %}
Create a site-wide HTML embed.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="location" type="string" %}
Location of where the code will be added in the website.

\
Default: `CONTENT_END`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="markup" type="string" %}
The raw HTML you want to embed into the site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "location": "BODY",
  "markup": "string",
  "uuid": "string"
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/sitewidehtml \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4' \
     --data '
{
  "location": "CONTENT_END"
}
'
```
{% endtab %}
{% endtabs %}

## List all

{% swagger method="get" path="/integrationhub/application/site/{site_name}/sitewidehtml/list" baseUrl=" https://api-sandbox.duda.co/api" summary="List all" expanded="false" %}
{% swagger-description %}
View all site-wide HTML codes your app has installed.

The response returns an object, with a property of `siteWides`. This array contains all sitewide HTML code installs.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "siteWides": [
    {
      "location": "BODY",
      "markup": "string",
      "uuid": "string"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/sitewidehtml/list \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Get

{% swagger method="get" path="/integrationhub/application/site/{site_name}/sitewidehtml/{uuid}" baseUrl=" https://api-sandbox.duda.co/api" summary="Get" expanded="false" %}
{% swagger-description %}
Get a specific site-wide HTML embed.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="uuid" type="string" required="true" %}
An existing site wide HTML UUID.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "location": "BODY",
  "markup": "string",
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/sitewidehtml/uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update

{% swagger method="put" path="/integrationhub/application/site/{site_name}/sitewidehtml/{uuid}" baseUrl=" https://api-sandbox.duda.co/api" summary="Update" expanded="false" %}
{% swagger-description %}
Update a specific SWH Install
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="uuid" type="string" required="true" %}
An existing site wide HTML UUID.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="location" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="markup" type="string" %}
HTML Markup to update
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "location": "BODY",
  "markup": "string",
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
curl --request PUT \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/sitewidehtml/uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Delete

{% swagger method="delete" path="/integrationhub/application/site/{site_name}/sitewidehtml/{uuid}" baseUrl=" https://api-sandbox.duda.co/api" summary="Delete" expanded="false" %}
{% swagger-description %}
Delete a specific SWH Install
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="uuid" type="string" required="true" %}
An existing site wide HTML UUID.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "location": "BODY",
  "markup": "string",
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
curl --request DELETE \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/sitewidehtml/uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
