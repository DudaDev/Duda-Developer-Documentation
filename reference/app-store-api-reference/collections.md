# Collections

## List Collections

{% swagger method="get" baseUrl=" https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="List Collections" path="/integrationhub/application/site/{site_name}/collections" %}
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collections \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Get Collection

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="get" summary="Get Collection" path="/integrationhub/application/site/{site_name}/collection/{collection_name}" %}
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
     --url  https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name \
     --header 'Accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Collection

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Create Collection" path="/integrationhub/application/site/{site_name}/collection" %}
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
     --url  https://api-sandbox.duda.co/api/sites/multiscreen/site_name/collection \
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

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="put" summary="Update Collection" path="/integrationhub/application/site/{site_name}/collection/{current_collection_name}" %}
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
     --url https://api-sandbox.duda.co/api/sites/multiscreen/site_name/collection/current_collection_name \
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

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="delete" summary="Delete Collection" path="/integrationhub/application/site/{site_name}/collection/{collection_name}" %}
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
     --url  https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name \
     --header 'Accept: application/json'
```
{% endtab %}
{% endtabs %}

## Clear Cache

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Clear Cache" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/revalidate" %}
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/revalidate \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Clear Cache by External ID

{% swagger baseUrl=" https://api-sandbox.duda.co/api" expanded="false" method="post" summary="Clear Cache by External ID" path="/integrationhub/application/site/collections/revalidate/{external_id}" %}
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/collections/revalidate/external_id \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}

## Create Rows

{% swagger method="post" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/row" baseUrl=" https://api-sandbox.duda.co/api" summary="Create Rows" expanded="false" fullWidth="false" %}
{% swagger-description %}
Add new row(s) of data into an existing collection. This accepts multiple row values if you'd like to insert more than one.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to add the field
{% endswagger-parameter %}

{% swagger-parameter in="body" type="json" name="-" required="false" %}
object of row(s) and fields to set
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "id": "233"
  },
  {
    "id": "234"
  }
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** The request JSON must adhere to the structure of the collection. More than one row can be added at a time.&#x20;
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/row \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '
[
  {
    "data": {
      "date": "01/03/2019",
      "entry-price": "$40",
      "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
      "location": "San Jose"
    }
  },
  {
    "data": {
      "date": "01/13/2019",
      "entry-price": "$45",
      "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
      "location": "New York"
    }
  }
]
'
```
{% endtab %}
{% endtabs %}

## Update Rows

{% swagger method="put" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/row" baseUrl=" https://api-sandbox.duda.co/api" summary="Update Rows" expanded="false" %}
{% swagger-description %}
Update existing collection rows.

The request JSON must provide the `id` of the row. You must send the full data of the object back to Duda (of all existing fields), as Duda will simply overwrite all values in the column with the new value added.&#x20;
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to update the field
{% endswagger-parameter %}

{% swagger-parameter in="body" name="-" type="json" required="false" %}
object of row(s) and fields to update
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** For internal collections, you are able to update the dynamic page URL by passing a `page_item_url` property. For image collections, the `page_item_url` property will be ignored.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/row \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '
[
  {
    "id": "144",
    "data": {
      "date": "01/10/2019",
      "entry-price": "$50",
      "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
      "location": "San Francisco"
    }
  },
  {
    "id": "145",
    "data": {
      "date": "01/12/2019",
      "entry-price": "$55",
      "event-image": "https://irt-cdn.multiscreensite.com/md/dmip/dms3rep/multi/young-woman-portrait-blue-eyes.jpg",
      "location": "Boston"
    }
  }
]
'
```
{% endtab %}
{% endtabs %}

## Delete Rows

{% swagger method="delete" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/row" baseUrl=" https://api-sandbox.duda.co/api" summary="Delete Rows" expanded="false" %}
{% swagger-description %}
Delete existing rows of data that exist within the collection.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to delete the field
{% endswagger-parameter %}

{% swagger-parameter in="body" type="json" name="-" %}
Array of row ids to delete
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/row \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '["146","324"]'
```
{% endtab %}
{% endtabs %}

## Create Fields

{% swagger method="post" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/field" baseUrl=" https://api-sandbox.duda.co/api" summary="Create Fields" expanded="false" fullWidth="false" %}
{% swagger-description %}
Add a new field(s) to an existing collection.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to add the field
{% endswagger-parameter %}

{% swagger-parameter in="body" type="string" name="name" required="true" %}
The name of the collection field. (must not start with $)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
The data type for this field
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
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/field \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '
[
  {
    "name": "name",
    "type": "plain_text"
  },
  {
    "name": "age",
    "type": "number"
  }
]
'
```
{% endtab %}
{% endtabs %}

## Update Fields

{% swagger method="put" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/field/{field_name}" baseUrl=" https://api-sandbox.duda.co/api" summary="Update Fields" expanded="false" %}
{% swagger-description %}
Update existing field of a collection
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to update the field
{% endswagger-parameter %}

{% swagger-parameter in="path" name="field_name" type="string" required="true" %}
Name of the field in the collection. (must not start with $)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
The new field name (must not start with $)
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Only updating the name of a field is permitted. If you need to update the type, then delete the field and re-add it with the correct type.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PUT \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/field/field_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --data '
{
  "name": "new-field-name"
}
'
```
{% endtab %}
{% endtabs %}

## Delete Fields

{% swagger method="delete" path="/integrationhub/application/site/{site_name}/collection/{collection_name}/field/{field_name}" baseUrl="https://api.duda.co/api" summary="Delete Fields" expanded="false" %}
{% swagger-description %}
Delete an existing field of a collection
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collection_name" type="string" required="true" %}
Name of the collection to delete the field
{% endswagger-parameter %}

{% swagger-parameter in="path" name="field_name" type="string" required="true" %}
Name of the field in the collection
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Only updating the name of a field is permitted. If you need to update the type, then delete the field and re-add it with the correct type.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/collection/collection_name/field/field_name \
     --header 'accept: application/json' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
