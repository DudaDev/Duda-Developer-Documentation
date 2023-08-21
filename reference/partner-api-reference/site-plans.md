# Site Plans

## List Site Plans

{% swagger method="get" path="/sites/multiscreen/plans" baseUrl="https://api.duda.co/api" summary="List Site Plans" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get a list of plans that the sites can be changed to within the account.
{% endswagger-description %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "planId": 201,
    "planName": "YELL_ONE_PAGER"
  },
  {
    "planId": 202,
    "planName": "YELL_PREMIUM_OLD"
  },
  {
    "planId": 203,
    "planName": "YELL_PREMIUM"
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
     --url https://api.duda.co/api/sites/multiscreen/plans \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Site Plan

{% swagger method="get" path="/sites/multiscreen/{site_name}/plan" baseUrl="https://api.duda.co/api" summary="Get Site Plan" expanded="false" %}
{% swagger-description %}
Get the current plan assigned to a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "planName": "INFO",
  "planId": 101
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/plan \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Site Plan

{% swagger method="post" path="/sites/multiscreen/{site_name}/plan/{plan_id}" baseUrl="https://api.duda.co/api" summary="Update Site Plan" expanded="false" %}
{% swagger-description %}
Set or change the Plan of a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique site name, originally received when creating the site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="plan_id" type="int32" %}
The plan ID number of the plan you want to apply to this site
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "planName": "INFO",
  "planId": 101
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
     --url https://api.duda.co/api/sites/multiscreen/site_name/plan/plan_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
