# Dynamic Dropdown

A dynamic dropdown is an input that allows you to fetch and display multiple options returned from a server outside of Duda. This allows the user to select the most relevant item and have that be integrated into the widget on their website.

This is often great when your service or platform has multiple different options or configurations that a user must select from. This way they can select the most relevant one, directly from the widget, as their designing i

## Fetch URL Request

When the widget is loaded in the editor, Duda will send a `POST` request to fetch data from your server. Duda expects a list of options to be returned from your server to configure the widget, based on the settings inside of your service. Duda sends the following data to your server:

{% tabs %}
{% tab title="JSON" %}
```json
{
  site: {
    site_name: '263ebd15',
    lang: 'en',
    account_uuid: '0ec203891d1f47608faeb3663e272d3f'
  },
  widget: { variables: [ ] }
}
```
{% endtab %}
{% endtabs %}

### Fetch URL Response

Respond to the `POST` request with a JSON object in the format below. Duda expects an array of options to be returned that a user can select from.

* The `value` will be embedded into the widget and transferred into handlebars/javascript.
* The `label` is the name the user will see. It should be human-readable

{% tabs %}
{% tab title="JSON" %}
```json
{
  "options": [
    {
      // The value to assign to the variable in the widget builder
      "value": "unique-value",
      
      // The label to display to the user in the dropdown
      "label": "unique-label",
    },
  ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Heads up: Fast Response Time**

The response from your server should happen quickly (ideally less than 50ms response time from your server), as this data is displayed to the user, in the editor, in real-time. Any delays will cause a poor experience for someone editing the website.
{% endhint %}

### Variables

As part of the Fetch Request data, Duda sends along with the variables & selections of the widget that the user has entered. This allows you to tailor your response based on how the widget is already configured.

### Authorization

Duda supports two different authentication mechanisms:

1. [Basic Authentication](../../reference/partner-api-reference/authentication.md#get-sso-link-1)
2. [HMAC Authentication](../../webhooks/tutorials/webhook-authentication.md)
