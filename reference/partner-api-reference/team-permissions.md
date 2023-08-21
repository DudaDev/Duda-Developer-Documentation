# Team Permissions

## List Duda Team Groups

{% swagger method="get" path="/permission-groups/default" baseUrl="https://api.duda.co/api" summary="List Duda Team Groups" expanded="false" fullWidth="false" %}
{% swagger-description %}
List Duda's assignable permission group for staff account.
{% endswagger-description %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
    {
        "group_name": "administrator",
        "color": "rgb(253,113,34)",
        "title": "Admin",
        "permissions": [
            "BLOG",
            "LIMIT_EDITING",
            "ANNOTATIONS",
            "EDIT_SITES",
            "CREATE_SITES",
            "DELETE_SITES",
            "API",
            "PRO_SETTINGS",
            "MANAGE_STAFF",
            "STATS",
            "E_COMMERCE",
            "MARKETING",
            "REPUBLISH",
            "PUBLISH",
            "DEV_MODE",
            "CUSTOM_DOMAIN",
            "MANAGE_CUSTOMERS",
            "PUSH_NOTIFICATIONS",
            "WIDGETS_BUILDER",
            "MANAGE_CATEGORY",
            "INSTALL_APP",
            "VIEW_APP",
            "CONTENT_LIBRARY",
            "ACTIVITY_LOG"
        ]
    },
    {
        "group_name": "salesman",
        "color": "rgb(36,206,151)",
        "title": "Sales",
        "permissions": []
    },
    {
        "group_name": "designer",
        "color": "rgb(21,193,191)",
        "title": "Designer",
        "permissions": [
            "CREATE_SITES",
            "BLOG",
            "LIMIT_EDITING",
            "EDIT_SITES",
            "REPUBLISH",
            "CONTENT_LIBRARY",
            "PUSH_NOTIFICATIONS",
            "E_COMMERCE",
            "MARKETING",
            "VIEW_APP"
        ]
    },
    {
        "group_name": "storemanager",
        "color": "rgb(53,188,221)",
        "title": "Store Manager",
        "permissions": [
            "E_COMMERCE"
        ]
    },
    {
        "group_name": "blogger",
        "color": "rgb(0,150,136)",
        "title": "Blogger",
        "permissions": [
            "BLOG"
        ]
    }
]{}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/permission-groups/default \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## List Custom Team Groups

{% swagger method="get" path="/permission-groups/custom" baseUrl="https://api.duda.co/api" summary="List Custom Team Group" expanded="false" %}
{% swagger-description %}
List your specific custom permission groups for staff account.
{% endswagger-description %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "group_name": "MjcwNzg",
    "color": "rgb(49,49,49)",
    "title": "Support Tier 3",
    "permissions": [
      "EDIT_SITES",
      "BLOG"
    ]
  },
  {
    "group_name": "MjkzMzQ",
    "color": "rgb(49,49,49)",
    "title": "Template Designer",
    "permissions": [
      "BLOG",
      "LIMIT_EDITING",
      "ANNOTATIONS",
      "EDIT_SITES",
      "CREATE_SITES",
      "DELETE_SITES",
      "E_COMMERCE",
      "MARKETING",
      "DEV_MODE",
      "MANAGE_CATEGORY",
      "CONTENT_LIBRARY"
    ]
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
     --url https://api.duda.co/api/permission-groups/custom \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Assign Team Member to Group

{% swagger method="post" path="/permission-groups/{group_name}/accounts/{account_name}/add" baseUrl="https://api.duda.co/api" summary="Assign Team Member to Group" expanded="false" %}
{% swagger-description %}
List your specific custom permission groups for staff account.
{% endswagger-description %}

{% swagger-parameter in="path" name="group_name" type="string" required="true" %}
The name associated with a team permission group
{% endswagger-parameter %}

{% swagger-parameter in="path" name="account_name" type="string" required="true" %}
The account name is a unique reference to the account
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
     --url https://api.duda.co/api/permission-groups/group_name/accounts/account_name/add \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
