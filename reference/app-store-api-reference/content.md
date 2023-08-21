# Content

## Settings Object

{% tabs %}
{% tab title="JSON" %}
```json
{
  "location_data":{
    "phones":[
      {
        "phoneNumber":"123-123-1234",
        "label":"Russ Phone"
      },
      {
        "phoneNumber":"18001234567",
        "label":"Duda Phone"
      }
    ],
    "emails":[
      {
        "emailAddress":"api@duda.co",
        "label":"API Email"
      },
      {
        "emailAddress":"support@duda.co",
        "label":"Support Email"
      }
    ],
    "schema": {
      "type": "Resort",
      "custom_fields":[
        {
          "name":"acceptsReservations",
          "value":true
        },
        {
          "name":"priceRange",
          "value":"$$$"
        }
      ]
    },
    "label":"Duda HQ",
    "social_accounts":{
      "tripadvisor":"Restaurant_Review-g32849-d2394400-Reviews-Oren_s_Hummus_Shop-Palo_Alto_California.html",
      "youtube":"UCPMwzOc1Su-s2z-J1xiU9ig",
      "facebook":"duda",
      "yelp":"orens-hummus-shop-palo-alto",
      "pinterest":"michelleobama",
      "google_plus":"+Dudamobile577",
      "linkedin":"duda",
      "instagram":"orenshummus",
      "snapchat":"michelleobama",
      "twitter":"dudamobile",
      "rss":"https://www.duda.co/blog/feed/",
      "vimeo":"dudamobile",
      "reddit":"duda"
    },
    "address":{
      "streetAddress":"577 College Ave",
      "postalCode":"94306",
      "region":"CA",
      "city":"Palo Alto",
      "country":"US"
    },
    "address_geolocation":"1833 Harvard St NW, Washington, DC 20009, USA",
    "geo":{
      "longitude":"-122.4757527166",
      "latitude":"37.502439189002"
    },
    "logo_url":"https://du-cdn.multiscreensite.com/duda_website/img/home/agencies.svg",
    "business_hours":[
      {
        "days":[
          "MON",
          "TUE",
          "WED",
          "THU",
          "FRI"
        ],
        "open":"09:00",
        "close":"18:00"
      }
    ]
  },
  "additional_locations":[
    {
      "uuid":"276169839",
      "phones":[
        {
          "phoneNumber":"123-123-1234",
          "label":""
        }
      ],
      "emails":[
        
      ],
      "label":"Duda Tel Aviv",
      "social_accounts":{
        
      },
      "address":{
        
      },
      "geo":{
        "longitude":"34.78337",
        "latitude":"32.07605"
      },
      "logo_url":null,
      "business_hours":null
    }
  ],
  "site_texts":{
    "overview":"Oh, Duda? Duda is a variation of \"Dude\", who just happens to be the main character in one of our favorite movies of all time: The Big Lebowski. You should watch it some time. Look out for that ferret!",
    "services":"- Responsive Website Builder",
    "custom":[
      {
        "label":"Example CTA 1",
        "text":"THE WEB DESIGN PLATFORM FOR Scaling Your Agency"
      },
      {
        "label":"Example CTA 2",
        "text":"THE WEB DESIGN PLATFORM FOR\nBuilding Websites Faster"
      }
    ],
    "about_us":"Duda is a leading website builder for web professionals and agencies of all sizes. Our website builder enables you to build amazing, feature-rich websites that are perfectly suited to desktop, tablet and mobile. Our mobile builder enables you to build mobile-only sites from scratch, or based on an existing desktop site or Facebook business page. Duda allows professionals and agencies to build high-converting, personalized websites at scale. Duda optimizes each and every site for Google PageSpeed."
  },
  "business_data":{
    "name":"Duda",
    "logo_url":"https://www.duda.co/developers/REST-API-Reference/images/duda.svg"
  },
  "site_images":[
    {
      "label":"Example Store Logo",
      "url":"https://irt-cdn.multiscreensite.com/7536fe2010ed4f7ea68e21d0cb868e01/dms3rep/multi/ice_cream_logo_b_w-18-300x300.svg",
      "alt":"Example Store Logo"
    },
    {
      "label":"Example Store Banner",
      "url":"https://irt-cdn.multiscreensite.com/7536fe2010ed4f7ea68e21d0cb868e01/dms3rep/multi/sign_icecream_shop-1000x1108.jpg",
      "alt":"Example Store Banner"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>location_data</strong></td><td><em>object</em></td><td>Contains location-specific data for the primary location associated with a site.<br><br><a href="content.md#location_data-and-additional_locations">See the section below for details</a>.</td></tr><tr><td><strong>additional_locations</strong></td><td><em>object</em></td><td>Contains location-specific data for any secondary/child locations associated with a site.<br><br><a href="content.md#location_data-and-additional_locations">See the section below for details</a>.</td></tr><tr><td><strong>site_texts</strong></td><td><em>object</em></td><td>Contains the standard and custom text strings. Each field has a max length of 2000 characters.<br><br><a href="content.md#global-properties-returned">See the section below for details</a>.</td></tr><tr><td><strong>business_data</strong></td><td><em>object</em></td><td>Contains the <code>name</code> of the business and the primary image <code>logo_url</code> of the website.<br><br><a href="content.md#global-properties-returned">See the section below for details</a>.</td></tr><tr><td><strong>site_images</strong></td><td><em>object</em></td><td>Images that can be set and used within the design of the website. If you have the data, you should populate the alt value.<br><br><a href="content.md#global-properties-returned">See the section below for details</a>.</td></tr></tbody></table>

#### location\_data & additional\_locations

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>phones</strong></td><td><em>object[]</em></td><td>Contains phone numbers for this location. The object allows for a friendly label name and the actual phone number. Note that there is no specific requirement for phone numbers, Duda will display this in the same format you submit it in. Max 80 characters each.<br><br><a href="content.md#phone">See the section below for details</a>.</td></tr><tr><td><strong>emails</strong></td><td><em>object[]</em></td><td>Contains all email addresses associated with this location. The object allows for a friendly label name and the actual email address. Max 80 characters each.<br><br><a href="content.md#email">See the section below for details</a>.</td></tr><tr><td><strong>label</strong></td><td><em>string</em></td><td>A simple name for this location. This is displayed in the Duda Content Library UI related to this location. Max 80 characters.</td></tr><tr><td><strong>schema</strong></td><td><em>object</em></td><td>Details of the location/organizational schema that's generated. <strong>Note: only available as a property for <code>location_data</code>, setting schema properties for <code>additional_locations</code> is not currently supported.</strong></td></tr><tr><td><strong>social_accounts</strong></td><td><em>object</em></td><td>The profile name of this location's social networks. You must pass only the profile name/ID. Do not pass the full URL (e.g., <a href="https://wwwfacebook.com/duda">https://wwwfacebook.com/duda</a>). We support the following social networks: Facebook, Twitter, Yelp, Foursquare, Google Plus, Instagram, Youtube, Linkedin, Pinterest, Vimeo, RSS, Reddit, Trip Advisor &#x26; Snapchat.<br><br><a href="https://developer.duda.co/reference/site-content-content-library-object#social_accounts">See the section below for details</a><a href="content.md#social_accounts">.</a></td></tr><tr><td><strong>address</strong></td><td><em>object</em></td><td>Contains all fields required to display an address: streetAddress, postalCode, region, city, country.<br><br><a href="content.md#address">See the section below for details</a>.</td></tr><tr><td><strong>address_geolocation</strong></td><td><em>string</em></td><td>A geocode address string used to get LAT/LON from a geocoding map service. This is generated within the Duda Editor UI when searching for an address. <strong>Note: You can't update the geolocation string via the API (you can only read it).</strong></td></tr><tr><td><strong>geo</strong></td><td><em>object</em></td><td>An object containing the LAT and LON of the address. Duda will return this if we've identified an address in the editor for this location, but we will not automatically generate it. You can pass this if you know the exact LAT/LON.</td></tr><tr><td><strong>logo_url</strong></td><td><em>string</em></td><td>A URL directly referencing the logo of this location. Must be a public URL and be served over HTTPS.</td></tr><tr><td><strong>business_hours</strong></td><td><em>object[]</em></td><td>An array containing each day of the week and the hours that the location opens and closes. For each set of hours, you can pass an array of days: MON, TUE, WED, THU, FRI, SAT, SUN that applies to those hours. Open and close hours must be in 24HH:MM format. So, for example, 7:30 am would be: 07:30 and 5 pm would be 17:00. If the business is closed on a certain day, please omit it from the data set. If the business is open 24 hours a day, you should pass the hours as 00:00 to 24:00.<br><br><a href="content.md#business_hours">See the section below for details</a>.</td></tr></tbody></table>

#### phone

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>phoneNumber</strong></td><td><em>string</em></td><td>A specific phone number.</td></tr><tr><td><strong>label</strong></td><td><em>string</em></td><td>A label to associate with the above phone number.</td></tr></tbody></table>

#### email

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>emailAddress</strong></td><td><em>string</em></td><td>A specific email address.</td></tr><tr><td><strong>label</strong></td><td><em>string</em></td><td>A label to associate with the above email address.</td></tr></tbody></table>

#### schema

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>type</strong></td><td><em>string</em></td><td>The type of LocalBusinessSchema for this business. <a href="https://developer.duda.co/docs/local-business-schema">Full list of types can be found here.</a></td></tr><tr><td><strong>split_address_1_field</strong></td><td><em>bool</em></td><td>An array of objects with <code>name</code> and <code>value</code> properties for additional schema fields. <a href="https://developer.duda.co/docs/local-business-schema">This allows you to add any schema fields that Duda does not support via the content library data.</a></td></tr></tbody></table>

#### social\_accounts

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>tripadvisor</strong></td><td><em>string</em></td><td>A TripAdvisor page ID.</td></tr><tr><td><strong>youtube</strong></td><td><em>string</em></td><td>A TripAdvisor page ID.</td></tr><tr><td><strong>facebook</strong></td><td><em>string</em></td><td>A Facebook page ID.</td></tr><tr><td><strong>yelp</strong></td><td><em>string</em></td><td>A Yelp page ID.</td></tr><tr><td><strong>pinterest</strong></td><td><em>string</em></td><td>A Pinterest page ID.</td></tr><tr><td><strong>linkedin</strong></td><td><em>string</em></td><td>A Linkedin page ID.</td></tr><tr><td><strong>instagram</strong></td><td><em>string</em></td><td>An Instagram page ID.</td></tr><tr><td><strong>snapchat</strong></td><td><em>string</em></td><td>A Snapchat page ID.</td></tr><tr><td><strong>twitter</strong></td><td><em>string</em></td><td>A Twitter page ID.</td></tr><tr><td><strong>rss</strong></td><td><em>string</em></td><td>A link to the site's RSS feed.</td></tr><tr><td><strong>vimeo</strong></td><td><em>string</em></td><td>A Vimeo page ID.</td></tr><tr><td><strong>reddit</strong></td><td><em>string</em></td><td>A Reddit page ID.</td></tr><tr><td><strong>foursquare</strong></td><td><em>string</em></td><td>A Foursquare page ID.</td></tr></tbody></table>

#### address

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>streetAddress</strong></td><td><em>string</em></td><td>The business's street address.</td></tr><tr><td><strong>postalCode</strong></td><td><em>string</em></td><td>The business's postal code.</td></tr><tr><td><strong>region</strong></td><td><em>string</em></td><td>The region where the business is located.</td></tr><tr><td><strong>city</strong></td><td><em>string</em></td><td>The city where the business is located.</td></tr><tr><td><strong>country</strong></td><td><em>string</em></td><td>The country where the business is located.</td></tr></tbody></table>

#### geo

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>longitude</strong></td><td><em>string</em></td><td></td></tr><tr><td><strong>latitude</strong></td><td><em>string</em></td><td></td></tr></tbody></table>

#### business\_hours

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>days</strong></td><td><em>string[]</em></td><td>[ "MON", "TUE", "WED", "THU", "FRI" ]</td></tr><tr><td><strong>open</strong></td><td><em>string</em></td><td>The time the business opens.</td></tr><tr><td><strong>close</strong></td><td><em>string</em></td><td>The time the business closes.</td></tr></tbody></table>

#### Global Properties Returned

Below is website content that does not relate to a specific location. This is global data stored across the website and is not related to a specific location.

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>site_texts</strong></td><td><em>object</em></td><td>Containing overview, services, about_us and custom text strings. Each field has a max length of 2000 characters.</td></tr><tr><td><strong>custom</strong></td><td><em>object[]</em></td><td>An array that contains custom text strings. These will each have a label &#x26; text associated with them. These can be used for storing site data or information about the business.</td></tr><tr><td><strong>business_data</strong></td><td><em>object</em></td><td>Set the <code>name</code> of the business and the primary image <code>logo_url</code> of the website.</td></tr><tr><td><strong>site_images</strong></td><td><em>object[]</em></td><td>Images that can be set and used within the design of the website. If you have the data, you should populate the alt value.</td></tr></tbody></table>

## Get Content Library

{% swagger method="get" baseUrl="https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="Get Content Library" path="/integrationhub/application/site/{site_name}/content" %}
{% swagger-description %}
Get the data that exists within the content library of a website.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "location_data": {
    "phones": [
      {
        "phoneNumber": "123-123-1234",
        "label": "Russ Phone"
      },
      {
        "phoneNumber": "18001234567",
        "label": "Duda Phone"
      }
    ],
    "emails": [
      {
        "emailAddress": "api@duda.co",
        "label": "API Email"
      },
      {
        "emailAddress": "support@duda.co",
        "label": "Support Email"
      }
    ],
    "label": "Duda HQ",
    "social_accounts": {
      "tripadvisor": "Restaurant_Review-g32849-d2394400-Reviews-Oren_s_Hummus_Shop-Palo_Alto_California.html",
      "youtube": "UCPMwzOc1Su-s2z-J1xiU9ig",
      "facebook": "duda",
      "yelp": "orens-hummus-shop-palo-alto",
      "pinterest": "michelleobama",
      "google_plus": "+Dudamobile577",
      "linkedin": "duda",
      "instagram": "orenshummus",
      "snapchat": "michelleobama",
      "twitter": "dudamobile",
      "rss": "https://www.duda.co/blog/feed/",
      "vimeo": "dudamobile",
      "reddit": "duda"
    },
    "address": {
      "streetAddress": "577 College Ave",
      "postalCode": "94306",
      "region": "CA",
      "city": "Palo Alto",
      "country": "US"
    },
    "address_geolocation": "1833 Harvard St NW, Washington, DC 20009, USA",
    "geo": {
      "longitude": "-122.4757527166",
      "latitude": "37.502439189002"
    },
    "logo_url": "https://du-cdn.multiscreensite.com/duda_website/img/home/agencies.svg",
    "business_hours": [
      {
        "days": [
          "SAT",
          "SUN"
        ],
        "open": "00:00",
        "close": "00:00"
      },
      {
        "days": [
          "MON",
          "TUE",
          "WED",
          "THU",
          "FRI"
        ],
        "open": "09:00",
        "close": "18:00"
      }
    ]
  },
  "additional_locations": [
    {
      "uuid": "276169839",
      "phones": [
        {
          "phoneNumber": "123-123-1234",
          "label": ""
        }
      ],
      "emails": [],
      "label": "Duda Tel Aviv",
      "social_accounts": {},
      "address": {},
      "geo": {
        "longitude": "34.78337",
        "latitude": "32.07605"
      },
      "logo_url": null,
      "business_hours": null
    }
  ],
  "site_texts": {
    "overview": "Oh, Duda? Duda is a variation of \"Dude\", who just happens to be the main character in one of our favorite movies of all time: The Big Lebowski. You should watch it some time. Look out for that ferret!",
    "services": "- Responsive Website Builder",
    "custom": [
      {
        "label": "Example CTA 1",
        "text": "THE WEB DESIGN PLATFORM FOR Scaling Your Agency"
      },
      {
        "label": "Example CTA 2",
        "text": "THE WEB DESIGN PLATFORM FOR\nBuilding Websites Faster"
      }
    ],
    "about_us": "Duda is a leading website builder for web professionals and agencies of all sizes. Our website builder enables you to build amazing, feature-rich websites that are perfectly suited to desktop, tablet and mobile. Our mobile builder enables you to build mobile-only sites from scratch, or based on an existing desktop site or Facebook business page. Duda allows professionals and agencies to build high-converting, personalized websites at scale. Duda optimizes each and every site for Google PageSpeed."
  },
  "business_data": {
    "name": "Duda",
    "logo_url": "https://www.duda.co/developers/REST-API-Reference/images/duda.svg"
  },
  "site_images": [
    {
      "label": "Example Store Logo",
      "url": "https://irt-cdn.multiscreensite.com/7536fe2010ed4f7ea68e21d0cb868e01/dms3rep/multi/ice_cream_logo_b_w-18-300x300.svg",
      "alt": "Example Store Logo"
    },
    {
      "label": "Example Store Banner",
      "url": "https://irt-cdn.multiscreensite.com/7536fe2010ed4f7ea68e21d0cb868e01/dms3rep/multi/sign_icecream_shop-1000x1108.jpg",
      "alt": "Example Store Banner"
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Update Content Library

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Update Content Library" path="/integrationhub/application/sites/multiscreen/{site_name}/content" %}
{% swagger-description %}
Update the data that exists within the content library. Once updated the data is ready for immediate use within the editor.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** You only need to pass the data fields you want to update and you do not need to send the entire data object representing the whole content library
{% endhint %}

{% hint style="info" %}
**Good to Know:** For any images you pass into the API, Duda strongly recommends uploading these images to the Duda first as part of the [uploads api](upload-resources-images.md).
{% endhint %}

{% hint style="info" %}
**Good to Know:** The primary location of a business is only managed through the content library API. All additional/child locations are managed by the locations API (documented below).
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/sites/multiscreen/site_name/content \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Publish Content Library

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Publish Content Library" path="/integrationhub/application/site/{site_name}/content/publish" %}
{% swagger-description %}
Push updates already within the content library directly to the live version of the website. This pushes the data that exists within the content library to the live/published version of the website.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content/publish \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Get Location

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="get" summary="Get Location" path="/integrationhub/application/site/{site_name}/content/location/{location_id}" %}
{% swagger-description %}
Get data for a specific location.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="location_id" type="string" required="true" %}
The 

`uuid`

 of the location
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "uuid": "367163873",
  "phones": [
    {
      "phoneNumber": "123-123-4321",
      "label": "Main Phone"
    },
    {
      "phoneNumber": "123-123-5321",
      "label": "Scheduling"
    }
  ],
  "emails": [
    {
      "emailAddress": "colorado@duda.co",
      "label": "Colorado Office Email"
    }
  ],
  "label": "Duda Colorado - Goosetail Labs",
  "social_accounts": {
    "twitter": "dudamobile",
    "facebook": "duda"
  },
  "address": {
    "streetAddress": "197 S 104th St C",
    "postalCode": "80027",
    "city": "Louisville",
    "country": "US"
  },
  "address_geolocation": "197 S 104th St C Louisville 80027 US",
  "geo": {
    "longitude": null,
    "latitude": null
  },
  "logo_url": "https://www.duda.co/developers/REST-API-Reference/images/duda.svg",
  "business_hours": [
    {
      "days": [
        "MON",
        "TUE",
        "WED",
        "THU",
        "FRI"
      ],
      "open": "09:00",
      "close": "18:00"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** Only `additional_locations` are available via this API call.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content/location/location_id \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Create Location

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Create Location" path="/integrationhub/application/site/{site_name}/content/location" %}
{% swagger-description %}
Create a new location for a website. This location will be apart of the 

`additional_locations`

 object that is returned from a site's content library.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "uuid": "367163873",
  "phones": [
    {
      "phoneNumber": "123-123-4321",
      "label": "Main Phone"
    },
    {
      "phoneNumber": "123-123-5321",
      "label": "Scheduling"
    }
  ],
  "emails": [
    {
      "emailAddress": "colorado@duda.co",
      "label": "Colorado Office Email"
    }
  ],
  "label": "Duda Colorado - Goosetail Labs",
  "social_accounts": {
    "twitter": "dudamobile",
    "facebook": "duda"
  },
  "address": {
    "streetAddress": "197 S 104th St C",
    "postalCode": "80027",
    "region": "CO",
    "city": "Louisville",
    "country": "USA"
  },
  "geo": null,
  "logo_url": "https://www.duda.co/developers/REST-API-Reference/images/duda.svg",
  "business_hours": [
    {
      "days": [
        "MON",
        "TUE",
        "WED",
        "THU",
        "FRI"
      ],
      "open": "09:00",
      "close": "18:00"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Duda expects a JSON object describing the location details. You can see the full representation to the right.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content/location \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update Location

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Update Location" path="/integrationhub/application/site/{site_name}/content/location/{location_id}" %}
{% swagger-description %}
Update an existing location within the content library. You can only update 

`additional_locations`

 that exist as part of the content library.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="location_id" type="string" required="true" %}
The 

`uuid`

 of the location
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** When you update values of the data, make sure you're updating the entire property. For example, if you update the phone, make sure you send back all valid phone numbers that exist for the location and don't just update a specific phone number.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content/location/location_id \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Delete Location

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="delete" summary="Delete Location" path="/integrationhub/application/site/{site_name}/content/location/{location_id}" %}
{% swagger-description %}
Delete an existing location.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="location_id" type="string" required="true" %}
The 

`uuid`

 of the location
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/content/location/location_id \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
