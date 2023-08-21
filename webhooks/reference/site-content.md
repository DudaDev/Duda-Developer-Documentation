---
description: All webhooks related to content library events are listed below.
---

# Site Content

### Content Library Updated

A notification is sent when a field is updated within Business Info, Business Text, or Business Images. Event type: `CONTENT_LIB_CHANGED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "location_data": {
      "phones": [
        {
          "phoneNumber": "555-5555",
          "label": "main"
        }
      ],
      "emails": [],
      "social_accounts": {
        "socialAccounts": {}
      },
      "address_geolocation": "1 Main st, Boulder, CO 12345, United States of America",
      "geo": {
        "longitude": "-105.06089",
        "latitude": "39.90951"
      },
      "logo_url": null,
      "business_hours": [],
      "schema": {
        "type": "AnimalShelter"
      },
      "label": null,
      "address": {
        "streetAddress": "1 Main st",
        "postalCode": "12345",
        "region": "CO",
        "city": "Boulder",
        "country": "USA",
        "countryCode": "USA"
      }
    },
    "additional_locations": [],
    "site_texts": {
      "overview": null,
      "services": null,
      "custom": [],
      "about_us": "<p class=\"rteBlock\">This is the about us section of our shelter.</p>"
    },
    "business_data": {
      "name": "Boulder Animal Shelter",
      "logo_url": null,
      "data_controller": null
    },
    "site_images": [
      {
        "label": "Image-01",
        "url": "https://irp.cdn-website.com/md/dmtmpl/554b1d7e-bb97-403d-98ad-81477c37c93a/dms3rep/multi/class_placeholder.jpg",
        "alt": null
      }
    ]
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "resource_data": {
    "site_name": "2dbf8579"
  },
  "event_timestamp": 1686862679132,
  "event_type": "CONTENT_LIB_CHANGED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="151">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data</strong></td><td><em>object</em></td><td>The updated data that exists within the content library of a site.</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the publish event. Possible values are EDITOR.</td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>If a publish was triggered through the editor, then this contains the account who initiated the publish.</td></tr></tbody></table>

### Content Library Published

A notification is sent when the content library is published and applied to a live site. Event type: `CONTENT_LIB_PUBLISHED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "location_data": {
      "phones": [
        {
          "phoneNumber": "555-5555",
          "label": "main"
        }
      ],
      "emails": [],
      "social_accounts": {
        "socialAccounts": {}
      },
      "address_geolocation": "1 Main st, Boulder, CO 12345, United States of America",
      "geo": {
        "longitude": "-105.06089",
        "latitude": "39.90951"
      },
      "logo_url": null,
      "business_hours": [],
      "schema": {
        "type": "AnimalShelter"
      },
      "label": null,
      "address": {
        "streetAddress": "1 Main st",
        "postalCode": "12345",
        "region": "CO",
        "city": "Boulder",
        "country": "USA",
        "countryCode": "USA"
      }
    },
    "additional_locations": [],
    "site_texts": {
      "overview": null,
      "services": null,
      "custom": [],
      "about_us": "<p class=\"rteBlock\">This is the about us section of our shelter.</p>"
    },
    "business_data": {
      "name": "Boulder Animal Shelter",
      "logo_url": null,
      "data_controller": null
    },
    "site_images": [
      {
        "label": "Image-01",
        "url": "https://irp.cdn-website.com/md/dmtmpl/554b1d7e-bb97-403d-98ad-81477c37c93a/dms3rep/multi/class_placeholder.jpg",
        "alt": null
      }
    ]
  },
  "source": {
    "type": "EDITOR",
    "account_name": "user@email.com"
  },
  "resource_data": {
    "site_name": "2dbf8579"
  },
  "event_timestamp": 1686862679132,
  "event_type": "CONTENT_LIB_PUBLISHED"
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Name</th><th width="190">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data</strong></td><td><em>object</em></td><td>The updated data that exists within the content library of a published site.</td></tr><tr><td><strong>source.type</strong></td><td><em>string</em></td><td>The location of the source for the publish event. Possible values are EDITOR.</td></tr><tr><td><strong>source.account_name</strong></td><td><em>string</em></td><td>If a publish was triggered through the editor, then this contains the account who initiated the publish.</td></tr></tbody></table>
