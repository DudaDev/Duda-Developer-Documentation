# Client Permissions

## Client Permission Object

{% tabs %}
{% tab title="JSON" %}
```json
["STATS_TAB",
  "EDIT",
  "ADD_FLEX",
  "E_COMMERCE",
  "PUBLISH",
  "REPUBLISH",
  "DEV_MODE",
  "INSITE",
  "SEO",
  "BACKUPS",
  "CUSTOM_DOMAIN",
  "RESET",
  "BLOG",
  "PUSH_NOTIFICATIONS",
  "LIMITED_EDITING",
  "SITE_COMMENTS",
  "CONTENT_LIBRARY",
  "EDIT_CONNECTED_DATA",
  "MANAGE_CONNECTED_DATA",
  "USE_APP",
  "CLIENT_MANAGE_FREE_APPS",
  "AI_ASSISTANT"]
```
{% endtab %}
{% endtabs %}

| Permission                 | Dependency                                    | Description                                                                                                         |
| -------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| STATS\_TAB                 | (None)                                        | Access to statistics for this website.                                                                              |
| EDIT                       | BLOG, LIMITED\_EDITING                        | Allow the user to perform all possible edits to the website, such as delete and move elements, and add new content. |
| DEV\_MODE                  | EDIT                                          | Allow direct access to the HTML & CSS of the website. This still allows the user to use the HTML embed widget.      |
| INSITE                     | EDIT                                          | Add, edit, or delete existing website personalization rules.                                                        |
| E\_COMMERCE                | (None)                                        | Manage catalogue, view orders and control store settings.                                                           |
| SEO                        | EDIT                                          | Set SEO settings on the site or page level.                                                                         |
| CUSTOM\_DOMAIN             | EDIT                                          | Set or edit the domain of a website. Can only be accessed on published websites.                                    |
| BLOG                       | (None)                                        | Give access to write new posts, edit existing ones, and manage blog settings.                                       |
| REPUBLISH                  | EDIT                                          | Update the live site with all changes made in the editor.                                                           |
| PUBLISH                    | (None)                                        | Publish the site for the first time.                                                                                |
| ADD\_FLEX                  | EDIT                                          | Add Flex templates and sections in the editor.                                                                      |
| BACKUPS                    | LIMITED\_EDITING                              | Create, restore and delete backups.                                                                                 |
| RESET                      | LIMITED\_EDITING                              | Reset and pick a new template for an existing site.                                                                 |
| AI\_ASSISTANT              | (None)                                        | Enable clients to use the AI Assistant to generate content.                                                         |
| LIMITED\_EDITING           | (None)                                        | Edit existing widget content.                                                                                       |
| SITE\_COMMENTS             | (None)                                        | Add, edit and delete site comments.                                                                                 |
| CONTENT\_LIBRARY           | LIMITED\_EDITING                              | Manage site Content Library including images, business info, form responses, etc.                                   |
| EDIT\_CONNECTED\_DATA      | (None)                                        | Edit connected content from the Connected Data popup.                                                               |
| MANAGE\_CONNECTED\_DATA    | EDIT, EDIT\_CONNECTED\_DATA, CONTENT\_LIBRARY | Add and manage widgets with Connected Data. Create and manage Dynamic Pages.                                        |
| USE\_APP                   | LIMITED\_EDITING                              | Use all apps which are added to a site, requires editing permissions.                                               |
| CLIENT\_MANAGE\_FREE\_APPS | LIMITED\_EDITING                              | Add, remove and use free apps. Use paid apps added by other users. Requires editing permissions.                    |

## List Client Permissions

{% swagger method="get" path="/accounts/permissions/multiscreen" baseUrl="https://api.duda.co/api" summary="List Client Permissions" expanded="false" fullWidth="false" %}
{% swagger-description %}
List all assignable permissions.
{% endswagger-description %}

{% swagger-response status="200: OK" description="JSON" %}
```json
[ 'STATS_TAB',
  'EDIT',
  'ADD_FLEX',
  'E_COMMERCE',
  'PUBLISH',
  'REPUBLISH',
  'DEV_MODE',
  'INSITE',
  'SEO',
  'BACKUPS',
  'CUSTOM_DOMAIN',
  'RESET',
  'BLOG',
  'PUSH_NOTIFICATIONS',
  'LIMITED_EDITING',
  'SITE_COMMENTS',
  'CONTENT_LIBRARY',
  'EDIT_CONNECTED_DATA',
  'MANAGE_CONNECTED_DATA',
  'USE_APP',
  'CLIENT_MANAGE_FREE_APPS',
  "AI_ASSISTANT"]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** We recommend updating your list of permissions on a daily basis and using blacklist of permissions you don't want customers to have access to. This way if Duda rolls out new features, you will give customers access to new features instead of limiting them.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/accounts/permissions/multiscreen \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Client Permissions

{% swagger method="get" path="/accounts/{account_name}/sites/{site_name}/permissions" baseUrl="https://api.duda.co/api" summary="Get Client Permissions" expanded="false" %}
{% swagger-description %}
Returns the assigned Site permissions for an Account
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
  "permissions": [
    "STATS_TAB",
    "EDIT",
    "PUBLISH",
    "REPUBLISH",
    "STATS_EMAIL",
    "SEO",
    "CUSTOM_DOMAIN",
    "BACKUPS"
  ]
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
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/permissions \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## List Client Sites

{% swagger method="get" path="/accounts/grant-access/{account_name}/sites/multiscreen" baseUrl="https://api.duda.co/api" summary="List Client Sites" expanded="false" %}
{% swagger-description %}
List all Sites that an Account has access to.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "site_name": "08e5f101"
  },
  {
    "site_name": "a7fa3956"
  },
  {
    "site_name": "u8elal2"
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
     --url https://api.duda.co/api/accounts/grant-access/account_name/sites/multiscreen \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Grant Site Access

{% swagger method="post" path="/accounts/{account_name}/sites/{site_name}/permissions" baseUrl="https://api.duda.co/api" summary="Grant Site Access" expanded="false" %}
{% swagger-description %}
Grant access to a Site for an Account.

When giving customers access to a site, it is important to note that some permissions are dependent on other permissions being present. For example, you cannot give a customer access to a site's SEO if they do not have permission to edit the site first. See below for which permissions are dependent on others for each site type.

If you would like to update the permissions that a specific customer has to a site, you can call the same API to overwrite any existing permissions.
{% endswagger-description %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
{% endswagger-parameter %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="body" name="permissions" type="array of strings" %}
List of permissions granted to the customer for the specified site
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
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/permissions \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "permissions": [
    "EDIT",
    "PUBLISH"
  ]
}
'
```
{% endtab %}
{% endtabs %}

## Remove Site Access

{% swagger method="delete" path="/accounts/{account_name}/sites/{site_name}/permissions" baseUrl="https://api.duda.co/api" summary="Remove Site Access" expanded="false" %}
{% swagger-description %}
Removes access to a Site for an Account.
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
     --url https://api.duda.co/api/accounts/account_name/sites/site_name/permissions \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
