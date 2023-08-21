---
description: All webhooks related to site comments are listed below.
---

# Site Comments

### New Conversation

A notification is sent when a new conversation is created on a site. A publish can be triggered inside the Duda editor or via the publish API endpoint. Event type: `NEW_CONVERSATION`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "comment": {
      "text": "Please change this font to match our logo",
      "uuid": "5bfa1f6b-0426-4893-9f20-363efd20abb6"
    },
    "conversation_context": {
      "page_uuid": "88848a7e884147729b9f7b5c62c88377",
      "device": "DESKTOP",
      "conversation_number": 2
    },
    "conversation_uuid": "94320b30-96b1-40ad-a8f6-75eea204e255"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "customer@gmail.com"
  },
  "resource_data": {
    "site_name": "8a8ed8f4d2a34032b5cdc10feb483527"
  },
  "event_timestamp": 1547849546045,
  "event_type": "NEW_CONVERSATION"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="162">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.comment.text</strong></td><td><em>string</em></td><td>The text of the initial comment in the new conversation</td></tr><tr><td><strong>data.comment.uuid</strong></td><td><em>string</em></td><td>UUID of the comment</td></tr><tr><td><strong>data.conversation_context.page_uuid</strong></td><td><em>string</em></td><td>UUID of the page the comment was created on</td></tr><tr><td><strong>data.conversation_context.device</strong></td><td><em>string</em></td><td>The device view in use when the comment was entered. Possible values are <code>DESKTOP</code>, <code>TABLET</code>, or <code>MOBILE</code></td></tr><tr><td><strong>data.conversation_context.conversation_number</strong></td><td><em>int</em></td><td>Tracks the total number of conversations across a site. A conversation_number of 3 means this conversation is the 3rd conversation added to the site (regardless of page)</td></tr><tr><td><strong>data.conversation_uuid</strong></td><td><em>string</em></td><td>UUID of the conversation</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>Account name of the user who authored the comment.</td></tr></tbody></table>

### New Comment

A notification is sent when a new comment is added to an existing conversation. Event type: `NEW_COMMENT`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "comment": {
      "text": "Font family has been updated. Please confirm.",
      "uuid": "eafb2b72-2845-4d49-baf4-36f38ecc32a1"
    },
    "conversation_uuid": "0abab363-5b95-4f4e-a5d2-c7e39f993094"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "employee@myfirm.com"
  },
  "resource_data": {
    "site_name": "8a8b556ad2a34032b5cdc10feb483527"
  },
  "event_timestamp": 1547849618170,
  "event_type": "NEW_COMMENT"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="160">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.comment.text</strong></td><td><em>string</em></td><td>The text of the new comment</td></tr><tr><td><strong>data.comment.uuid</strong></td><td><em>string</em></td><td>UUID of the comment</td></tr><tr><td><strong>data.conversaton_uuid</strong></td><td><em>string</em></td><td>UUID of the conversation</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source of the event. Possible values are <code>Editor</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>The account who authored the new comment</td></tr></tbody></table>

### Conversation Update

A notification is sent when the status of a conversation has changed. A conversation can be resolved by a Team Member which will fire this webhook. Additionally a resolved conversation can be reopened which will fire a status of unresolved. Event type: `CONVERSATION_UPDATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "conversation_properties": {
      "status": "resolved",
      "deleted": false
    },
    "conversation_uuid": "e0fa2c71-c8a4-4cb7-b3f4-2040609a439b"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "employee@myfirm.com"
  },
  "resource_data": {
    "site_name": "8a8b556ad2a34032b5cdc10feb483527"
  },
  "event_timestamp": 1547849670851,
  "event_type": "CONVERSATION_UPDATED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="169">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data. conversation_properties.status</strong></td><td><em>string</em></td><td>The current status of the conversation. Possible values are "resolved, unresolved"</td></tr><tr><td><strong>data. conversation_properties.deleted</strong></td><td><em>bool</em></td><td>Boolean value depicting if conversation is deleted or not</td></tr><tr><td><strong>data.conversation_uuid</strong></td><td><em>string</em></td><td>UUID of the conversation</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>The account who initiated the status change</td></tr></tbody></table>

### Comment Edited

A notification is sent when a comment is edited. The webhook includes the complete comment object as shown below. Event type: `COMMENT_EDITED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "comment": {
      "text": "Please update with this image https://irp-cdn.multiscreensite.com/md/dmip/dms3rep/multi/woman-nature-smiling-green.jpg",
      "uuid": "abcbebdd-c430-444e-8ebb-ydaf78482bfc"
    },
    "conversation_uuid": "c4w79464-ed20-427e-9cb8-e1b89bab272b"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "lebowski@hotmail.com"
  },
  "resource_data": {
    "site_name": "je4ec1c6"
  },
  "event_timestamp": 1550081354524,
  "event_type": "COMMENT_EDITED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="184">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.comment.text</strong></td><td><em>string</em></td><td>The text of the comment</td></tr><tr><td><strong>data.comment.uuid</strong></td><td><em>string</em></td><td>UUID of the comment</td></tr><tr><td><strong>data.conversation_uuid</strong></td><td><em>string</em></td><td>UUID of the conversation</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>The account that initiated the edit</td></tr></tbody></table>

### Comment Deleted

A notification is sent when a comment is deleted. Event type: `COMMENT_DELETED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "comment": {
      "uuid": "adcaddb0-8674-4f0f-be5e-c926d58e2053"
    },
    "conversation_uuid": "de6c0840-94d1-4e7c-a6ac-41360a42b98a"
  },
  "source": {
    "type": "EDITOR",
    "account_name": "lebowski@hotmail.com"
  },
  "resource_data": {
    "site_name": "je4ec1c6"
  },
  "event_timestamp": 1550081783440,
  "event_type": "COMMENT_DELETED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="163">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.comment.uuid</strong></td><td><em>string</em></td><td>UUID of the comment</td></tr><tr><td><strong>data.conversaton_uuid</strong></td><td><em>string</em></td><td>UUID of the conversation</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the event. Possible values are <code>EDITOR</code> or <code>API</code></td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>The account that initiated the delete</td></tr></tbody></table>
