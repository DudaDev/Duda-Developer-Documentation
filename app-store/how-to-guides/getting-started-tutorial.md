# Getting Started Tutorial

This step-by-step tutorial is designed to get you started with core concepts of the Duda App Store. You'll learn how to access the App Store API, configuring the app manifest, and manage the lifecycle of your app.

After completing the steps in this guide you'll be able to:

* Handle lifecycle [events](../tutorials/lifecycle-events.md) (install, uninstall, upgrade, downgrade).
* Authenticate users into your service via Single Sign-On.
* Perform API calls against the sites on which your App is installed.

### Prequisites

To follow along you'll need:

* Access to the [Sandbox Environment](https://editor-sandbox.duda.co/login)
* App Store API Credentials
* An app UUID

If you don't have these, please contact [app-developer-support@duda.co](mailto:app-developer-support@duda.co).

### 1. Get the App Manifest

We'll start by getting the full app manifest for your application. The [App Manifest](../concepts/manifest.md) contains all of your application configuration options within Duda.

Use this API call to get the details of your app from the Duda App Store:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X GET https://api-sandbox.duda.co/api/integrationhub/application/{{appUuid}} -u 'APIUser:APIPass' -H 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know: Basic Authentication**

All API calls to the Duda App Store require the `Authentication` header to be present. This authenticates that you are the owner of the app in question. Most other API calls also require a resource token to access APIs for a specific site.
{% endhint %}

The response will include your app manifest details in the following format:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "uuid": "2257f749-03a7-45c2-9e8a-ae5f5e6e072c",
    "webhooks": {
        "endpoint": "https://temporary.com/endpoint",
        "events": [
            "CONTENT_LIB_CHANGED",
            "CONTENT_LIB_PUBLISHED",
            "PUBLISH"
        ]
    },
    "scopes": [
        "GET_WEBSITE",
        "UPDATE_PAGES",
        "SITE_WIDE_HTML",
        "GET_PAGES"
    ],
    "public_key": "KEY-XXXX",
    "installation_endpoint": "https://temporary.com/endpoint",
    "uninstallation_endpoint": "https://temporary.com/endpoint",
    "updowngrade_installation_endpoint": "https://temporary.com/endpoint",
    "base_sso_url": "https://temporary.com/sso",
    "supported_locales": [
        "en"
    ],
    "app_profile": {
        "en": {
            "app_name": "Display name",
            "app_logo": "https://temporary.com/imageLogo.png",
            "app_short_description": "A short description goes here.",
            "app_long_description": "This app can do this a that",
            "public_page": "https://temporary.com/ourproduct",
            "terms_of_service_page": "https://temporary.com/terms_en",
            "privacy_note_page": "https://temporary.com/privacy_en",
            "app_screenshots": [
                {
                    "image_url": "https://temporary.com/image.jpg",
                    "alt_text": "Description of image above"
                },
                {
                    "image_url": "https://temporary.com/image2.jpg",
                    "alt_text": "Description of image above"
                }
            ]
        }
    },
    "wl_app_profile": {
        "en": {
            "app_name": "White Labeled display name",
            "app_logo": "https://temporary.com/imageLogo.png",
            "app_short_description": "A short description goes here.",
            "app_long_description": "This app can do this a that",
            "app_screenshots": [
                {
                    "image_url": "https://temporary.com/image.jpg",
                    "alt_text": "Description of image above"
                },
                {
                    "image_url": "https://temporary.com/image2.jpg",
                    "alt_text": "Description of image above"
                }
            ]
        }
    },
    "app_plans": [
        {
            "plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
            "is_free": false,
            "is_hidden": false,
            "plan_grade": 0,
            "plan_profiles": {
                "en": {
                    "plan_name": "First",
                    "plan_subtitle": "Start...",
                    "plan_features": [
                        "My first feature",
                        "<strong>My best feature</strong>",
                        "another feature"
                    ]
                }
            }
        },
        {
            "plan_uuid": "bd50e369-e7d4-4246-83d4-e190038e7f07",
            "is_free": false,
            "is_hidden": false,
            "plan_grade": 1,
            "plan_profiles": {
                "en": {
                    "plan_name": "Second",
                    "plan_subtitle": "...Finish",
                    "plan_features": [
                        "My first feature",
                        "<strong>My best feature</strong>",
                        "another feature"
                    ]
                }
            }
        }
    ]
}
```
{% endtab %}
{% endtabs %}

### 2. Update the App Manifest

Use an API call to update your app manifest with the relevant information pointing to your development environment.

| Key                                 | Description                                                                                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `installation_endpoint`             | The endpoint that Duda sends installation details to whenever a user installs your app.                                            |
| `uninstallation_endpoint`           | The endpoint that Duda sends uninstallation details to whenever a user uninstalls your app.                                        |
| `updowngrade_installation_endpoint` | The endpoint that Duda sends upgrade or downgrade details to whenever a user updates their plan details for your app.              |
| `base_sso_url`                      | The URL that Duda opens whenever a user decides to open your app. This is also the URL Duda opens after a successful installation. |
| `webhook_endpoint`                  | The endpoint that Duda sends webhooks to whenever one is triggered.                                                                |

For this tutorial, you can use these endpoints:

1. Set the endpoints to a webhook testing tool that _**always returns a 200**_ HTTP status code and makes sure you can access its details. There are many free tools online such as [beeceptor.com](https://beeceptor.com/) or [http://webhook.site/](http://webhook.site/) that can receive requests from Duda.
2. Set the `base_sso_url` to a URL that can be open inside of an iframe, such as: [https://www.w3schools.com](https://www.w3schools.com/) (or a URL into your application).

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST https://api-sandbox.duda.co/api/integrationhub/application/{{appUuid}} -u 'AppAccountUser:AppAccountPass' -H 'Content-Type: application/json' -d '{{YOUR UPDATED MANIFEST JSON}}'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know: API Behavior**

1. Sending a POST update that changes immutable properties (i.e. `app_uuid`) will return a 400 error.
2. Calls to update your app manifest should include all properties of the manifest. Think of this action as a pure PUT request.
{% endhint %}

{% hint style="warning" %}
**Heads up: URL Policies**

1. All URLs must use the HTTPS protocol.
2. In order to comply with Duda’s white Llbel policy, paths should not include the string ‘Duda’. You can use 'websitebuilder' instead.
{% endhint %}

### 3. Install your App

1. Log in to the [Sandbox Environment](https://editor-sandbox.duda.co/login).
2. Click **Create a Responsive Site**.
3. Select a template, give your site a name, and click **create**.
4. Click **App Store** in the side panel.
5. Find your app and click **Add**.
6. Select a plan.

{% hint style="info" %}
**Good to know: Don't see your app or plans?**

The app store only displays apps with valid manifests. Please check that all fields in your manifest are valid and assigned a value.
{% endhint %}

If the endpoint on `installation_endpoint` returned HTTP status code 200, Duda will finish the installation and direct the user to an iframe with the source specified on `base_sso_url`.

Duda will send an installation callback to your installation endpoint in the following format:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "auth": {
        "type": "bearer",
        "authorization_code": "XXX-XXXXX-XXXXX",
        "refresh_token": "YYY-YYYYY-YYYYY",
        "expiration_date": 1554254560438
    },
    "api_endpoint": "https://api-sandbox.duda.co/",
    "installer_account_uuid": "10",
    "account_owner_uuid": "12",
    "user_lang": "en",
    "app_plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
    "recurrency": "MONTHLY",
    "site_name": "1501ccca016a4220861ef07fe2c8eb0d",
    "free": true
}
```
{% endtab %}
{% endtabs %}

| Key                       | Description                                                                                                                                                                                                                                                          |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `api_endpoint`            | <p>The API endpoint for the specific site. This will change depending on which instance (US, EU, etc.) the site was created on.<br><br>This should be relied on when making API calls against a site and <em>not</em> a static API endpoint (i.e., api.duda.co).</p> |
| `installer_account_uuid`  | Duda's unique identifier of the installer.                                                                                                                                                                                                                           |
| `account_owner_uuid`      | Duda's unique identifier of the account owner of the target site.                                                                                                                                                                                                    |
| `user_lang`               | The language of the installer.                                                                                                                                                                                                                                       |
| `app_plan_uuid`           | The unique identifier of the plan that the user chose when installing your app.                                                                                                                                                                                      |
| `recurrency`              | The frequency of the plan (MONTHLY, ANNUAL, or NULL for free plans).                                                                                                                                                                                                 |
| `site_name`               | The unique identifier of the site and the installation.                                                                                                                                                                                                              |
| `free`                    | <p>Denotes whether or not a given installation is a test and should not be seen as a real event.<br><br>You <em>must</em> store this in your database. It's important to have when reconciling reports that Duda will send.</p>                                      |
| `auth.type`               | The authentication type. Currently, Duda only supports`Bearer` authentication.                                                                                                                                                                                       |
| `auth.authorization_code` | The access token to call APIs for the specified `site_name`.                                                                                                                                                                                                         |
| `auth.refresh_token`      | The refresh token to request another `authorization_code` to replace an expired one.                                                                                                                                                                                 |
| `auth.expiration_date`    | The expiration date (in milliseconds) for the `authorization_code`.                                                                                                                                                                                                  |

### 4. Get Site Details

Once Duda starts the installation process, your app can use REST APIs to get data about the site and perform other actions. You can use API calls during the installation phase before you return Duda an HTTP response for the installation callback. Duda will present the user with the progress bar until you return an HTTP response.\
The APIs your app can use are restricted by the `scopes` property of your app manifest. See further details on [available scopes](../reference/scopes.md).

{% hint style="info" %}
**Good to know: Bearer Authentication**

All site APIs require token authentication in addition to the Account Basic Authentication.\
Use the `X-DUDA-ACCESS-TOKEN` header to send the token.
{% endhint %}

### 5. (Optional) Get Account Branding

Use the following call to get the branding of the reseller. This API is available for all apps. Replace the _XXX-XXXXX-XXXXX_ in the token you got in the installation callback under authorization\_code:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X GET https://api-sandbox.duda.co/api/integrationhub/application/site/{{site name}}/branding -u 'AppAccountUser:AppAccountPass' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

You should expect a response in the following format:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "logo": "https://irt-cdn.multiscreensite.com/-resellers-preview/someaccount/logo/2rs7j2mr00to947a6625c6uc1m.png",
    "color": {
        "links": "#8c8c8c",
        "button_background": "#e218c6",
        "button_text": "#fdb33e",
        "text_on_light": "#fdb33e",
        "text_on_dark": "#fdb33e",
        "header_background": "#2c3e50",
        "preview_background": "#d4e4f5"
    },
    "preview_background_image": "none",
    "dashboard_domain": "http://someaccount.editor-sandbox.multiscreensite.com"
}
```
{% endtab %}
{% endtabs %}

### 6. (Optional) Get Reseller Details

Use the following call to get the reseller details (app scope GET\_ACCOUNT\_DETAILS is required):

{% tabs %}
{% tab title="curl" %}
```bash
curl -X GET https://api-sandbox.duda.co/api/integrationhub/application/site/{{site name}}/account/details -u 'AppAccountUser:AppAccountPass' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

You should expect a response of the following format:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "uuid": "10",
    "first_name": "name",
    "last_name": "name",
    "email": "someone@email.com"
}
```
{% endtab %}
{% endtabs %}

### 7. (Optional) Get Content Library

Use the following call to get the site's Content Library:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X GET https://api-sandbox.duda.co/api/integrationhub/application/site/{{site name}}/content -u 'AppAccountUser:AppAccountPass' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

For a full reference of the content library data structure, see [Duda's API documentation](https://developer.duda.co/reference#get-content-library-data).

{% hint style="warning" %}
**Heads up: Validity of Content Library data**

The Content Library is a repository used by web pros for storing assets that they use during the site building process.\
**The data in the Content Library is not verified.** In particular, emails, phone numbers, and addresses are not verified.
{% endhint %}

### 8. (Optional) Refresh `authorization_code`

Every 12 hours the authentication token is invalidated. To receive the new token you need to send the following request with the refresh token you received when installing the app:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST https://api-sandbox.duda.co/api/integrationhub/application/{{appUuid}}/token/refresh -H 'Content-Type: application/json' -d '{"refreshToken": "YYY-YYYYY-YYYYY"}'
```
{% endtab %}
{% endtabs %}

You should expect a response in the following format:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "type": "bearer",
    "authorization_code": "XXX-XXXXX-XXXXX",
    "refresh_token": "YYY-YYYYY-YYYYY",
    "expiration_date": 1555550616864
}
```
{% endtab %}
{% endtabs %}

For further reading on [Authentication & Token Management](https://developer.duda.co/docs/authentication)

{% hint style="info" %}
**Good to know:** For all available APIs, see the complete [REST API documentation](broken-reference) for the app store.
{% endhint %}

### 9. Upgrade the App

To upgrade your app plan, open the app store and click **upgrade** on your app card.\
Select the new plan you want to upgrade to.

Duda will send a callback event with a payload with the following format to the endpoint registered under `updowngrade_installation_endpoint` in your manifest:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "app_plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
    "recurrency": "MONTHLY",
    "site_name": "1501ccca016a4220861ef07fe2c8eb0d"
}
```
{% endtab %}
{% endtabs %}

Once received, update your app behavior to the new feature plan. The Duda UI will wait until the app responds to the callback in order to finish the upgrade process.

### 10. Open the App

Duda will render an iframe to the URL specified in the manifest under `base_sso_url`. The URL will be in the following format:

{% tabs %}
{% tab title="HTTP" %}
```http
https://app.domain.com/websitebuilder?site_name={{site name}}&timestamp={{time stamp}}&lang={{use langauge code}}&is_white_label={{true/false}}&iframeSDKSrc={{SDK URL}}&current_user_uuid={{user uuid}}&secure_sig=SIGNATURE
```
{% endtab %}
{% endtabs %}

### 11. Uninstall the App

To uninstall your app, open the app store, click on your app card, then click _**remove app**_.

Duda will send a callback event with a payload with the following format to the endpoint registered under `uninstallation_endpoint` in your manifest:

{% tabs %}
{% tab title="JSON" %}
```json
{
  "site_name": "1501ccca016a4220861ef07fe2c8eb0d",
  "free": false
}
```
{% endtab %}
{% endtabs %}

Once received, acknowledge the uninstall. The Duda UI will wait until the app responds to the callback in order to finish the upgrade process.

{% hint style="warning" %}
**Heads up: Data Retention**

Duda expects apps to retain data and configuration of each removed installation for 60 days. During this period, if the app is installed again the data and configuration should be recovered.
{% endhint %}
