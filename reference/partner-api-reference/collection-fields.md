# Collection Fields

## Create Fields

{% swagger method="post" path="/sites/multiscreen/{site_name}/collection/{collection_name}/field" baseUrl="https://api.duda.co/api" summary="Create Fields" expanded="false" fullWidth="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/field \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
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

{% swagger method="put" path="/sites/multiscreen/{site_name}/collection/{collection_name}/field/{field_name}" baseUrl="https://api.duda.co/api" summary="Update Fields" expanded="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/field/field_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "name": "first_name"
}
'
```
{% endtab %}
{% endtabs %}

## Delete Fields

{% swagger method="delete" path="/sites/multiscreen/{site_name}/collection/{collection_name}/field/{field_name}" baseUrl="https://api.duda.co/api" summary="Delete Fields" expanded="false" %}
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/collection/collection_name/field/field_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
