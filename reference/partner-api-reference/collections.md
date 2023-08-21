# Collections

## Collection Object

A collection is a flexible data store (similar to a database), containing `fields` and `values`.\
The collection API allows the structure of the collection and the data stored within to be created, retrieved, updated, and deleted.

#### Collection Properties

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the returned collection</td></tr><tr><td><strong>customer_lock</strong></td><td><em>string</em></td><td>Lock state for customer editing. One of 'unlocked', 'structure_locked' or 'locked'. 'Unlocked' gives access to edit data and the structure (fields) of a collection, 'structure_locked' only allows the editing of data (values), and 'view_only' will limit access to both structure (fields) and data (values)</td></tr><tr><td><strong>fields</strong></td><td><em>array</em></td><td>An array of objects containing the name and type of each field in the collection. <a href="collections.md#field-properties">See Field Properties table below</a></td></tr><tr><td><strong>values</strong></td><td><em>array</em></td><td>An array of all data rows in the collection. <a href="collections.md#value-properties">See Value Properties table below</a></td></tr><tr><td><strong>external_details</strong></td><td><em>object</em></td><td>Only available on external collections. Contains properties related to the data source. <a href="collections.md#external-detail-properties">See External Detail Properties table below</a></td></tr></tbody></table>

{% hint style="info" %}
**Good to Know:** Image collections can only be set to the 'locked' or 'unlocked' states. Structural changes are never available to image collections. Similarly, external collections can only be set to the 'structure\_locked' or 'unlocked' states as external collections will always receive their values from an external endpoint.
{% endhint %}

#### Field Properties

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the field when it was created. Note: Use a <em>URL friendly string</em>.</td></tr><tr><td><strong>type</strong></td><td><em>string</em></td><td>The type of date within the field. <a href="collections.md#collection-field-types">See Collection Field Types table</a></td></tr><tr><td><strong>inner_collection_fields</strong></td><td><em>array</em></td><td>Only available if the field type is "inner_collection". An array of field properties within the inner collection. <em>Note: inner collections can only be nested one level deep</em></td></tr></tbody></table>

#### Value Properties

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>int</em></td><td>The unique number of the row within the collection. This is used if you need to update the row later.</td></tr><tr><td><strong>data</strong></td><td><em>object</em></td><td>An object containing key-value pairs of the column name along with the data for that row.</td></tr></tbody></table>

#### External Detail Properties

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>enabled</strong></td><td><em>bool</em></td><td>Whether this collection is enabled as external.</td></tr><tr><td><strong>external_endpoint</strong></td><td><em>string</em></td><td>An absolute URI containing the data within the collection. Note: external collections will not have a 'values' property containing actual data. These values are only available from the external endpoint.</td></tr></tbody></table>

#### Collection Field Types

<table><thead><tr><th width="270">Property(Editor UI)</th><th>Type(API)</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>Plain Text</strong></td><td><em>plain_text</em></td><td>Simple string of content you want to be displayed on the website in some form. This text cannot contain escaped HTML. The maximum length of this field is 2000 characters.</td></tr><tr><td><strong>Rich Text</strong></td><td><em>rich_text</em></td><td>Simple string of content you want to be displayed on the website in some form. This text can contain escaped HTML. The maximum length of this field is 2000 characters.</td></tr><tr><td><strong>Image</strong></td><td><em>image</em></td><td>Absolute URL pointing to a publicly available image resource. Externally hosted images will not benefit from automatic image resizing or optimization. To take advantage of these features, first <a href="collections.md#upload-resource-1">upload</a> the image and then provide the URL of the returned image.</td></tr><tr><td><strong>Link</strong></td><td><em>link</em></td><td>String in URL format. A value with a type of link is automatically available for various widgets</td></tr><tr><td><strong>Number</strong></td><td><em>number</em></td><td>Whole or decimal number represented with or without commas for thousands and using periods for decimals.</td></tr><tr><td><strong>Date &#x26; Time</strong></td><td><em>date_time</em></td><td>A compatible ISO date format. (See value examples below)</td></tr><tr><td><strong>Business Hours</strong></td><td><em>business_hours</em></td><td>Array of objects describing the hours of operation for a business.</td></tr><tr><td><strong>Location</strong></td><td><em>location</em></td><td>Object describing a business location.</td></tr><tr><td><strong>Video</strong></td><td><em>video</em></td><td>Absolute URL pointing to a publicly available Youtube, Vimeo, or DailyMotion video.</td></tr><tr><td><strong>Email</strong></td><td><em>email</em></td><td>A valid email address.</td></tr><tr><td><strong>Phone</strong></td><td><em>phone</em></td><td>A valid phone number.</td></tr><tr><td><strong>Social Accounts</strong></td><td><em>social_accounts</em></td><td>An object containing key/value combinations of social network names and a specific account identifier.</td></tr><tr><td><strong>Inner Collection</strong></td><td><em>collection</em></td><td>An array of objects containing a name and type property. Inner collections can include all field types except collection and collection_ref.</td></tr><tr><td><strong>Collection Ref</strong></td><td><em>collection_ref</em></td><td>A string referencing another collection connected to the same site.</td></tr></tbody></table>

### Example data type values

When providing data to a collection via an external endpoint, values must be provided in a format appropriate for the field type.

{% tabs %}
{% tab title="Plain Text Value" %}
```json
{
  "logo": "https://example.org/path/to/logo.png"
}
```
{% endtab %}

{% tab title="Rich Text Value" %}
```json
{
	"about_us": "Lorum &lt;strong&gt;ipsum&lt;/strong&gt; dolor &lt;em&gt;sit&lt;/em&gt; amet."
}
```
{% endtab %}

{% tab title="Image Value" %}
```json
{
  "logo": "https://example.org/path/to/logo.png"
}
```
{% endtab %}

{% tab title="Link Value" %}
```json
{
  "profile": "https://www.crunchbase.com/organization/duda"
}
```
{% endtab %}

{% tab title="Number Value" %}
```json
{
  "price": 19.99
}
```
{% endtab %}

{% tab title="Date & Time Value" %}
```json
{
  "created_on": "2000-10-31T01:30:00",
  "updated_on": "2000-10-31T01:30",
  "last_viewed": "2000-10-30",
  "last_vote": "-0100-07-12T15:03:44"
}
```
{% endtab %}

{% tab title="Business Hour Value" %}
```json
[
  {
    "days":[
      "MON",
      "TUE",
      "WED",
      "THU",
      "FRI"
    ],
    "open":"9:00",
    "close":"18:00"
  }, {
    "days": [
      "SAT"
    ],
    "open": "12:00",
    "close": "16:00"
  }
]
```
{% endtab %}

{% tab title="Location Value" %}
```json
{
  "address_geolocation":"123 15th St, Columbus, IN, United States",
  "geo":{
    "longitude":"-85.8938199",
    "latitude":"39.2157605"
  },
  "address":{
    "streetAddress":"123 15th St, Columbus, IN, United States"
  }
}
```
{% endtab %}

{% tab title="Video Value" %}
```json
{
  "promo_vid": "https://vimeo.com/362415796"
}
```
{% endtab %}

{% tab title="Email Value" %}
```json
{
  email: "hello@duda.co"
}
```
{% endtab %}

{% tab title="Phone Value" %}
```json
{
  phone: "+1 (123) 456-7890"
}
```
{% endtab %}

{% tab title="Social Accounts Value" %}
```json
"social_accounts": {
  "email":"my@gmail.com",
  "whatsapp":"9543543543",
  "facebook":"duda",
  "twitter":"duda",
  "instagram":"duda",
  "youtube":"UCPMwzOc1Su-s2z-J1xiU9ig",
  "linkedin":"duda",
  "yelp":"orens-hummus-shop-palo-alto",
  "pinterest":"michelleobama",
  "google_my_business":"Cafe+Nona/@32.0718045,34.7809687,15z/data=!4m19!1m13!4m12!1m4!2m2!1d34.8127232!2d32.0503808!4e1!1m6!1m2!1s0x151d4b8468d5803f:0xc4b3f0a57332f82f!2z16DXldeg15Qg16rXnCDXkNeR15nXkeKArQ!2m2!1d34.7815956!2d32.0769206!3m4!1s0x151d4b8468d5803f:0xc4b3f0a57332f82f!8m2!3d32.0769206!4d34.7815956",
  "waze":"34.784267763974256, 32.07510593016749",
  "vimeo":"dudamobile",
  "snapchat":"michelleobama",
  "reddit":"duda",
  "tripadvisor":"Restaurant_Review-g32849-d2394400-Reviews-Oren_s_Hummus_Shop-Palo_Alto_California.html",
  "foursquare":"v/anita-la-mamma-del-gelato-%D7%90%D7%A0%D7%99%D7%98%D7%94/4b488bfff964a520184f26e3",
  "rss":"https://www.duda.co/blog/feed/",
}
```
{% endtab %}

{% tab title="Inner Collection Value" %}
```json
"all_photos": [
  {
    "alt": "Lorum ipsum",
    "url": "https://example.org/path/to/image.png
  },{
    "alt": "dolor sit amet",
    "url": "https://example.org/path/to/another.png"
  }
]
```
{% endtab %}

{% tab title="Collection Ref Value" %}
```json
{
  "related": "Collection Name"
}
```
{% endtab %}
{% endtabs %}

### Example field creation payloads

When creating new fields in a collection, either through the create collection or create field endpoints, you must always supply a name and a valid data type. (See the _Collection Field Types_ table above.) Inner collection and collection reference field types must also provide an array of their nested fields.

{% tabs %}
{% tab title="Collection Reference" %}
```json
{
    "name": "my-source-collection",
    "type": "collection_ref",
    "inner_collection_fields": [
        {
            "name":"title",
            "type":"text"
        },{
            "name":"description",
            "type":"text"
        }
    ]
}
```
{% endtab %}

{% tab title="Inner Collection" %}
```json
{
  "name": "my-inner-collection",
  "type": "collection",
  "inner_collection_fields": [
    {
      "name":"title",
      "type":"text"
    },{
      "name":"description",
      "type":"text"
    }
  ]
}
```
{% endtab %}

{% tab title="Other Types" %}
```json
{
    "name": "my-field",
    "type": "<TYPE>"
}
```
{% endtab %}
{% endtabs %}

### Data formatters

Some data types allow you to input a formatter. Applying a formatter allows you to visually output the value in a specified pattern, while keeping the original available for functionality such as filtering or sorting. Formatters can be specified in the _Collection Fields_ screen of the collection UI.

### Date & Time Formatter

The following ISO formats can be supplied as date & time values from an external endpoint.\


{% tabs %}
{% tab title="Compatible ISO formats for data" %}
```json
"-0100-07-12T15:03:44",
"2000-10-31T01:30:00",
"2000-10-31T01:30",
"2000-10-30",
"01:30"
```
{% endtab %}
{% endtabs %}

The following characters are available to format valid date & time values.

<table><thead><tr><th width="270">Formatter</th><th>Meaning</th><th width="255">Output</th></tr></thead><tbody><tr><td><strong>G</strong></td><td>era</td><td>AD; Anno Domini; A</td></tr><tr><td><strong>u</strong></td><td>year</td><td>2004; 04</td></tr><tr><td><strong>y</strong></td><td>year-of-era</td><td>2004; 04</td></tr><tr><td><strong>D</strong></td><td>day-of-</td><td>189</td></tr><tr><td><strong>M/L</strong></td><td>month-of-year</td><td>7; 07; Jul; July; J</td></tr><tr><td><strong>d</strong></td><td>day-of-month</td><td>10</td></tr><tr><td><strong>Q/q</strong></td><td>quarter-of-year</td><td>3; 03; Q3; 3rd quarter</td></tr><tr><td><strong>Y</strong></td><td>week-based-year</td><td>1996; 96</td></tr><tr><td><strong>W</strong></td><td>week-of-month</td><td>4</td></tr><tr><td><strong>E</strong></td><td>am-pm-of-day</td><td>Tue; Tuesday; T</td></tr><tr><td><strong>e/c</strong></td><td>localized day-of-week</td><td>2; 02; Tue; Tuesday; T</td></tr><tr><td><strong>F</strong></td><td>week-of-month</td><td>3</td></tr><tr><td><strong>a</strong></td><td>am-pm-of-day</td><td>PM</td></tr><tr><td><strong>h</strong></td><td>clock-hour-of-am-pm(1-12)</td><td>12</td></tr><tr><td><strong>K</strong></td><td>hour-of-am-pm(0-11)</td><td>0</td></tr><tr><td><strong>k</strong></td><td>clock-hour-of-am-pm(1-24)</td><td>0</td></tr><tr><td><strong>H</strong></td><td>hour-of-day(0-23)</td><td>0</td></tr><tr><td><strong>m</strong></td><td>minute-of-hour</td><td>30</td></tr><tr><td><strong>s</strong></td><td>second-of-minute</td><td>55</td></tr><tr><td><strong>S</strong></td><td>fraction-of-second</td><td>978</td></tr><tr><td><strong>A</strong></td><td>milli-of-day</td><td>1234</td></tr><tr><td><strong>n</strong></td><td>nano-of-second</td><td>987654321</td></tr><tr><td><strong>N</strong></td><td>nano-of-day</td><td>1234000000</td></tr><tr><td><strong>V</strong></td><td>time-zone ID</td><td>America/Los_Angeles; Z; -08:30</td></tr><tr><td><strong>z</strong></td><td>time-zone name</td><td>Pacific Standard Time; PST</td></tr><tr><td><strong>O</strong></td><td>localized zone-offset</td><td>GMT+8; GMT+08:00; UTC-08:00;</td></tr><tr><td><strong>X</strong></td><td>zone-offset 'Z' for zero</td><td>Z; -08; -0830; -08:30; -083015; -08:30:15;</td></tr><tr><td><strong>x</strong></td><td>zone-offset</td><td>+0000; -08; -0830; -08:30; -083015; -08:30:15;</td></tr><tr><td><strong>Z</strong></td><td>zone-offset</td><td>+0000; -0800; -08:00;</td></tr></tbody></table>

### Examples

| Data                | Formatter          | Output                  |
| ------------------- | ------------------ | ----------------------- |
| 2000-10-31T01:30:00 | YYYY-MM-dd         | 2000-10-31              |
| 2000-10-31T01:30:00 | MMM, dd, YY        | Oct, 03, 21             |
| 2000-10-31T01:30:00 | HH:mm:SS           | 01:30:00                |
| 2000-10-31T01:30:00 | E, MMMM dd - HH:mm | Tue, October 31 - 01:30 |

## List Collections

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Collections" path="/sites/multiscreen/{site_name}/collection" %}
{% swagger-description %}
Get all collections that exist on this website.

The `fields` object contains the structure of the collection. The `values` object contains the data that is stored in the collection\

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
[
  {
    "name": "events",
    "customer_lock": "unlocked",
    "fields": [
      {
        "name": "date",
        "type": "text"
      },
      {
        "name": "entry-price",
        "type": "text"
      },
      {
        "name": "event-image",
        "type": "image"
      },
      {
        "name": "location",
        "type": "text"
      }
    ],
    "values": [
      {
        "id": "144",
        "data": {
          "date": "01/01/2019",
          "entry-price": "$40",
          "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
          "location": "San Francisco"
        }
      },
      {
        "id": "145",
        "data": {
          "date": "01/10/2019",
          "entry-price": "$45",
          "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
          "location": "Boston"
        }
      },
      {
        "id": "146",
        "data": {
          "date": "01/03/2019",
          "entry-price": "$40",
          "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
          "location": "San Jose"
        }
      },
      {
        "id": "147",
        "data": {
          "date": "01/13/2019",
          "entry-price": "$45",
          "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
          "location": "New York"
        }
      }
    ]
  },
  {
    "name": "Multi-use Image Slider",
    "lock_state": "structure_locked",
    "fields": [
      {
        "name": "description",
        "type": "text"
      },
      {
        "name": "image",
        "type": "image"
      },
      {
        "name": "title",
        "type": "text"
      }
    ],
    "values": [
      {
        "id": "142",
        "data": {
          "image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
          "description": "<p class=\"rteBlock\">Description about image.</p>",
          "title": "Woman Face"
        }
      },
      {
        "id": "143",
        "data": {
          "image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/girls-jumping-fashion-cloths.jpg",
          "description": "<p class=\"rteBlock\">Jumping girls</p>",
          "title": "Jumping Girls"
        }
      }
    ]
  }
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Collection

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Collection" path="/sites/multiscreen/{site_name}/collection/{collection_name}" %}
{% swagger-description %}
Get the fields and data of an existing collection

The `fields` object contains the structure of the collection. The `values` object contains the data that is stored in the collection
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the current collection
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "name":"events",
  "customer_lock": "unlocked",
  "fields":[
    {
      "name":"date",
      "type":"text"
    },
    {
      "name":"entry-price",
      "type":"text"
    },
    {
      "name":"event-image",
      "type":"image"
    },
    {
      "name":"location",
      "type":"text"
    }
  ],
  "values":[
    {
      "id":"144",
      "page_item_url": '1',
      "data":{
        "date":"01/01/2019",
        "entry-price":"$40",
        "event-image":"https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
        "location":"San Francisco"
      }
    },
    {
      "id":"145",
      "page_item_url": '2',
      "data":{
        "date":"01/10/2019",
        "entry-price":"$45",
        "event-image":"https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
        "location":"Boston"
      }
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Collection

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Create Collection" path="/sites/multiscreen/{site_name}/collection" %}
{% swagger-description %}


Create a new collection within a site
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
The name of the collection (must not start with $)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customer_lock" type="string" %}
The lock state of the collection. Must be one of 

`unlocked`

, 

`structure_locked`

 or 

`locked`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fields" type="array of objects" %}
You must define at least one field when creating an internal collection (when 

`external_details.enabled`

 is set to false).
{% endswagger-parameter %}

{% swagger-parameter in="body" name="external_details" type="object" %}

{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up: External endpoint content type**

The URL specified in the `external_endpoint` property of the external details object, must return a `Content-Type` header set to `application/json` other content types will cause an error when creating the collection.
{% endhint %}

{% hint style="warning" %}
**Heads up:** A single external collection endpoint cannot exceed 20MB of data.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_lock": "unlocked",
  "external_details": {
    "enabled": true
  }
}
'
```
{% endtab %}
{% endtabs %}

## Update Collection

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="put" summary="Update Collection" path="/sites/multiscreen/{site_name}/collection/{current_collection_name}" %}
{% swagger-description %}
Update an existing collection
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="current_collection_name" type="string" required="true" %}
Name of the current collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
The new name of the collection (must not start with $)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customer_lock" type="string" %}
The lock state of the collection. Must be one of 

`unlocked`

, 

`structure_locked`

 or 

`locked`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="external_details" type="object" %}

{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Only the collection settings can be updated with this endpoint. Updating a field of a collection can be done with the Fields API documented below
{% endhint %}

{% hint style="warning" %}
**Heads up: External endpoint content type**

The URL specified in the `external_endpoint` property of the external details object, must return a `Content-Type` header set to `application/json` other content types will cause an error when creating the collection.
{% endhint %}

{% hint style="warning" %}
**Heads up:** When changing external details, you should include all existing properties. Any missing properties in your request, will be deleted from the collection configuration.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/current_collection_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_lock": "unlocked",
  "external_details": {
    "enabled": true
  }
}
'
```
{% endtab %}
{% endtabs %}

## Delete Collection

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="delete" summary="Delete Collection" path="/sites/multiscreen/{site_name}/collection/{collection_name}" %}
{% swagger-description %}
Delete an existing collection
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="" required="true" %}
Name of the collection
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Clear Cache

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Clear Cache" path="sites/multiscreen/{site_name}/collection/{collection_name}/revalidate" %}
{% swagger-description %}
Force Duda to refresh the data from an external URL for a given collection.

Duda caches the data for an external collection to help with performance. By default, we cache a collection up to 2hrs. If you want to update the data in the site immediately, you can use the revalidate API.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the current collection
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Updating data on the live site is performed asynchronously on Duda's side and therefore **may take up to 3 minutes to take effect**
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/revalidate \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Clear Cache by External ID

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Clear Cache by External ID" path="/sites/multiscreen/collections/revalidate/{external_id}" %}
{% swagger-description %}
Revalidate all collections in all sites under the same account that use the provided external id
{% endswagger-description %}

{% swagger-parameter in="path" name="external_id" type="string" required="true" %}
The external ID for the collections
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up: Rate limited endpoint**

This endpoint may cause resource intensive operations and may only be called a maximum of once every 15 minutes.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/collections/revalidate/external_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
