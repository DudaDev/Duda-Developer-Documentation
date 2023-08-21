# Creating Team Members

Team Members, also known as `STAFF` accounts, represent a member of your company who has access to work on sites. Their account will not be white-labeled and will see Duda-related content, allowing them access to features like [Duda Support](https://support.duda.co/hc/en-us), [Duda Community](https://community.duda.co/) and other Duda resources. The level of access is determined by the permissions granted to that account. Team member accounts will always see all sites in your Duda account. This access is given either directly through the [Duda Team Permissions page](https://support.duda.co/hc/en-us/articles/1500001597802), or by using the Duda Partner API.

Create an account through the [Create Account](../../reference/partner-api-reference/accounts.md#create-account-1) API as illustrated below. The API requires an `account_name`. To provide this account access to Duda, pass `STAFF` as the `account_type` within the body of the call. Substitute your values in the following example along with your [Duda API key and password](../../reference/partner-api-reference/#authentication-and-security).

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/accounts/create \
-d '{"account_type": "STAFF", "account_name": "johnsmith@websites.com"}'
```
{% endtab %}
{% endtabs %}

You are also able to supply a list of permissions that describe the level of access a team member will be given when accessing the Duda Platform. Unlike [client permissions](../../reference/partner-api-reference/client-permissions.md#client-permission-object), Team members are assigned to a permission group, where each group has a specific set of permissions granted. Duda has two endpoints to collect permission group names.

Collect the `group_name` for Duda's groups from the [default group list](../../reference/partner-api-reference/team-permissions.md#list-custom-team-group). Substituting your own values for the account and site name within the URL path.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Accept: application/json' \
-X GET \
-k https://api.duda.co/api/permission-groups/default \
```
{% endtab %}
{% endtabs %}

To assign a team member to a custom group, create or select a custom group from the [Duda Team Permissions page](https://support.duda.co/hc/en-us/articles/360061887933-Create-Custom-Team-Permissions-Groups). Collect the `group_name` for custom groups from the [custom group list](../../reference/partner-api-reference/team-permissions.md#list-custom-team-group).

{% tabs %}
{% tab title="First Tab" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Accept: application/json' \
-X GET \
-k https://api.duda.co/api/permission-groups/custom \
```
{% endtab %}
{% endtabs %}

The assign permission group endpoint requires both the `account_name` associated with the staff account and the `group_name` as path parameters. Use these values to make an [assign group](../../reference/partner-api-reference/team-permissions.md#assign-team-member-to-group-1) API call as illustrated below. Substitute your own values for the account and site name within the URL path.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Accept: application/json' \
-X POST \
-k https://api.duda.co/api/permission-groups/storemanager/accounts/johnsmith@websites.com/add \
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Heads up: Group required**

When creating `STAFF` members, assigning them to a group is required. If you do not assign them to a group, they will not have access to any features they might need and won't appear in the Manage Team section of the dashboard.
{% endhint %}
