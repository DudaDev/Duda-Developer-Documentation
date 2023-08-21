# Site Backups

## List Backups

{% swagger method="get" path="/sites/multiscreen/backups/{site_name}" baseUrl="https://api.duda.co/api" summary="List Backups" expanded="false" fullWidth="false" %}
{% swagger-description %}
Get an array of existing site backups
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "date": "2014-06-07T11:18:51",
    "name": "russ7_Auto_3"
  },
  {
    "date": "2014-06-07T11:19:02",
    "name": "russ7_Auto_4"
  },
  {
    "date": "2014-06-07T11:19:13",
    "name": "russ7_Auto_5"
  },
  {
    "date": "2014-06-07T11:19:21",
    "name": "russ7_Auto_6"
  },
  {
    "date": "2014-06-07T11:29:49",
    "name": "russ7_Auto_7"
  },
  {
    "date": "2014-06-07T11:33:21",
    "name": "ManualBackup_1"
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
     --url https://api.duda.co/api/sites/multiscreen/backups/site_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Create Backup

{% swagger method="post" path="/sites/multiscreen/backups/{site_name}/create" baseUrl="https://api.duda.co/api" summary="Create Backup" expanded="false" %}
{% swagger-description %}
Create a new backup of a site. This is used for saving the existing state of a site. Good for saving a restore point before a user starts to edit a site or after work has been completed.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
The name of the backup being created

\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
  "name": "QA-Complete"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know:** Each site can have a maximum of 50 manually created backup versions and 50 that are automatically created upon each publish of the site (100 in total). Backups that are automatically created will have a name such as: `sitename_Auto_4`
{% endhint %}

{% hint style="warning" %}
**Heads up:** Spaces are not allowed in the name of a site backup
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/backups/site_name/create \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Restore Backup

{% swagger method="post" path="/sites/multiscreen/backups/{site_name}/restore/{backup_name}" baseUrl="https://api.duda.co/api" summary="Restore Backup" expanded="false" %}
{% swagger-description %}
Restore a site from an existing backup. This will fully restore the site back to the state it was in at the time of the backup creation. When restoring a site, a backup is automatically made before the restore begins.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="backup_name" type="string" required="true" %}
The name of a site backup to restore from

\



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
     --url https://api.duda.co/api/sites/multiscreen/backups/site_name/restore/backup_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Backup

{% swagger method="delete" path="/sites/multiscreen/backups/{site_name}/{backup_name}" baseUrl="https://api.duda.co/api" summary="Delete Backup" %}
{% swagger-description %}
Deletes an existing backup from a Site.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-parameter in="path" name="backup_name" type="string" required="true" %}
The name of a site backup to restore from
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
     --url https://api.duda.co/api/sites/multiscreen/backups/site_name/backup_name \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
