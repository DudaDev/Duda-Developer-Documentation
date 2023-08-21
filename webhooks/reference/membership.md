---
description: All webhooks related to Duda's Membership events are listed below.
---

# Membership

### Member Created

A notification is sent when a new member joins the site. Event type: `MEMBER_CREATED`

{% tabs %}
{% tab title="JSON" %}
```json
 {
  "data": {
    "id": "53140bbb-ccc5-4fb7-9ab3-260e327c07c0",
    "email": "john.smith@duda.co",
    "first_name": "John",
    "last_name": "Smith",
    "status": "PENDING",
    "signup_timestamp": 1683201225981
  },
  "source": null,
  "resource_data": {
    "site_name": "f925383f"
  },
  "event_timestamp": 1683201226067,
  "event_type": "MEMBER_CREATED"
}
```
{% endtab %}
{% endtabs %}

| Name                       | Type        | Description                                                                   |
| -------------------------- | ----------- | ----------------------------------------------------------------------------- |
| **data.id**                | _string_    | A unique identifier for the member                                            |
| **data.email**             | _string_    | The member email                                                              |
| **data.first\_name**       | _string_    | The first name of the member                                                  |
| **data.last\_name**        | _string_    | The last name of the member                                                   |
| **data.status**            | _string_    | Status of the member. Possible values are `ACTIVE`, `PENDING`, `UNAUTHORIZED` |
| **data.signup\_timestamp** | _timestamp_ | The member signup date in Unix format                                         |

### Member Updated

A notification is sent when the member status is changed. Event type: `MEMBER_UPDATED`

{% tabs %}
{% tab title="JSON" %}
```json
 {
  "data": {
    "id": "53140bbb-ccc5-4fb7-9ab3-260e327c07c0",
    "email": "john.smith@duda.co",
    "first_name": "John",
    "last_name": "Smith",
    "status": "ACTIVE",
    "signup_timestamp": 1683201225981
  },
  "source": null,
  "resource_data": {
    "site_name": "f925383f"
  },
  "event_timestamp": 1683201226067,
  "event_type": "MEMBER_UPDATED"
}
```
{% endtab %}
{% endtabs %}

### Member Deleted

A notification is sent when a member is deleted from the site. Event type: `MEMBER_DELETED`

{% tabs %}
{% tab title="JSON" %}
```json
 {
  "data": {
    "id": "53140bbb-ccc5-4fb7-9ab3-260e327c07c0",
    "email": "john.smith@duda.co",
    "first_name": "John",
    "last_name": "Smith",
    "status": "PENDING",
    "signup_timestamp": 1683201225981
  },
  "source": null,
  "resource_data": {
    "site_name": "f925383f"
  },
  "event_timestamp": 1683201226067,
  "event_type": "MEMBER_DELETED"
}
```
{% endtab %}
{% endtabs %}
