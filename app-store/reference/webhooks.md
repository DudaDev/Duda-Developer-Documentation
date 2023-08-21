# Webhooks

Your App can register for webhooks related to actions that happen inside of the Duda platform. This helps ensure that your App stays in sync with actions that might update the website.

You can see the full [reference & data for webhooks in our webhook reference section](../../webhooks/introduction.md).

### Registering for Webhooks:

In your App Manifest, you can configure which events your App recieves:

{% tabs %}
{% tab title="JSON" %}
```json
{
  "webhooks": {
    "endpoint": "https://temporary.com/endpoint",
    "events": [
      "CONTENT_LIB_CHANGED",
      "CONTENT_LIB_PUBLISHED",
      "PUBLISH"
    ]
  },
  ...OtherManifestSettings
}
```
{% endtab %}
{% endtabs %}

When the App is installed on a website, Duda will then make sure that all events you subscribed to are sent to your server.

{% hint style="warning" %}
**Heads up: Updating Webhooks in Manifest**

If in the future you update which webhooks your App receives, you should know that it will not update webhooks for old/previous installs. If you need to start recieving those webhooks, the App either needs to be uninstalled or reinstalled. If that's an issue, please contact Duda.
{% endhint %}

### Scopes and webhooks

Duda limits which webhooks you can recieved, based on the scopes assigned to your App. When updating your manifest, if you try and include a webhook type that is not within your assigned scopes, you will get an error. You can see which scopes relate to which webhooks in the [scopes reference.](scopes.md)

### Common use cases:

* **Domain Update:** If your App needs to know the domain of the website, you should register for the `DOMAIN_UPDATED` webhook to know if the domain changes.
* **Publish**: Sometimes an App needs to know when content changes on the website. For example, if your App crawls the live website for content or cookies. This can be done by listening to the publish webhook.
