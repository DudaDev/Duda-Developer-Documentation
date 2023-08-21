# Collections JS API

The Collections API returns filtered, sorted, searched and paginated data from your [collections](../reference/partner-api-reference/collections.md) using Javascript. This article will walk you through how to use the Collections API and all of its options.

### Usage

In the interest of page speed, the Collections API is not included in the page until it is initialized using Duda's JavaScript API.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
dmAPI.loadCollectionsAPI().then(api => {
	// do something with API
})
```
{% endtab %}
{% endtabs %}

Once the Collections API is initialized, it can be used to fetch, filter, sort, search and paginate collection data via chaining additional methods to the `data` method. At a minimum, you must pass the collection name to the `data` method, followed by calling the `get` method. This configuration will return a single page of results from the specified collection.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
api.data("collectionName").get().then(data => {...})
```
{% endtab %}
{% endtabs %}

Each call to the `get` method makes an asynchronous network request. This method returns a promise, which will be resolved with data matching the query.

### Options

The Collection API supports optional method chaining to add specific filtering, sorting, and pagination when querying data. Below is an example using all optional methods.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
dmAPI.loadCollectionsAPI().then(api => {
	api.data("collectionName")
		.where("<field>", "<operator>", "<value>")
		.orderBy("<field>","<direction>")
    .select('property1', 'property2', ...)
		.pageSize(20)
		.pageNumber(2)
		.get()
		.then(json => console.log(json))
})
```
{% endtab %}
{% endtabs %}

### Paginating Items

Pagination is handled with two methods:

<table><thead><tr><th width="209">Method Name</th><th width="88">Type</th><th width="111">Required</th><th>Notes</th></tr></thead><tbody><tr><td><strong>pageSize</strong></td><td><em>int</em></td><td>No</td><td>Defaults to 50 items per page.<br><br>Max size is 100 items per page.</td></tr><tr><td><strong>pageNumber</strong></td><td><em>int</em></td><td>No</td><td>Defaults to 0.</td></tr></tbody></table>

### Filtering Items

Use the `.where()` method to filter the results using a provided comparison. Where takes three arguments:

<table><thead><tr><th width="140">Argument</th><th width="232">Type</th><th width="101">Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>field</strong></td><td><em>string</em></td><td>Yes</td><td>The field in the collection.</td></tr><tr><td><strong>operator</strong></td><td><em>string</em></td><td>Yes</td><td>Available operators: EQ, IN, NE, NIN, GT, GTE, LT, LTE, BTWN.</td></tr><tr><td><strong>value</strong></td><td><em>string</em> | <em>array</em> | <em>number</em></td><td>Yes</td><td>A value to compare.</td></tr></tbody></table>

#### Filter Operators

The `.where()` method can utilize several different operators to filter fields based on their value. Certain operators can only be applied to fields of a specific data type.

<table><thead><tr><th width="197">Value</th><th width="181">Field Data Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>EQ</strong></td><td><em>string, number</em></td><td>Checks if the field is equal to the supplied value.</td></tr><tr><td><strong>IN</strong></td><td><em>string, number</em></td><td>Checks if the field contains a value within the supplied array.</td></tr><tr><td><strong>NE</strong></td><td><em>string, number</em></td><td>Checks if the field is <em>not</em> equal to the supplied value.</td></tr><tr><td><strong>NIN</strong></td><td><em>string, number</em></td><td>Checks if the field is <em>not</em> a value within the supplied array.</td></tr><tr><td><strong>GT</strong></td><td><em>number</em></td><td>Checks if the field is greater than the supplied value.</td></tr><tr><td><strong>GTE</strong></td><td><em>number</em></td><td>Checks if the field is greater than or equal to the supplied value.</td></tr><tr><td><strong>LT</strong></td><td><em>number</em></td><td>Checks if the field is less than the supplied value.</td></tr><tr><td><strong>LTE</strong></td><td><em>number</em></td><td>Checks if the field is less than or equal to the supplied value.</td></tr><tr><td><strong>BTWN</strong></td><td><em>number</em></td><td>Combination of LTE and GTE for convenience. Check if the field is equal or between two values. Expects a list of exactly two values.</td></tr></tbody></table>

### Sorting Items

Use the `.orderBy()` method to sort the query results. Order by takes two arguments:

<table><thead><tr><th>Argument</th><th width="123">Type</th><th width="108">Required</th><th>Notes</th></tr></thead><tbody><tr><td><strong>field</strong></td><td><em>string</em></td><td>Yes</td><td>The field in the collection.</td></tr><tr><td><strong>direction</strong></td><td><em>string</em></td><td>No</td><td>Possible values are “asc” and “desc”.<br>Defaults to “asc”.</td></tr></tbody></table>

### Searching collection

Use the `.search()` method to search a collection.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
dmAPI.loadCollectionsAPI().then(api => {
	api.data("collectionName")
    .search("<search_query>")
		.get()
		.then(json => console.log(json))
})
```
{% endtab %}
{% endtabs %}

* You can search for all `string` fields in a collection.
* Search is case insensitive.
* When searching in a collection, we check whether the search query is contained in any of the searchable fields in the collection.

### Returning Specific Item Properties

Use the `.select()` method to only return the specific properties you need for the site or widget to function. This can improve performance for collections with a large number of properties per item. Provide each property name as a separate argument to the function.
