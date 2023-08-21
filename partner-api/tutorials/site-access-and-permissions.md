# Site Access & Permissions

### Granting Site Access to a Client

[Team members](creating-team-members.md) have access to all sites in an organization. [Client accounts](../../reference/partner-api-reference/accounts.md#account-object), in comparison, are granted access on a site-by-site basis. A client may have access to a single site or many sites within your organization, and an individual site may be accessible to one or more clients. This access is given either directly through the [Duda client management page](https://support.duda.co/hc/en-us/articles/360042933853-Manage-User-Permissions), or by using the Duda Partner API.

The [grant access](../../reference/partner-api-reference/client-permissions.md#grant-site-access-1) endpoint requires both the `account_name` associated with the client and the `site_name` property assigned to a Duda website as path parameters. You are also able to supply a [list of permissions](../../reference/partner-api-reference/client-permissions.md#get-client-permissions-1) which describe the level of access the client will be given when editing the specified site.

To grant access via the API, create or select an existing client member from the client management page. Note the value in the Email address field. This will be the `account_name` needed for the call. Next create or select an existing site from the site dashboard. While editing the site, note the unique site name located in the URL bar of the browser e.g., [https://my.duda.co/home/site/\*\*site\_name](https://my.duda.co/home/site/\*\*site\_name)\*\*. Substitute your values in the example below along with your [Duda API key and password](../../reference/partner-api-reference/#authentication-and-security)

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/accounts/johnsmith@gmail.com/sites/146856ab/permissions \
-d '{"permissions":["EDIT","DEV_MODE","STATS_TAB"]}'
```
{% endtab %}
{% endtabs %}

You can always view what permissions a client has on a given site by making a [get permissions](../../reference/partner-api-reference/client-permissions.md#get-client-permissions-1) API call as illustrated below. Substituting your own values for the account and site name within the URL path.

{% tabs %}
{% tab title="List Client Permissions for a Site" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/accounts/johnsmith@gmail.com/sites/146856ab/permissions
```
{% endtab %}
{% endtabs %}

It is important to note that some permissions are dependent on other permissions being present. For example, you cannot grant a client access to a site's `DEV_MODE` if they do not have the `EDIT` permission defined. You can find a [list of all possible permissions](../../reference/partner-api-reference/client-permissions.md#list-client-permissions-1), along with any dependencies, within our API reference.

### Team Member Permissions & Site Access

Team Members have access to all sites under your Duda account. Currently there is not a way to allow a team member access to a subset of sites. You are able to manage what permissions a team member has for all sites. This can be done via the [Duda dashboard](https://support.duda.co/hc/en-us/articles/360042435514-Manage-Team-Permissions) or using the [Duda Partner API](creating-team-members.md).
