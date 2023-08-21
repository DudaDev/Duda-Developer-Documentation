---
description: All webhooks related to site events are listed below.
---

# Site

### Publish

A notification is sent when a site is published. A publish can be triggered inside the Duda editor or via the publish API endpoint. Event type: `PUBLISH`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "republish": false,
    "first_publish": true
  },
  "resource_data": {
    "site_name": "sw1d3f9f18eb4c82a472402505a731a1",
    "external_id": "my-external-id"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "event_type": "PUBLISH",
  "event_timestamp": 1532467846492,
  "resource_type": "site"
}
```
{% endtab %}
{% endtabs %}

| Name                     | Type     | Description                                                                                             |
| ------------------------ | -------- | ------------------------------------------------------------------------------------------------------- |
| **data.republish**       | _bool_   | Boolean stating if this was a republish of an already published site                                    |
| **data.first\_publish**  | _bool_   | Boolean stating if this was the first publish of a site                                                 |
| **source.type**          | _string_ | The location of the source for the publish event. Possible values are `EDITOR` or `API`                 |
| **source.account\_name** | _string_ | If a publish was triggered through the editor, then this contains the account who initiated the publish |
| **resource\_type**       | _string_ | Always set to `site` for the publish event                                                              |

{% hint style="info" %}
**Heads up:** If a site is published after it was unpublished, then both `republish` and `first_publish` are false
{% endhint %}

### Unpublish

A notification is sent when a site is unpublished. An unpubilsh can be triggered inside the Duda editor or via the unpublish API endpoint. Event type: `UNPUBLISH`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": 1532482228987,
  "resource_data": {
    "site_name": "sw1d3f9f18eb4c82a472402505a731a1",
    "external_id": "my-external-id"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "event_type": "UNPUBLISH",
  "event_timestamp": 1532471227566,
}
```
{% endtab %}
{% endtabs %}

| Name                     | Type     | Description                                                                                                  |
| ------------------------ | -------- | ------------------------------------------------------------------------------------------------------------ |
| **source.type**          | _string_ | The location of the source for the unpublish event. Possible values are `EDITOR` or `API`                    |
| **source.account\_name** | _string_ | If an unpublish was triggered through the editor, then this contains the account who initiated the unpublish |

### Form Submission

A notification is sent when a new form submissions takes place on a site. Event type: `CONTACT_FORM_SENT_V2`

{% tabs %}
{% tab title="JSON" %}
```json
{
 "data": {
   "utm_campaign": "MY_CAMPAIGN",  
   "fieldsData": [
     {
       "field_label": "Name",
       "field_value": "sdfsdf",
       "field_type": "text",
       "field_key": "",
       "field_id": "dmform-00"
     },
     {
       "field_label": "Message",
       "field_value": "sdfsdf",
       "field_type": "message",
       "field_key": "",
       "field_id": "dmform-01"
     },
     {
       "field_label": "Title",
       "field_value": "Contact Us",
       "field_type": "form_title",
       "field_key": "",
       "field_id": null
     }
   ],
   "recipients": [
      "email@site.com"
    ],
    "emailSubject": "Subject set in form widget",
    "emailSender": "Sender set in form widget"
 },
 "source": null,
 "resource_data": {
   "site_name": "974d714008f440529ea58094ccf9a97c"
 },
 "event_timestamp": 1569338502786,
 "event_type": "CONTACT_FORM_SENT_V2" 
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="215">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>fieldsData</strong></td><td><em>array</em></td><td>Array of all fields from the submitted form</td></tr><tr><td><strong>utm_campaign</strong></td><td><em>string</em></td><td>If the user has a <code>utm_campaign</code> cookie in their session, then it will be added to the webhook</td></tr></tbody></table>

### Site Creation

A notification is sent when a site is created. A site creation can be triggered inside the Duda editor or via the API. Event type: `SITE_CREATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
    "resource_data": {
       "site_name": "dfdd3f9f18eb4c82a472402505a731a1",
       "external_id": "my-external-id"
    },
    "source": {
       "type": "EDITOR",  
       "account_name": "user@email.com"
    },
       "event_type": "SITE_CREATED",
       "event_timestamp": 1532467846492,
       "resource_type": "site"
}
```
{% endtab %}
{% endtabs %}

| Name                     | Type     | Description                                                                               |
| ------------------------ | -------- | ----------------------------------------------------------------------------------------- |
| **source.type**          | _string_ | The location of the source for the unpublish event. Possible values are `EDITOR` or `API` |
| **source.account\_name** | _string_ | This contains the account who initiated the site creation.                                |
| **resource\_type**       |          | Always set to `site` for the site creation event                                          |

### Domain Update

A notification is sent when the domain of a site is updated. A domain change can be triggered inside the Duda editor or via the update site API endpoint. Event type: `DOMAIN_UPDATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "domain": null,
    "sub_domain": "example-time.multiscreensite.com",
    "alternate_domains": []
  },
  "resource_data": {
    "site_name": "sw1d3f9f18eb4c82a472402505a731a1",
    "external_id": "my-external-id"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "event_type": "DOMAIN_UPDATED",
  "event_timestamp": 1532471131957,
  "resource_type": "site"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="175">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.domain</strong></td><td><em>string</em></td><td>The current domain for the site. The value can be null</td></tr><tr><td><strong>data.sub_domain</strong></td><td><em>string</em></td><td>The current subdomain (default domain) for the site.</td></tr><tr><td><strong>data.alternate_domains</strong></td><td><em>array</em></td><td>List of optional alternate domains defined for this site</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the publish event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>If a publish was triggered through the editor, then this contains the account who initiated the publish</td></tr><tr><td><strong>resource_type</strong></td><td><em>string</em></td><td>Always set to <code>site</code> for the domain update event</td></tr></tbody></table>

### Certificate Created

A notification is sent when the SSL certificate for a site is generated. The same created event will also fire when the status is updated to `COMPLETE`. Event type: `CERTIFICATE_CREATED`

{% hint style="info" %}
**Good to know: Certificate Regeneration**

A webhook event is not triggered when the certificate is generated. Duda will renew/regenerate a new certificate every 3 months, but no event will be triggered when this occurs.
{% endhint %}

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    id: "12345abc",
    domains: ["www.domain.com","domain.com"],
    deployment_status: "DEPLOYED",
    created: 1532467846492
  },
  "resource_data": {
    "site_name": "8a8eda"
  },
  "event_type": "CERTIFICATE_CREATED",
  "event_timestamp": 1683201225981
}

```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="245">Name</th><th width="138">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.id</strong></td><td><em>string</em></td><td>The id of the certificate generated.</td></tr><tr><td><strong>data.domains</strong></td><td><em>array</em></td><td>List of domains assigned to the generated certificate. This should include alternate domains and the www value, as well.</td></tr><tr><td><strong>data.deployment_status</strong></td><td><em>string</em></td><td>Status of the generated certificate. Can be: <code>PENDING</code>, <code>DEPLOYED</code>, or <code>FAILED</code>.</td></tr></tbody></table>

### Certificate Deleted

A notification is sent when the SSL certificate for a site is deleted. Event type: `CERTIFICATE_DELETED`

{% tabs %}
{% tab title="First Tab" %}
```json
{
  "data": {
    id: "12345abc",
    domains: ["www.domain.com","domain.com"],
    created: 1532467846492,
  },
  "resource_data": {
    "site_name": "8a8eda"
  },
  "event_type": "CERTIFICATE_DELETED",
  "event_timestamp": 1683201225981
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="181">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.id</strong></td><td><em>string</em></td><td>The id of the certificate deleted.</td></tr><tr><td><strong>data.domains</strong></td><td><em>array</em></td><td>List of domains associated with the deleted certificate.</td></tr></tbody></table>

### Site Plan Changed

A notification is sent when the plan ID of a site has been changed. Event type: `SITE_PLAN_CHANGED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "newPlanId":804,
    "siteAlias":"2dbf8579",
    "previousPlanId":802
  },
  "source": {
    "type":"EDITOR",
    "account_name":"user@email.com"
  },
  "resource_data": {
    "site_name":"2dbf8579"
  },
  "event_timestamp":1686861354729,
  "event_type":"SITE_PLAN_CHANGED"
}

```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="169">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.newPlanId</strong></td><td><em>int</em></td><td>The ID of the new Plan assigned to the site.</td></tr><tr><td><strong>data.siteAlias</strong></td><td><em>string</em></td><td>Duda's unique identifier for the Site.</td></tr><tr><td><strong>data.previousPlanId</strong></td><td><em>int</em></td><td>The ID of the plan the site was previously assigned to.</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the plan changed event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>This contains the account who initiated the plan change.</td></tr></tbody></table>

### Backup Restored

A notification is sent when a backup is restored for a site. Event type: `SITE_RESTORED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": 1686862504428,
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "resource_data": {
    "site_name": "2dbf8579"
  },
  "event_timestamp": 1686862504455,
  "event_type": "SITE_RESTORED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="173">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data</strong></td><td><em>timestamp</em></td><td>The date the back up was restored in Unix format</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the backup restored event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>This contains the account who initiated the backup restore.</td></tr></tbody></table>
