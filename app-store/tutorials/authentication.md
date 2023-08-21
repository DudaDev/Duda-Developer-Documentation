---
description: Using the App Store API
---

# Authentication

Duda enforces two authentication schemes on apps to access a site specific API.

* **Basic Authentication:** by default, Duda enforces [basic authentication](https://datatracker.ietf.org/doc/html/rfc7617) to access most of its public APIs.
* **Bearer Tokens:** in addition to basic authentication, Duda requires a [bearer token](https://datatracker.ietf.org/doc/html/rfc6750) for apps to access APIs for specific a site, after an App is installed on that site.

### Basic Authentication

Duda will provide you with API credentials (user and pass) to authenticate API requests with Duda. The provided credentials will work for both the sandbox and production environments.

To create the HTTP Authorization Header, you should combine your username and password into one string, separated by a colon and then Base64 encode that string. So for example, 'user:pass' combination would result in the header:

`Authorization: dXNlcjpwYXNz`

### Bearer Token

When an app is installed, Duda will send an install lifecycle event that contains an `authorization_code` to call the API for a specific site. Duda expects all site specific API calls to include an `authorization_code` as a bearer token for the target site.

`authorization_code` tokens are valid for **12 hours**. After they expire, you must refresh the token using the `refresh _token` obtained in the install lifecycle event. Duda will also return a `401 Unauthorized` HTTP Code when an authorization\_code has expired. Once you receive a 401, you can generate a new code and store it for use.

{% hint style="warning" %}
**Heads up: Credentials Security Best Practice**

1. Store the permanent `refresh_token` and restrict access to it to a single utility function.
2. All functions that require the `authorization_code` should retrieve it from the utility function.
3. The utility function should keep the `authorization_code` in memory.
{% endhint %}

<figure><img src="https://files.readme.io/166d2dc-Duda.App.Token.Authentication.jpeg" alt="2434"><figcaption><p>The process we recommend implementing to manage auth_codes that can expire.</p></figcaption></figure>

Example request:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST \
  https://<duda-environment-api-url>/api/integrationhub/application/{{appUuid}}/token/refresh \
  -H 'Authorization: Basic ZG9jdW1lbnRhdGlvbjpleGFtcGxlMQ==' \
  -H 'Content-Type: application/json' \
  -d '{"refreshToken": "c7ea6d25-7f5e-4d1b-b569-bbd2e102c7a4"}'
```
{% endtab %}
{% endtabs %}

After sending the previous request to generate a new authorization code, you will get the following response:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "type": "bearer",
    "authorization_code": "a8b88a96-d0d5-4dc8-b397-9da3044a03bc",
    "refresh_token": "c7ea6d25-7f5e-4d1b-b569-bbd2e102c7a4",
    "expiration_date": 1543977362382
}
```
{% endtab %}
{% endtabs %}

The new `authorization_code` will be valid for another 12 hours. Duda will return a `401 Unauthorized` HTTP Code when an authorization\_code has expired. Once you receive a 401, you can generate a new code and store it for use.

### Example

Here is an example Get Site Details request using both authentication schemes:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X GET \
https://{{api_endpoint}}/api/integrationhub/application/site/{{site_name}}/ \
  -H 'Authorization: Basic ZG9jdW1lbnRhdGlvbjpleGFtcGxlMQ==' \
  -H 'X-DUDA-ACCESS-TOKEN: Bearer ee69a4b4-b843-4e4b-8cf6-e7ff645a1535'
```
{% endtab %}
{% endtabs %}

### Complete API reference

See [App Reference](../reference/)
