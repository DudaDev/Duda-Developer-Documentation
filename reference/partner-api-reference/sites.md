# Sites

## Site Object

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
    "description": "A description of the website.", 
    "no_index": false
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
  "store_status": "active",
  "store_type": "native",
  "labels": [
      {
          "name": "QA team"
      },
      {
          "name": "priority client"
      }
  ]
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>google_tracking_id</strong></td><td><em>string</em></td><td>The Google Tag ID set for this site. This value is empty by default, until set in the UI or via API.</td></tr><tr><td><strong>site_domain</strong></td><td><em>string</em></td><td>The primary domain currently assigned to the Site.</td></tr><tr><td><strong>site_name</strong></td><td><em>string</em></td><td>Duda's unique identifier for the Site.</td></tr><tr><td><strong>canonical_url</strong></td><td><em>string</em></td><td>The URL Duda generates as the canonical and where SEO/Search traffic gets directed to. This handles all the different logic of https vs. http vs www. or no-www for the website.</td></tr><tr><td><strong>account_name</strong></td><td><em>string</em></td><td>The name, usually an email, of the account that owns the Site.</td></tr><tr><td><strong>preview_site_url</strong></td><td><em>string</em></td><td>A direct URL to the white-labeled multi-device preview.</td></tr><tr><td><strong>overview_site_url</strong></td><td><em>string</em></td><td>A URL of the overview page of the site.</td></tr><tr><td><strong>editor_site_url</strong></td><td><em>string</em></td><td>A direct URL to the site editor.</td></tr><tr><td><strong>force_https</strong></td><td><em>bool</em></td><td>Defaults to true. If set to true, the site will be available for both secure and insecure connections.</td></tr><tr><td><strong>last_published_date</strong></td><td><em>datetime</em></td><td>The most recent publication date for the Site.</td></tr><tr><td><strong>first_published_date</strong></td><td><em>datetime</em></td><td>The first publication date for the Site.</td></tr><tr><td><strong>publish_status</strong></td><td><em>string</em></td><td>The current status of the Site: "<strong>PUBLISHED</strong>", "<strong>UNPUBLISHED</strong>", "<strong>NOT_PUBLISHED_YET</strong>".</td></tr><tr><td><strong>site_business_info</strong></td><td><em>object</em></td><td><a href="sites.md#site_business_info">See the section below for details</a>.</td></tr><tr><td><strong>site_seo</strong></td><td><em>object</em></td><td><a href="sites.md#site_seo">See the section below for details</a>.</td></tr><tr><td><strong>external_uid</strong></td><td><em>string</em></td><td>A unique identifier from an external system such as a database. Optional.</td></tr><tr><td><strong>last_reset_by</strong></td><td><em>string</em></td><td>The account that last reset the Site.</td></tr><tr><td><strong>certification_status</strong></td><td><em>string</em></td><td>The status of SSL for the Site: "<strong>COMPLETE</strong>", "<strong>IN_PROGRESS</strong>", "<strong>FAILED</strong>".</td></tr><tr><td><strong>modification_date</strong></td><td><em>datetime</em></td><td>The date of the most recent change to the website, including API calls.</td></tr><tr><td><strong>creation_date</strong></td><td><em>datetime</em></td><td>The created date for the Site.</td></tr><tr><td><strong>thumbnail_url</strong></td><td><em>string</em></td><td>A direct URL to view the Site's thumbnail image which Duda generates for the site.</td></tr><tr><td><strong>store_status</strong></td><td><em>enum</em></td><td>The current state of the store for the site: "<strong>NONE</strong>", "<strong>ACTIVE</strong>", "<strong>SUSPENDED</strong>".</td></tr><tr><td><strong>store_type</strong></td><td><em>enum</em></td><td>The type of store installed on the site: "<strong>NATIVE</strong>", "<strong>THIRDPARTY</strong>"</td></tr><tr><td><strong>site_alternative_domains</strong></td><td><em>object</em></td><td><a href="sites.md#site_alternate_domains">See the section below for details</a>.</td></tr><tr><td><strong>fav_icon</strong></td><td><em>string</em></td><td>A direct URL to download the Site's favicon. Supports: gif, jpg, jpeg, png, ico, png, and bmp.</td></tr><tr><td><strong>lang</strong></td><td><em>string</em></td><td>The primary language set on the website, as a two character string in (<a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO_3166-1_alpha-2</a>)format.</td></tr><tr><td><strong>labels</strong></td><td><em>object</em></td><td><a href="sites.md#labels">See the section below for details</a>.</td></tr></tbody></table>

#### site\_business\_info

Provides structured data about a website or business. Duda will use this information to help populate the website with this data and fill the [content library](https://help.duda.co/hc/en-us/articles/229790908-Manage-Content-Library) with data. All data fields are optional.

<table><thead><tr><th width="274">Property</th><th width="208">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>business_name</strong></td><td><em>string</em></td><td>The name of the business that owns the Site.</td></tr><tr><td><strong>phone_number</strong></td><td><em>string</em></td><td>The phone number of the business.</td></tr><tr><td><strong>address</strong></td><td><em>object</em></td><td><a href="sites.md#address">See the section below for details</a>.</td></tr><tr><td><strong>opentable_info</strong></td><td><em>object</em></td><td>An object containing arrays of possible Open Table IDs.</td></tr></tbody></table>

#### address

Providing an address helps the site creation process by giving Duda more information about the location of the business. For example, if you provide an address, we will automatically populate a maps element and potentially find other resources online to assist in site creation.

<table><thead><tr><th width="274">Property</th><th width="210">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>street</strong></td><td><em>string</em></td><td>The street name of the business.</td></tr><tr><td><strong>state</strong></td><td><em>string</em></td><td>The state where the business is located.</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>The country where the business is located.</td></tr><tr><td><strong>zip_code</strong></td><td><em>string</em></td><td>The zip code or postal code of the business.</td></tr></tbody></table>

#### site\_alternate\_domains

Allows you to define alternate or secondary domains associated with this site. By default, these domains will be 301 redirected to the primary domain. If you change the is\_redirect value to false, the alternate domains will resolve the website instead of performing the redirect. Each alternate domain will need to have its DNS settings configured the same way as the primary domain, read here for how to set these up.

<table><thead><tr><th width="274">Property</th><th width="210">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>domains</strong></td><td><em>string[]</em></td><td>An array of fully qualified domain names for the Site.</td></tr><tr><td><strong>is_redirect</strong></td><td><em>bool</em></td><td>Defaults to true. If set as true, all alternate domains will be set to 301 redirects to the primary domain.</td></tr></tbody></table>

#### site\_seo

Set the default site SEO settings for all pages of this website. Any SEO settings on a page level will override the global setting on the site.

[Please follow see best practices for Open Graph Images](https://developers.facebook.com/docs/sharing/best-practices/#images).

<table><thead><tr><th width="274">Property</th><th width="210">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>og_image</strong></td><td><em>string</em></td><td>The image displayed in URL previews such as social media posts or SMS texts.</td></tr><tr><td><strong>title</strong></td><td><em>string</em></td><td>The default title for the Site that's displayed in tabs. (&#x3C;60 characters)</td></tr><tr><td><strong>description</strong></td><td><em>string</em></td><td>The meta description of the site. (&#x3C;155 characters)</td></tr><tr><td><strong>no_index</strong></td><td><em>bool</em></td><td>Defaults to false. If set as true, the entire site will be set to not index.</td></tr></tbody></table>

#### schemas

The schema's object allows you to enable schema for the website for specific schema objects that exist at the site level. Today, the only schema object supported is LocalBusiness schema.

[Read our guide on implementing Local Business Schema.](https://developer.duda.co/docs/local-business-schema)

The location grabbed from the content library is only from the first/primary location in the content library. We do not support multiple locations, yet.

LocalBusiness schema takes core business information from the [content library](https://support.duda.co/hc/en-us/articles/360042436074-Manage-and-Import-Content) and translates that into the required LocalBusiness schema. This API exists as a validation engine to verify that the data added to the content library passes the minimum data requirement for Local Business.

The schemas object includes a **local\_business** field with the following possible values:

<table><thead><tr><th width="285">Property</th><th width="210">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>enabled</strong></td><td><em>bool</em></td><td>Whether or not a specific local business schema is enabled.</td></tr><tr><td><strong>status</strong></td><td><em>string</em></td><td>The most recent status returned after attempting to enable a specific local business schema.</td></tr><tr><td><strong>missing_required_fields</strong></td><td><em>string[]</em></td><td>An array of required fields that have no value.<br><strong>"Address", "Business Name", "Geo Coordinates", "Image"</strong>.</td></tr><tr><td><strong>missing_recommended_fields</strong></td><td><em>string[]</em></td><td>An array of recommended fields that have no value.<br>"<strong>Phone Number</strong>", "<strong>Email</strong>", "<strong>Hours of Operation</strong>", "<strong>Social</strong>", "<strong>Description</strong>", "<strong>Logo</strong>".</td></tr></tbody></table>

#### labels

Allows you to define site labels for a site. These labels will appear in the sites dashboard.

<table><thead><tr><th width="285">Property</th><th width="210">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>The value of labels applied to your site either through the dashboard or API.</td></tr></tbody></table>

## Get Site

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" path="/sites/multiscreen/{site_name}" summary="Get Site" %}
{% swagger-description %}
Get the details of a site by name.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target Site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "account_name": "example@domain.com",
  "external_uid": "externalReference1",
  "site_domain": "customDomain1.com",
  "lang": "en",
  "additionalLanguages": [
    "de",
    "sp"
  ],
  "site_business_info": {
    "business_name": "Example Business",
    "address": {
      "street": "1240 Main ST.",
      "city": "San Francisco",
      "state": "CA",
      "country": "United States",
      "zip_code": "94122"
    },
    "phone_number": "(415) 123-1234",
    "email": "example@domain.com",
    "opentable_info": []
  },
  "site_alternate_domains": {
    "domains": [
      "example1.com",
      "example2.net"
    ],
    "is_redirect": true
  },
  "site_seo": {
    "og_image": "string",
    "title": "Example Title",
    "description": "Example description. Should be around 155 characters long, but can be upto 320."
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
  "template_id": 20022,
  "site_default_domain": "exampleBusiness.multiscreensite.com",
  "preview_site_url": "http://websitebuilder.websitebusiness.com/preview/6c56394c",
  "last_published_date": "2016-11-15T22:55:53",
  "first_published_date": "2016-04-03T04:36:54",
  "force_https": true,
  "last_reset_by": "ex@dudamobile.com",
  "modification_date": "2016-11-15T22:55:53",
  "creation_date": "2016-04-01T04:36:54",
  "publish_status": "PUBLISHED",
  "thumbnail_url": "https://irp-cdn.multiscreensite.com/423b2d/screenshots/Screenshot.png?timestamp=1565804336000&updated=true",
  "fav_icon": "https://my.duda.co/favicon_d1.ico",
  "store_status": "active",
  "store_type": "native",
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
     --url https://api.duda.co/api/sites/multiscreen/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Site by External ID

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Site by External ID" path="/sites/multiscreen/byexternalid/{external_uid}" %}
{% swagger-description %}
Get the names of Sites that have a specific external id.
{% endswagger-description %}

{% swagger-parameter in="path" type="string" required="true" name="external_uid" %}
The external ID associated with a single or group of Sites.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array" %}
```json
[
  "6c56394c",
  "e714b0ba"
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
     --url https://api.duda.co/api/sites/multiscreen/byexternalid/external_uid \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Create Site" path="/sites/multiscreen/create" %}
{% swagger-description %}
Create a new Site from a Template.
{% endswagger-description %}

{% swagger-parameter in="body" type="string" name="template_id" required="true" %}
The ID of template to apply to the Site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="default_domain_prefix" type="string" %}
Must be between 4-44 characters long.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="lang" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="site_data" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="labels" type="array of objects" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```
{
  "site_name": "28e1182c"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know: We recommend storing the `site_name` in your database**

The `site_name` is a unique string across all Duda websites and will be needed to later access other resources, such as updating the site, getting analytics or granting access.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/create \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Update Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Update Site" path="/sites/multiscreen/update/{site_name}" %}
{% swagger-description %}
Update properties of an existing Site.
{% endswagger-description %}

{% swagger-parameter in="body" type="string" name="site_domain" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" type="string" name="default_domain_prefix" %}
Must be betwee 4-44 characters long.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="external_uid" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="lang" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="fav_icon" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="force_https" type="bool" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="site_seo" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="schemas" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="site_alternate_domains" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="google_tracking_id" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="additionalLanguages" type="array of strings" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="labels" type="array of objects" %}

{% endswagger-parameter %}

{% swagger-response description="" status="204: No Content" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/update/site_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Duplicate Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Duplicate Site" path="/sites/multiscreen/duplicate/{site_name}" %}
{% swagger-description %}
Creates a new Site based on an existing one.
{% endswagger-description %}

{% swagger-parameter in="body" name="new_default_domain_prefix" type="string" %}
The domain prefix for the newly created Site (ex. a value of 'bobspizza' would create a site with a domain of bobspizza.multiscreensite.com.) This must be a unique value across the system.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="new_external_uid" type="string" %}
The external ID for the newly created Site.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="site_name" type="string" %}
The unique identifier of the target Site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": "a6119858"
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
     --url https://api.duda.co/api/sites/multiscreen/duplicate/site_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Publish Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Publish Site" path="/sites/multiscreen/publish/{site_name}" %}
{% swagger-description %}
Takes a Site live and purchases a subscription.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
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
     --url https://api.duda.co/api/sites/multiscreen/publish/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Unpublish Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Unpublish Site" path="/sites/multiscreen/unpublish/{site_name}" %}
{% swagger-description %}
Takes down a Site and suspends it's subscription
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
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
     --url https://api.duda.co/api/sites/multiscreen/unpublish/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Reset Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Rest Site" path="/sites/multiscreen/reset/{site_name}" %}
{% swagger-description %}
Resets a Site to initial state or based on a new template and data.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="template_id" type="string" required="true" %}
The template ID to use when resetting the Site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="site_data" type="object" %}

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
     --url https://api.duda.co/api/sites/multiscreen/reset/site_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Switch Template

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Switch Template" path="/sites/multiscreen/switchTemplate/{site_name}" %}
{% swagger-description %}
Applies a new template to an existing Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="template_id" type="string" %}
The template ID to apply to the existing Site.
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
     --url https://api.duda.co/api/sites/multiscreen/switchTemplate/site_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="delete" summary="Delete Site" path="/sites/multiscreen/{site_name}" %}
{% swagger-description %}
Permanently deletes a Site and cancels all subscriptions.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
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
     --url https://api.duda.co/api/sites/multiscreen/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Site Theme

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Site Theme" path="/sites/multiscreen/{site_name}/theme" %}
{% swagger-description %}
Get the theme of a site by name.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "colors": [
    {
      "id": "color_1",
      "value": "rgba(20,68,57,1)",
      "label": "Primary"
    },
    {
      "id": "color_2",
      "value": "rgba(0,117,89,1)",
      "label": "Secondary"
    },
    {
      "id": "color_3",
      "value": "rgba(255,255,255,1)",
      "label": "Color #3"
    },
    {
      "id": "color_4",
      "value": "rgba(247,154,73,1)",
      "label": "Color #4"
    },
    {
      "id": "color_5",
      "value": "rgba(131,156,234,1)",
      "label": "Color #5"
    },
    {
      "id": "color_6",
      "value": "rgba(227,238,237,1)",
      "label": "Color #6"
    },
    {
      "id": "color_7",
      "value": "rgba(255,246,234,1)",
      "label": "Color #7"
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/theme \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Site Theme

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Update Site Theme" path="/sites/multiscreen/{site_name}/theme" %}
{% swagger-description %}
Update the theme of a site by name.

The request JSON must provide the `id` of the color.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target Site.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="colors" type="object" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

The request JSON must provide the `id` of the color.

{% hint style="warning" %}
**Heads up: Send Entire JSON Body**

The API requires all colors within the site's theme to be sent in order to update.&#x20;
{% endhint %}

{% tabs %}
{% tab title="JSON" %}
```json
{
  "colors": [
    {
      "id": "string",
      "value": "string",
      "label": "string"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

| Data      | Type     | Description                                                                                         |
| --------- | -------- | --------------------------------------------------------------------------------------------------- |
| **id**    | _string_ | Needs to follow the pattern: "color\_". (color\_1, color\_2, etc). This property cannot be changed. |
| **value** | _string_ | RGB/RGBA/HEX color value. This will be converted to RGBA by Duda.                                   |
| **label** | _string_ | 50 chars max. HTML-safe string                                                                      |

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api.duda.co/api/sites/multiscreen/site_name/theme \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "colors": {
    "colors": [
      {
        "id": "string",
        "value": "string",
        "label": "string"
      }
    ]
  }
}
'
```
{% endtab %}
{% endtabs %}
