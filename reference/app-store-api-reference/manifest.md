# Manifest

The Manifest is your way to configure your App settings within the Duda environment. It contains all technical integration details and also marketing/profile-based details. We currently have two methods:

* [Get](manifest.md#get)
* [Update](manifest.md#update)

## Limitations of the Manifest

You cannot perform the following actions via the Manifest:

* Add/delete plans
* Change app or plan UUID
* Set plan price
* Change public key
* Change scopes

These items must be managed by Duda currently. If you need to change them -- please contact Duda.

## URL Policies

* All URLs, like SSO, endpoints, etc.. must use the HTTPS protocol.

## Manifest Details:

| Item                                                   | Description                                                                                                                                                                                                   | Comments/format                                                                                                                  |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **supported\_locales**                                 | The profile presented to [white-labeled](https://developer.duda.co/docs/white-labing-apps) users (not Duda aware).                                                                                            | Use the following ENUM: en, es, zh, pt, fr, de, tr, it, nl, fi, pl                                                               |
| **app\_profile**                                       | The information presented in the 'about' tab of the app's more-info popup.                                                                                                                                    |                                                                                                                                  |
| **app\_profile\["lang"]**                              | Profile per language                                                                                                                                                                                          | App are not displayed if they don't have a valid profile. Use the following enum: en, es\_ar, zh, pt, fr, de, tr, it, nl, fi, pl |
| **app\_profile\["lang"].app\_name**                    | The app name presented on the app's card, in the more-info popup and all other mentions of the app.                                                                                                           |                                                                                                                                  |
| **app\_profile\["lang"].app\_logo**                    | Branded logo                                                                                                                                                                                                  | URL, png/jpg, minimum size 100x100px                                                                                             |
| **app\_profile\["lang"].app\_short\_description**      | Presented on the app's card                                                                                                                                                                                   | The short description should be between 55-105 characters long.                                                                  |
| **app\_profile\["lang"] .app\_long\_description**      | Presented in the more-info popup.                                                                                                                                                                             | Supports HTML tags. A long description should be less than 500 characters long.                                                  |
| **app\_profile\["lang"] .public\_page**                | A link to the app's public page                                                                                                                                                                               | URL, HTTPS                                                                                                                       |
| **app\_profile\["lang"] .terms\_of\_service\_page**    | A link to the app's terms of service                                                                                                                                                                          | URL, HTTPS                                                                                                                       |
| **app\_profile\["lang"] .privacy\_note\_page**         | A link to the app's privacy note                                                                                                                                                                              | URL, HTTPS                                                                                                                       |
| **app\_profile\["lang"] .app\_screenshots**            | An array of screenshots with descriptions. Displayed in the more-info popup.                                                                                                                                  | Object, URL + ALT tag, recommended size: 1,278 x 948 (4:3 aspect ratio)                                                          |
| **wl\_app\_profile\["lang"]**                          | The profile presented to [white-labeled](https://developer.duda.co/docs/white-labing-apps) users (not Duda aware).                                                                                            | Do no mention the app's branded name in the white-labeled profile.                                                               |
| **wl\_app\_profile\["lang"] .app\_logo**               | White labeled logo.                                                                                                                                                                                           | URL, png/jpg, minimum size 100x100px                                                                                             |
| **wl\_app\_profile\["lang"] .app\_short\_description** | Presented on the app's card.                                                                                                                                                                                  | Do no mention the app's branded name. The short description should be between 55-105 characters longs.                           |
| **wl\_app\_profile\["lang"] .app\_long\_description**  | Presented in the more-info popup.                                                                                                                                                                             | Supports HTML tags. Do no mention the app's branded name. The long description should be less than 500 characters longs.         |
| **wl\_app\_profile\["lang"] .app\_screenshots**        | An array of screenshots with descriptions. Displayed in the more-info popup.                                                                                                                                  | Object, URL + ALT tag, recommended size: 1,278 x 948 (4:3 aspect ratio). Do no mention the app's branded name.                   |
| **visible\_to\_clients**                               | Is the app visible to users of type ['client'](https://www.duda.co/client-management/client-permissions)                                                                                                      | Boolean                                                                                                                          |
| **default\_plan\_uuid**                                | Use to define a plan which will be [installed by default](https://developer.duda.co/docs/app-plans-and-upgrades#section-setting-up-a-free-trial) without asking the user to select a plan.                    | UUID of a free plan with grade 0.                                                                                                |
| **required\_fields**                                   | An array or mandatory fields that needs to be added to the site's [content library](https://support.duda.co/hc/en-us/articles/360042436074-Manage-and-Import-Content) before the application can in installed | Can be either "EMAIL" or "LOCATION"                                                                                              |

## Get

{% swagger method="get" path="/integrationhub/application/{app_uuid}" baseUrl="https://api-sandbox.duda.co/api" summary="Get" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get the manifest of an App.
{% endswagger-description %}

{% swagger-parameter in="path" name="app_uuid" type="string" required="true" %}
UUID of the App
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
  "public_key": "MIIBI...",
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
      "plan_type": "free",
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
      "plan_type": "paid",
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
  ],
  "default_plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
  "required_fields": [
    "EMAIL",
    "LOCATION"
  ],
  "is_in_beta": false,
  "visible_to_clients": true,
  "window_type": "IFRAME|NEW_TAB"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/app_uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update

{% swagger method="post" path="/integrationhub/application/{app_uuid}" baseUrl="https://api-sandbox.duda.co/api" summary="Get Client Permissions" expanded="false" %}
{% swagger-description %}
Update the manifest of an App.
{% endswagger-description %}

{% swagger-parameter in="path" name="app_uuid" type="string" required="true" %}
UUID of the App
{% endswagger-parameter %}

{% swagger-parameter in="body" name="UUID" type="string" %}
UUID of the App
{% endswagger-parameter %}

{% swagger-parameter in="body" name="webhooks" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="scopes" type="array of strings" %}
An array of strings of supported scopes. See documentation for all supported scopes.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="public_key" type="string" %}
Your Apps public key, generated at time of App creation. Will never change.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="installation_endpoint" type="string" %}
URL Where Duda will notify when a website installs your App.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="uninstallation_endpoint" type="string" %}
URL Where Duda will notify when someone uninstalls your App.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="updowngrade_installation_endpoint" type="string" %}
URL Where Duda will notify upon plan upgrade or change of state for your App.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="base_sso_url" type="string" %}
URL of your App UI where Duda should SSO users into.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="supported_locales" type="array of strings" %}
Two character language codes your App supports.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="app_profile" type="object" %}
An object containing language key that points to the profile for that language.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="wl_app_profile" type="object" %}
The white labeled version of your App profile, keyed with a language code.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="app_plans" type="array of objects" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="default_plan_uuid" type="string" %}
Skips the select plan selection page and allows users to install only a specific starting plan. Plan must be free or trial.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="required_fields" type="array of strings" %}
Required fields that must exist in the content library before installing. Can be "EMAIL" and "LOCATION".
{% endswagger-parameter %}

{% swagger-parameter in="body" name="window_type" type="string" %}
How your App SSO is opened from Duda. IFRAME stronlgy recommended.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="visible_to_clients" type="bool" %}
If the App will be shown to end clients (customers of an agency)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="is_in_beta" type="bool" %}
If the App should be shown as 'coming soon' in the App Store.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
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
  "public_key": "MIIBI...",
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
      "plan_type": "free",
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
      "plan_type": "paid",
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
  ],
  "default_plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
  "required_fields": [
    "EMAIL",
    "LOCATION"
  ],
  "is_in_beta": false,
  "visible_to_clients": true,
  "window_type": "IFRAME|NEW_TAB"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up: No partial updates**

Please make sure to send the full manifest request body when updating a manifest. We do not support partial updates at this time.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/app_uuid \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '
{
  "visible_to_clients": true,
  "is_in_beta": false
}
'
```
{% endtab %}
{% endtabs %}
