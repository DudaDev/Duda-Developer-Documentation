# Accounts

## Account Object

{% tabs %}
{% tab title="JSON" %}
```json
{
    "account_name": "uniqueAcctReference",
    "first_name": "Joann",
    "last_name": "Smith",
    "lang": "en",
    "email": "example@domain.com",
  	"company_name": "Joann's Agency",
    "account_type": "CUSTOMER"
}
```
{% endtab %}
{% endtabs %}

| Field             | Type     | Description                                                                                                                             |
| ----------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **account\_name** | _string_ | Usually the email or unique identifer of the user you want to add. Is not required to be a email.                                       |
| **first\_name**   | _string_ | First name off the account holder. This is only used if Duda sends white labeled emails to the customer or the user writes a blog post. |
| **last\_name**    | _string_ | Last name of the account holder. This is used if Duda sends white labeled emails to the customer or the user writes a blog post.        |
| **account\_type** | _string_ | Can be "CUSTOMER" or "STAFF" accounts. Most common is "CUSTOMER"                                                                        |
| **lang**          | _string_ | Sets what language the user will see the website builder interface in.                                                                  |
| **company\_name** | _string_ | Sets the company name for the user.                                                                                                     |

## Get Account

{% swagger method="get" path="/accounts/{account_name}" baseUrl="https://api.duda.co/api" summary="Get Account" expanded="false" fullWidth="false" %}
{% swagger-description %}
Returns the details of an existing Account.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "account_name": "johnl2@yahoo.com",
  "first_name": "John",
  "last_name": "Lewis",
  "lang": "en",
  "email": "johnl@yahoo.com",
  "accountData": {
    "company_name": "Lewis Co."
  },
  "account_type": "CUSTOMER"
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
     --url https://api.duda.co/api/accounts/account_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Account

{% swagger method="post" path="/accounts/create" baseUrl="https://api.duda.co/api" summary="Create Account" expanded="false" %}
{% swagger-description %}
Creates a new Account
{% endswagger-description %}

{% swagger-parameter in="body" name="account_name" type="string" required="true" %}
Unique account reference. Can be an email address, but does not need to be.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="first_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="lang" type="string" %}


[Supported languages](https://developer.duda.co/reference/accounts-create-account#languages)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="company_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="account_type" type="string" %}
"CUSTOMER" or "STAFF"
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Duda will not email your customer directly (assuming you provide a valid email) when the account is created or updated. We only send emails to your customers for form submissions, stats emails, resetting passwords, site comment notifications, and sending site invites (from dashboard UI only). All emails we send to customers are white-labeled fully and will not reference Duda.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/accounts/create \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "account_name": "john12@yahoo.com"
}
'
```
{% endtab %}
{% endtabs %}

## Update Account

{% swagger method="post" path="/accounts/update/{account_name}" baseUrl="https://api.duda.co/api" summary="Update Account" expanded="false" %}
{% swagger-description %}
Updates an existing Account
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-parameter in="body" name="first_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_name" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="lang" type="string" %}


[Supported languages](https://developer.duda.co/reference/accounts-create-account#languages)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="company_name" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** We currently do not support updating the account name or type after it's been created.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/accounts/update/account_name \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "first_name": "James"
}
'
```
{% endtab %}
{% endtabs %}

## Delete Account

{% swagger method="delete" path="/accounts/{account_name}" baseUrl="https://api.duda.co/api" summary="Delete Account" expanded="false" %}
{% swagger-description %}
Deletes an existing Account
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** We currently do not support updating the account name or type after it's been created.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api.duda.co/api/accounts/account_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
