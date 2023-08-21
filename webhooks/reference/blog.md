---
description: All webhooks related to blog events are listed below.
---

# Blog

### Blog Post Publish

A notification is sent when a blog post is published. A publish can be triggered inside the Duda editor. Event type: `BLOG_POST_PUBLISH`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "title": "The Art of Playing Baseball",
    "republish": true,
    "first_publish": false
  },
  "source": {
    "type": "EDITOR",
    "account_name": "sammy.sosa@duda.co"
   },
   "resource_data": {
    "site_name": "der45dtj3465tee"
   },
   "event_timestamp": 1567603977697,
   "event_type": "BLOG_POST_PUBLISH"
}
```
{% endtab %}
{% endtabs %}

| Name                     | Type     | Description                                                                                             |
| ------------------------ | -------- | ------------------------------------------------------------------------------------------------------- |
| **data.title**           | _string_ | The title of the blog post                                                                              |
| **data.republish**       | _bool_   | Boolean stating if this was a republish of an existing blog post                                        |
| **data.first\_publish**  | _bool_   | Boolean stating if this was the first publish of a blog post                                            |
| **source.type**          | _string_ | The location of the source for the publish event. Possible values are EDITOR                            |
| **source.account\_name** | _string_ | If a publish was triggered through the editor, then this contains the account who initiated the publish |
