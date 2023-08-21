---
description: Getting a site via App Store APIs
---

# Get Site

{% tabs %}
{% tab title="JSON" %}
```json
{
  "account_name": "owner@example.com",
  "external_uid": "an-external-reference",
  "site_domain": "example.com",
  "google_tracking_id": "string",
  "lang": "en",
  "additionalLanguages":["de"],
  "site_business_info": {
    "business_name": "Example Business",
    "address": {
      "street": "1240 Main ST.",
      "city": "San Francisco",
      "state": "CA",
      "country": "United States",
      "zip_code": "94122"
    },
    "phone_number": "(123) 456-7890",
    "email": "business@example.com",
    "opentable_info": []
  },
  "site_alternate_domains": {
    "domains": [
      "example.org",
      "example.net"
    ],
    "is_redirect": true
  },
  "site_seo": {
    "og_image": "https://example.com/link/to/image",
    "title": "Example Title",
    "description": "A description of the website."
  },
  "schemas": {
    "local_business": {
      "enabled": true,
      "status": "MISSING_REQUIRED_FIELDS",
      "missing_required_fields": [
        "Business Name",
        "Geo Coordinates",
        "Physical Address"
      ],
      "missing_recommended_fields": [
        "Phone Number",
        "Image"
      ]
    }
  },
  "site_name": "6c56394c",
  "template_id": 1027437,
  "site_default_domain": "example.multiscreensite.com",
  "preview_site_url": "https://exmaple.com/link/to/preview",
  "overview_site_url": "https://exmaple.com/home/dashboard/overview/6c56394c",
  "editor_site_url":"https://example.com/home/site/6c56394c",
  "last_published_date": "2016-11-15T22:55:53",
  "first_published_date": "2016-04-03T04:36:54",
  "force_https": false,
  "last_reset_by": "developer@example.com",
  "certificate_status": "COMPLETE",
  "modification_date": "2016-11-15T22:55:53",
  "creation_date": "2016-04-01T04:36:54",
  "publish_status": "PUBLISHED",
  "thumbnail_url": "https://example.com/link/to/image",
  "canonical_url":"https://www.example.com/",
  "store_status": "NONE"
}
```
{% endtab %}
{% endtabs %}

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/site/{site_name}" summary="" %}
{% swagger-description %}
Get the details of the website the App is installed on. Great for getting the domain, account owner, preview URL, language(s)
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" required="true" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" required="true" %}
Your App Account's username and password, based64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "account_name": "russ@duda.co",
  "site_seo": {
    "og_image": null,
    "title": null,
    "description": null
  },
  "schemas": {
    "local_business": {
      "enabled": false,
      "status": null,
      "missing_required_fields": null,
      "missing_recommended_fields": null
    }
  },
  "site_business_info": {
    "email": "mymail@mailservice.com",
    "opentable_info": []
  },
  "site_name": "6198d674fe924478a3f1e0b2adc2ee3a",
  "template_id": 1041972,
  "site_default_domain": "russ18408d87.sandbox.multiscreensite.com",
  "preview_site_url": "http://russ.editor-sandbox.multiscreensite.com/preview/6198d674fe924478a3f1e0b2adc2ee3a",
  "edit_site_url": "http://russ.editor-sandbox.multiscreensite.com/home/site/6198d674fe924478a3f1e0b2adc2ee3a",
  "overview_site_url": "http://russ.editor-sandbox.multiscreensite.com/home/dashboard/overview/6198d674fe924478a3f1e0b2adc2ee3a",
  "force_https": false,
  "lang": "en",
  "modification_date": "2022-11-18T23:43:23",
  "creation_date": "2022-11-18T23:43:11",
  "publish_status": "NOT_PUBLISHED_YET",
  "store_status": "NONE",
  "cookie_notification": {
    "enabled": false
  }
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}
