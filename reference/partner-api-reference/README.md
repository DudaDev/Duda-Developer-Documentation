---
description: This page will help you get started with using the Partner API.
---

# Partner API Reference

Duda's Partner API is organized around REST. Our API has predictable resource-oriented URLs, accepts JSON request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

The Partner API is designed to be a Management API, which means you can integrate Duda's white-labeled resources (sites, accounts, etc.) into your own workflows and/or services.

Duda's primary path for all production API endpoints is: `https://api.duda.co/api`



{% hint style="info" %}
**Good to know:** To access the Duda API, you need to request access through your websites dashboard or [submit a request](https://support.duda.co/hc/en-us/requests/new) to our support team.
{% endhint %}

### Authentication & Security

Duda's APIs use [basic HTTP authentication](https://en.wikipedia.org/wiki/Basic\_access\_authentication) to authenticate requests and allow access to resources.

As part of getting access to the API, you will get a user name and password specific to your account. The user and password need to be joined with a colon and base64 encoded before passing it into the `Authorization` header. An example cURL request:

{% tabs %}
{% tab title="curl" %}
{% code overflow="wrap" %}
```sh
curl -H 'Authorization: Basic <base64-token>' 'https://api.duda.co/api'
```
{% endcode %}
{% endtab %}
{% endtabs %}

Duda's APIs are only available over HTTPS to ensure that data is securely transmitted over the internet. In addition, Duda only accepts connections using TLS v1.2 and higher.

### Rate Limits

Duda's servers enforce rate limits to maintain a level of performance and stability for all Duda customers. **We have both global and endpoint-specific rate limits**.

For all API endpoints, there is a hard limit of **10 API calls per second**. If you are running any batch process against the API, Duda recommends limiting your requests to one every 125ms (8 a second) to prevent hitting the rate limit.

The following endpoints have their own specific limits:

* Publish Site and Unpublish Site: 20 calls per minute
* Create Site: 60 calls per minute
* Create Account: 60 calls per minute
* Clear Cache by External ID: 1 call every 15 minutes
* Get Contact Form Submissions: 800 calls per minute

Duda will respond with a `429 Too Many Requests` status code if you hit the rate limit.

### Error

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

There are some Duda APIs that return date-time values. Duda formats these in the standard universal full date-time pattern in the UTC timezone. The format is: `yyyy-mm-ddThh:mm:ss`. So for example: 2016-11-15T22:55:53 would be November 15th, 2016 at 10:55:53 PM UTC.

When sending dates to Duda, you can use the full universal format above, or just the YYYY-MM-DD format. If you omit the time, Duda will default that time to the beginning of the day.

**Languages**

There are some parts of the API where Duda returns real-world content to display to users. As part of this, we are able to deliver localized content. Below you will see a full list of languages that the Duda platform (UI) is localized for along with their corresponding language codes.

<table data-full-width="false"><thead><tr><th>Language</th><th>Language Code</th></tr></thead><tbody><tr><td>Arabic</td><td>ar</td></tr><tr><td>Dutch</td><td>nl</td></tr><tr><td>English</td><td>en</td></tr><tr><td>English UK</td><td>en_gb</td></tr><tr><td>French</td><td>fr</td></tr><tr><td>German</td><td>de</td></tr><tr><td>Indonesian</td><td>id</td></tr><tr><td>Italian</td><td>it</td></tr><tr><td>Japanese</td><td>ja</td></tr><tr><td>Polish</td><td>pl</td></tr><tr><td>Portuguese</td><td>pt</td></tr><tr><td>Spanish</td><td>es</td></tr><tr><td>Spanish LATAM</td><td>es_ar</td></tr><tr><td>Turkish</td><td>tr</td></tr></tbody></table>

**Python Requests**

All endpoints require a user-agent header to be present. Some tools like cURL will add the user agent automatically. The same holds true for helper libraries such as node-fetch. The cURL, Ruby, Node and JavaScript code examples included for each endpoint all handle the user-agent header for you. If you are using Python, your header should include an explicit `user-agent` in your request.
