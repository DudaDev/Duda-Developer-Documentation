# Reporting

## Site Created

{% swagger method="get" path="/sites/multiscreen/created" baseUrl="https://api.duda.co/api" summary="Site Created" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get a list of Sites created within a span of time.
{% endswagger-description %}

{% swagger-parameter in="query" name="from" type="string" %}
Start date. ex "2016-03-01"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" type="string" %}
End Date. ex "2016-03-31"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of strings" %}
```json
[
  "a75b4ddc",
  "d2f8eded"
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** If no parameters are specified, sites created within the last 7 days including today are returned.\
If just a `from` date is specified, sites created in the 7 day period including with the date provided are returned.\
If just a `to` date is specified, sites created during the 7 day period prior to and excluding the date provided are returned.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/created \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Site Published

{% swagger method="get" path="/sites/multiscreen/published" baseUrl="https://api.duda.co/api" summary="Site Published" expanded="false" %}
{% swagger-description %}
Get a list of recently published websites in your account.
{% endswagger-description %}

{% swagger-parameter in="query" name="lastDays" type="string" %}
The number of days in which you would like get sites that have been published
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of strings" %}
{% code overflow="wrap" %}
```json
[
  "a75b4ddc",
  "d2f8eded"
]
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** This API call returns all sites that have been published recently regardless if it is the first time a site was published.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/published \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Site Unpublished

{% swagger method="get" path="/sites/multiscreen/unpublished" baseUrl="https://api.duda.co/api" summary="Site Unpublished" expanded="false" %}
{% swagger-description %}
Get a list of recently unpublished websites in your account.
{% endswagger-description %}

{% swagger-parameter in="query" name="lastDays" type="string" %}
The number of days in which you would like to get sites that have been published
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of strings" %}
```json
[
  "a75b4ddc",
  "d2f8eded"
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
     --url https://api.duda.co/api/sites/multiscreen/unpublished \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Form Submissions

{% swagger method="get" path="/sites/multiscreen/get-forms/{site_name}" baseUrl="https://api.duda.co/api" summary="Form Submissions" %}
{% swagger-description %}
Get all the contact form submissions from a given site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from" type="string" %}
Start date. ex "2016-03-01"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" type="string" %}
End Date. ex "2016-03-31"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "form_title": "Contact Us",
    "message": {
      "Name": "test3",
      "Phone": "123-123-1234",
      "Dropdown": "Option 2",
      "Email": "test@test.com",
      "Message": "test message",
      "Radio button": "Option 2",
      "Date": "02/05/2014",
      "Check box": "Option 2"
    },
    "date": "2014-05-08T23:12:06"
  },
  {
    "form_title": "Contact Us",
    "message": {
      "Name": "test",
      "Phone": "abcc",
      "Email": "test@test.com",
      "Message": "123"
    },
    "date": "2014-05-08T22:34:50"
  }
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** If a `from` parameter is not specified, then all form submissions from a site will be returned
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/get-forms/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Activities

{% swagger method="get" path="/sites/multiscreen/{site_name}/activities" baseUrl="https://api.duda.co/api" summary="Activities" %}
{% swagger-description %}
Get activity history for a specific website over a certain amount of time.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="int32" %}
Items to be retrieved per page. Lower bound: 1, Upper bound: 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="int32" %}
The index of the first item to return. Must be greater or equal to zero.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from" type="date" %}
Start date in the format of “yyyy-MM-dd'T'HH:mm:ss” ex “2020-03-20T23:23:03” (UTC)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" type="date" %}
End date in the format of “yyyy-MM-dd'T'HH:mm:ss” ex. “2020-03-20T23:23:03” (UTC)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="activities" type="string" %}
Activities are the activity types you are looking to retrieve - this parameter can be included multiple times in your query e.g. “activities=site_created&activities=site_published”.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "site_name": "my-great-site",
  "results": [
    {
      "date": "2021-02-08T19:06:01",
      "activity": "site_published",
      "source": "ADMINISTRATOR",
      "account_name": "ADMINISTRATOR"
    },
    {
      "date": "2021-02-08T19:06:01",
      "activity": "site_backup_created",
      "source": "ADMINISTRATOR",
      "account_name": "ADMINISTRATOR"
    },
    {
      "date": "2021-02-08T19:05:57",
      "activity": "page_deleted",
      "source": "ADMINISTRATOR",
      "account_name": "ADMINISTRATOR"
    },
    {
      "date": "2021-02-08T19:05:47",
      "activity": "page_created",
      "source": "ADMINISTRATOR",
      "account_name": "ADMINISTRATOR"
    },
    {
      "date": "2021-02-08T19:04:40",
      "activity": "site_published",
      "source": "ADMINISTRATOR",
      "account_name": "ADMINISTRATOR"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

| Activity         | Activity Name         |
| ---------------- | --------------------- |
| Site created     | site\_created         |
| Site published   | site\_published       |
| Backup created   | site\_backup\_created |
| Page created     | page\_created         |
| Page deleted     | page\_deleted         |
| Domain assigned  | site\_domain\_changed |
| Unpublished      | site\_unpublished     |
| Site restored    | site\_restored        |
| Site reset       | site\_reset           |
| Site transferred | site\_transferred     |

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/site_name/activities \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Analytics

{% swagger method="get" path="/analytics/site/{site_name}" baseUrl="https://api.duda.co/api" summary="Analytics" %}
{% swagger-description %}
Get analytics history for a specific website over a certain amount of time.

If neither the `from` parameter nor the `to` parameter is provided, the queried period will be the past 30 days.

If only the `from` parameter is provided, the queried period will be the `from` date plus 30 days.

If only the `to` parameter is provided, the queried period will be from 30 days prior to the `to` date until the `to` date.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from" type="date" %}
Start date. ex "2016-03-01". Defaults to 30 days prior from the 

`to`

 date
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" type="date" %}
End Date. ex "2016-03-31". Defaults to current day
{% endswagger-parameter %}

{% swagger-parameter in="query" name="dimension" type="string" %}
The type of dimension to query the data by. "system" or "geo"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="result" type="string" %}
Type of metrics to results with. "traffic" or "activities"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="dateGranularity" type="string" %}
"DAYS", "WEEKS", "MONTHS", or "YEARS"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Traffic (Not Dimensioned)" %}
```json
{
  "VISITORS": 50,
  "VISITS": 100,
  "PAGE_VIEWS": 150
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="Activities (Not Dimensioned)" %}
```json
{
  "CLICK_TO_EMAILS": 2,
  "FORM_SUBMITS": 5,
  "CLICK_TO_MAPS": 15,
  "CLICK_TO_CALLS": 20
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="Traffic (Dimensioned By Geo)" %}
```json
[
  {
    "data": {
      "VISITORS": 50,
      "PAGE_VIEWS": 150,
      "VISITS": 100
    },
    "dimension": {
      "country": "US",
      "region": "CA"
    }
  },
  {
    "data": {
      "VISITORS": 50,
      "PAGE_VIEWS": 150,
      "VISITS": 100
    },
    "dimension": {
      "country": "US",
      "region": "FL"
    }
  },
  {
    "data": {
      "VISITORS": 50,
      "PAGE_VIEWS": 150,
      "VISITS": 100
    },
    "dimension": {
      "country": "Canada",
      "region": "Ontario"
    }
  }
]
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="Traffic (Dimensioned By System)" %}
```json
[
  {
    "dimension": {
      "browser": "Chrome 10",
      "os": "Windows"
    },
    "data": {
      "VISITORS": 374,
      "VISITS": 391,
      "PAGE_VIEWS": 895
    }
  },
  {
    "dimension": {
      "browser": "Firefox Mobile",
      "os": "Android"
    },
    "data": {
      "VISITORS": 29,
      "VISITS": 32,
      "PAGE_VIEWS": 60
    }
  }
]
```
{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** The `?result=activities` cannot be combined with the 'dimension' query string. This will return an error.
{% endhint %}

**If the result parameter is "traffic":**

If a dimension set is provided, an array containing the following JSON elements for each row of the result set.

If no dimension set is provided, a JSON structure containing the following elements.

| Parameter   | Type           | Description                                                                                                                                                                             |
| ----------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dimension   | JSON structure | A single dimension pertaining to the queried dimension type (if a dimension type was sent). Ex: The "geo" dimension type may return "dimension":{"Country":"Canada","Region":"Ontario"} |
| VISITS      | integer        | For the queried period and for the specified dimension, the number of visits to the site.                                                                                               |
| VISITORS    | integer        | For the queried period and for the specified dimension, the number of unique visitors to the site.                                                                                      |
| PAGE\_VIEWS | integer        | For the queried period and for the specified dimension, the number of page views to the site.                                                                                           |

**If the result parameter is "activities":**

If a dimension set is provided, an array containing the following JSON elements for each row of the result set.

If no dimension set is provided, a JSON structure containing the following elements.

| Parameter         | Type           | Description                                                                                                                                                                             |
| ----------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dimension         | JSON Structure | A single dimension pertaining to the queried dimension type (if a dimension type was sent). Ex: The "geo" dimension type may return "dimension":{"Country":"Canada","Region":"Ontario"} |
| CLICK\_TO\_CALLS  | integer        | For the queried period and for the specified dimension, the number of click-to-call actions on the site.                                                                                |
| CLICK\_TO\_MAPS   | integer        | For the queried period and for the specified dimension, the number of click-to-map actions on the site.                                                                                 |
| CLICK\_TO\_EMAILS | integer        | For the queried period and for the specified dimension, the number of click-to-email actions on the site.                                                                               |
| FORM\_SUBMITS     | integer        | For the queried period and for the specified dimension, the number of form submission actions on the site.                                                                              |

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/analytics/site/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
