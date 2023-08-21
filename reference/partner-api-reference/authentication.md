# Authentication

## Get SSO Link

{% swagger method="get" path="/accounts/sso/{account_name}/link" baseUrl="https://api.duda.co/api" summary="Get SSO Link" expanded="false" fullWidth="false" %}
{% swagger-description %}
Generates a link that automatically logs an Account into Duda.

All valid targets are listed below. If a target is specified, then a `site_name` must be provided. You can generate a link to the Duda dashboard, the editor, stats page or reset a site. If you are sending the user to the stats, editor or reset pages, you will need to pass the `site_name` and `target` on the query string. After generating the link, you should direct the users browser to this URL. This API is supported for `CUSTOMER` and `STAFF` account types.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-parameter in="query" name="site_name" type="string" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="query" name="target" type="string" %}
See valid targets listed below
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object of string" %}
```json
{
  "url": "http://example.mobilewebsiteserver.com/home/site/146856ab?dm_sso=2!eyJyZXFVdWlkIjoiYzU0Y2E0MzYwNDA2NDgwZDlmZmM2MTIxY2FiOTM2MzAifQ"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

| Target Location  | Query Key | Query Value       | Description                                                                                                                                                                                                                                                                                |
| ---------------- | --------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dashboard        | (none)    | (none)            | Send the user directly to their website dashboard. You do not need to send a target or site\_name parameter.                                                                                                                                                                               |
| Stats            | target    | STATS             | Send the user directly to the website statistics page.                                                                                                                                                                                                                                     |
| Site Editor      | target    | EDITOR            | Send the user directly to the white labeled website builder.                                                                                                                                                                                                                               |
| Template Chooser | target    | RESET\_SITE       | Send the user directly to select a new template / reset site page. If the user does reset the site, all existing website edits will be lost and the site will be reset to a new template that is selected.                                                                                 |
| Template Chooser | target    | SWITCH\_TEMPLATE  | Send the user directly to select new a template without resetting the site. This will retain all site data and installed apps. **When implementing a** [**DIY Flow**](https://developer.duda.co/docs/diy-onboarding) **it is highly recommended to use this target and not `RESET_SITE`.** |
| Simple Editor    | target    | RESET\_BASIC      | Send the user directly to the simple editor to build or maintain their site. (note: the simple editor is an add-on and may not be available on all accounts)                                                                                                                               |
| Store Management | target    | STORE\_MANAGEMENT | Send the user directly to the Store Management area within the site editor.                                                                                                                                                                                                                |

{% hint style="info" %}
**Good to Know:** SSO Links should be generated on demand and should not be generated upon page load or be statically linked to. SSO Tokens are only valid for two minutes, so you need to verify in real time that the user is authenticated to your system, then generate the SSO link once they intend to enter the editor, dashboard, stats, etc..
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/accounts/sso/account_name/link \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Password Reset Link

{% swagger method="post" path="/accounts/reset-password/{account_name}" baseUrl="https://api.duda.co/api" summary="Create Password Reset Link" expanded="false" %}
{% swagger-description %}
Generates a password reset link for an Account.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "reset_url": "http://example.mobilewebsiteserver.com/login/resetpwd?uuid=e4ec7b6f-b77f-47de-aedf-d2383ccb5de2",
  "expiration": 1679060736175
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** We recommend emailing the Reset Password link directly to your customers. This URL is only valid for 30 minutes.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/accounts/reset-password/account_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Welcome Link

{% swagger method="post" path="/accounts/{account_name}/welcome" baseUrl="https://api.duda.co/api" summary="Create Welcome Link" expanded="false" %}
{% swagger-description %}
Delete existing rows of data that exist within the collection.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "welcome_url": "http://example.mobilewebsiteserver.com/login/welcome?lang=en&uuid=b447f9d0c5c74b7d9114875e3c7562dc",
  "expiration": 1679060736175
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
     --url https://api.duda.co/api/accounts/account_name/welcome \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
