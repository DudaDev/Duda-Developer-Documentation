# Stats Email

## Get Client Settings

{% swagger method="get" path="/accounts/{account_name}/sites/{site_name}/stats-email" baseUrl="https://api.duda.co/api" summary="Get Client Settings" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get the status of stats emails for a customer on a given site.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website

\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "frequency": "WEEKLY"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** If a recurring email is already enabled, the API returns a JSON object with the frequency. If no recurring email is enabled, then an error will be returned.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/stats-email \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Subscription

{% swagger method="post" path="/sites/multiscreen/backups/{site_name}/create" baseUrl="https://api.duda.co/api" summary="Create Subscription" expanded="false" %}
{% swagger-description %}
Subscribe a customer (or staff member) to statistics emails for a specific site.

\




\


These emails will be automatically delivered by the Duda platform to your users. Monthly emails are sent on the 3rd of each month and weekly emails are sent every Tuesday. You can also perform the same API call to overwrite the existing frequency of customers already signed up.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="body" name="frequency" type="string" required="true" %}
WEEKLY, MONTHLY or YEARLY
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}
```json
{
  "name": "QA-Complete"
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
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/stats-email \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "frequency": "WEEKLY"
}
'
```
{% endtab %}
{% endtabs %}

## Unsubscribe

{% swagger method="delete" path="/accounts/{account_name}/sites/{site_name}/stats-email" baseUrl="https://api.duda.co/api" summary="Restore Backup" expanded="false" %}
{% swagger-description %}
Unsubscribe a customer (or staff member) to statistics emails for a specific site.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

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
curl --request DELETE \
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/stats-email \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
