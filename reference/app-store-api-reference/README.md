---
description: This page will help you get started with using the App Store API.
---

# App Store API Reference

Duda's App Store API is organized around REST. Our API has predictable resource-oriented URLs, accepts JSON request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

Duda's primary path for all App Store API endpoints is: `https://api.duda.co/api/integrationhub/application`

{% hint style="warning" %}
**Heads up:** the Duda App Store API is currently not open to the public.
{% endhint %}

### Authentication & Security

Duda's App Store API uses [basic HTTP authentication](https://en.wikipedia.org/wiki/Basic\_access\_authentication) and authorization tokens to authenticate requests and allow access to site resources.

As part of partnering with Duda's App Store, you will get a username and password specific to your app. The username and password need to be joined with a colon and base64 encoded before passing it into the `Authorization` header.

In addition to the username and password, Duda provides site-specific bearer tokens in the [install callback](https://about/docs/app-store-webhooks#install). Duda expects all App Store API calls to include the site-specific token in an `X-DUDA-ACCESS-TOKEN` header.

An example cURL request:

{% tabs %}
{% tab title="curl" %}
```bash
curl 'https://api.duda.co/api/integrationhub/application' \
-H 'Authorization: Basic <base64-user:pass>' \
-H 'X-DUDA-ACCESS-TOKEN: Bearer <authorization-token>'
```
{% endtab %}
{% endtabs %}

Duda's APIs are only available over HTTPS to ensure that data is securely transmitted over the internet. In addition, Duda only accepts connections using TLS v1.2 and higher.

### Rate Limits

Duda's servers enforce rate limits to maintain a level of performance and stability for all Duda customers. **We have both global and endpoint-specific rate limits**.

For all API endpoints, there is a hard limit of **10 API calls per second**. If you are running any batch process against the API, Duda recommends limiting your requests to one every 125ms (8 a second) to prevent hitting the rate limit.

Duda will respond with a `429 Too Many Requests` status code if you hit a rate limit.

### Errors

When Duda detects an error in your request, we will respond with a 400 (Bad Request) HTTP response and return a JSON error object:

{% tabs %}
{% tab title="JSON" %}
```json
{
  "error_code": "ResourceNotExist",
  "message": "Site with alias 'badName' doesn't exist"
}
```
{% endtab %}
{% endtabs %}

### Good-to-Know

**Dates**

There are some Duda APIs that return date-time values. Duda formats these in the standard universal full date-time pattern in the UTC timezone. The format is: `yyyy-mm-ddThh:mm:ss`. So for example: 2016-11-15T22:55:53 would be November 11th, 2016 at 10:55:53 PM UTC.

When sending dates to Duda, you can use the full universal format above, or just the YYYY-MM-DD format. If you omit the time, Duda will default that time to the beginning of the day.

**Languages**

There are some parts of the API where Duda returns real-world content to display to users. As part of this, we can deliver localized content. Below you will see a full list of languages that the Duda platform (UI) is localized for and their corresponding language codes. \*

| Language      | Language Code |
| ------------- | ------------- |
| Arabic        | ar            |
| Dutch         | nl            |
| English       | en            |
| English UK    | en\_gb        |
| French        | fr            |
| German        | de            |
| Indonesian    | id            |
| Italian       | it            |
| Japanese      | ja            |
| Polish        | pl            |
| Portuguese    | pt            |
| Spanish       | es            |
| Spanish LATAM | es\_ar        |
| Turkish       | tr            |
