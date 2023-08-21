# Collection Rows

## Create Rows

{% swagger method="post" path="/sites/multiscreen/{site_name}/collection/{collection_name}/row" baseUrl="https://api.duda.co/api" summary="Create Rows" expanded="false" fullWidth="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/row \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
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

{% swagger method="put" path="/sites/multiscreen/{site_name}/collection/{collection_name}/row" baseUrl="https://api.duda.co/api" summary="Update Rows" expanded="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/row \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
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

{% swagger method="delete" path="/sites/multiscreen/{site_name}/collection/{collection_name}/row" baseUrl="https://api.duda.co/api" summary="Delete Rows" expanded="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/field/field_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
[
  {
    "id": "233"
  },
  {
    "id": "234"
  }
]
'
```
{% endtab %}
{% endtabs %}
