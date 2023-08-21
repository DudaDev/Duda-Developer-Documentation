---
description: Enabling better SEO for local businesses, automatically, via the Duda API
---

# How to Enable Local Business Schema

## Goals

By the end of this guide, you'll be able to pass data into the content library that will be used for Local Business Schema, enable schema on the website, and then make sure that it's live on the web for that business.

## Requirements

In order to complete this, you'll need:

* Access to the Duda API and the related username and password
* An already created website `site_name` value
* Sample (or real) location data to fill into the content library

Examples for this how-to leverage the [NodeJS Client libraries](../../reference/partner-api-reference/libraries-sdks.md).

### 1. Pass Data into the Content Library

Insert the business data with all the required fields into the primary location in the content library for the site. Below you'll see we're passing in full business details.

{% tabs %}
{% tab title="Node" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

//api details
const duda = new Duda({
  user: "{user}",
  pass: "{pass}",
  env: Duda.Environments.Direct
});

duda.content.update({"site_name":"d318193e", 
  "location_data":{
    "phones":[
      {
        "phoneNumber":"123-123-1234",
        "label":"Main Phone"
      }
    ],
    "emails":[
      {
        "emailAddress":"support@duda.co",
        "label":"Support Email"
      }
    ],
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
  "site_texts":{
    "overview":"Oh, Duda? Duda is a variation of \"Dude\", who just happens to be the main character in one of our favorite movies of all time: The Big Lebowski. You should watch it some time. Look out for that ferret!", "services":"- Responsive Website Builder",
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
      "alt":"Example Store Banner "
    }
  ]
}).then(resp => console.log(resp))
.catch(resp => console.log(resp))
```
{% endtab %}
{% endtabs %}

### 2. Enable Schema

After adding the required data to the website, we want to enable schema on the website. This is done on the [Site API](../../reference/partner-api-reference/sites.md).

{% tabs %}
{% tab title="Node" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

//api details
const duda = new Duda({
  user: "{user}",
  pass: "{pass}",
  env: Duda.Environments.Direct
});

duda.sites.update({
  "site_name":"d318193e",
  "schemas":{
    "local_business":{
      "enabled":true
    }
  }
})
.then(resp => console.log(`successfully enabled schema on the site`))
.catch(e => console.log(e))
```
{% endtab %}
{% endtabs %}

### 3. Check the Schema Status

The [Site Details](../../reference/partner-api-reference/sites.md#get-site-1) endpoint returns a [schemas object](../../reference/partner-api-reference/sites.md#schemas), which includes the Local Business Schema status as well as any missing fields. The status property can be checked to see if the information is `VALID`, or if additional fields should be populated within the content library.

{% tabs %}
{% tab title="Node" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

//api details
const duda = new Duda({
  user: "{user}",
  pass: "{pass}",
  env: Duda.Environments.Direct
});

duda.sites.get({"site_name":"d318193e"})
.then(resp => console.log(`Schema status is: ${resp.schemas.local_business.status}`))
.catch(e => console.log(e))

//outputs: Schema status is: VALID
```
{% endtab %}
{% endtabs %}

### 4. (Optional) Update the Type of Business

[Schema.org supports many types of business](../tutorials/local-business-schema.md#7.-business-types) and you can pass the most relevant business into the content library settings of the website.

{% tabs %}
{% tab title="Node" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

//api details
const duda = new Duda({
  user: "{user}",
  pass: "{pass}",
  env: Duda.Environments.Direct
});

duda.content.update({
  "site_name":"d318193e",
  "location_data":{
    "schema":{
      "type": "CafeOrCoffeeShop"
    }
  }
}).then(resp => console.log('success'))
.catch(resp => console.log('error'))
```
{% endtab %}
{% endtabs %}

### 5. Republish Website

Finally, we're going to publish (or republish) the website. This ensures the schema is successfully embedded and enabled on the live site.

{% tabs %}
{% tab title="Node" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

//api details
const duda = new Duda({
  user: "{user}",
  pass: "{pass}",
  env: Duda.Environments.Direct
});

duda.sites.publish({
  "site_name":"d318193e"
}).then(resp => console.log('success'))
.catch(resp => console.log('error'))
```
{% endtab %}
{% endtabs %}

That's it! You've now successfully enabled schema on a website.
