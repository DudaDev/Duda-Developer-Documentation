---
description: Updating a site via App Store APIs
---

# Update Site

{% tabs %}
{% tab title="JSON" %}
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

{% swagger-parameter in="body" name="site_domain" type="string" %}
The primary domain of the website. Change this with extreme caution.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="default_domain_prefix" type="string" %}
The prefix of the sub-domain or alternate the site first renders under.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="external_uid" type="string" %}
Refers to the owner of the website and some external reference of the website.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="lang" type="string" %}
Two char lang code for the website default language.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="additionalLanguages" type="array of strings" %}
An array of secondary languages for the website, in two character format.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fav_icon" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="force_https" type="string" %}
If the website always redirect visitors to https or not.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="site_seo" type="object" %}

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
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4' \
     --data '
{
  "site_domain": "www.example.com",
  "default_domain_prefix": "example-website",
  "external_uid": "abcdefg",
  "fav_icon": "https://someurl.com/icon.png",
  "force_https": true,
  "site_seo": {
    "og_image": "https://somedomain.com/image.jpg"
  }
}
'
```
{% endtab %}
{% endtabs %}
