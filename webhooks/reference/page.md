---
description: All webhooks related to page events are listed below.
---

# Page

### Page Published

A notification is sent when a site page is published. A publish can be triggered inside the Duda editor. Event type: `PAGE_PUBLISHED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "pageUuid": "f408e3b0a2a04ecdb47dda40b42e45c5",
    "pageAlias": "home"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "resource_data": {
    "site_name": "2dbf8579"
  },
  "event_timestamp": 1686864645790,
  "event_type": "PAGE_PUBLISHED"
}
```
{% endtab %}
{% endtabs %}

| Name                     | Type     | Description                                                                                             |
| ------------------------ | -------- | ------------------------------------------------------------------------------------------------------- |
| **data.pageUuid**        | _string_ | The internal unique identifier of the published page.                                                   |
| **data.pageAlias**       | _string_ | The title of the published page. It's used in the navigation of the site and pages menu.                |
| **source.type**          | _string_ | The location of the source for the publish event. Possible values are EDITOR                            |
| **source.account\_name** | _string_ | If a publish was triggered through the editor, then this contains the account who initiated the publish |
