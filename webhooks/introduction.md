# Introduction

A webhook delivers data to your application as it happens within Duda. Unlike our APIs where you would need to request data very frequently in order for your system to know the status of data within the Duda system.

Webhooks are HTTP requests which can be enabled to send notifications when specific events occur in Duda or on a site. Then, your application performs whatever logic you feel necessary - read/write from a database, integrate with another API, or perform a computation. This allows external systems to react in real-time to your events as they happen.

### Receiving and Retrying Webhook Notifications

Webhook notifications are sent as an HTTP POST request. The notification data is sent as JSON in the `POST` body.

Duda uses an exponential backoff policy with 30 seconds intervals and a max of 3 retries. The first retry will be after 30 seconds, the second 90 seconds after the initial attempt, and the third and last, 210 seconds after the initial attempt.

### JSON Format

Below is an example JSON data structure for a webhook. Each event includes specific information relevant to that event.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "event_type": "",
  "event_timestamp": "",
  "resource_type": "",
  "data": { ... },
  "resource_data": { ... },
  "source": { ... }
}
```
{% endtab %}
{% endtabs %}

| Name                 | Included   | Description                                             |
| -------------------- | ---------- | ------------------------------------------------------- |
| **event\_type**      | always     | describes the type of event                             |
| **event\_timestamp** | always     | epoch timestamp of the event occurrence in milliseconds |
| **resource\_type**   | not always | describes what event relates to                         |
| **data**             | not always | additional data related to an event                     |
| **resource\_data**   | always     | data on the resource (ex. site\_name, external\_id)     |
| **source**           | not always | where the event was triggered (ex. API, EDITOR)         |

\
