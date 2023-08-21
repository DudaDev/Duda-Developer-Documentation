# Plans

{% hint style="warning" %}
**Heads up: Custom Plan Required**

In order to access this part of the API, schedule a time to speak with a member of our Partner Team about upgrading your account to a Custom plan.
{% endhint %}

Duda Partners offering a DIY(Do-it-Yourself) solution to their customers have the opportunity to lock different feature sets to clients. These feature sets are broken down into different plans that can be used as an upsell opportunity.

View a break down of the [plans](https://docs.google.com/spreadsheets/d/1ix6kmmLwYq0oDvnm6u08qosf9tHc5dlO04gR7V3662k/edit#gid=1834328068).

When enabled, plans are set at the site level. Within the editor, clients see these features available within the editor, but they appear locked with a message to upgrade.

​

![](https://files.readme.io/89c433b-upsell\_messaging.png)

​

In order to upgrade sites to higher plans, you need to utilize the [Change Site Plan](../../reference/partner-api-reference/site-plans.md#update-site-plan-1) API endpoint and build a UI that the upgrade button links to.

Learn more about [Upsell + Publish Flows](../how-to-guides/upsell-+-publish-flows.md).

{% hint style="info" %}
**Good to know:** You do not need to offer all of these plans to your clients. You can start your sites on any of the 6 plans.
{% endhint %}

### Permissions vs Plans

Granting clients permission to a certain feature displays the feature within the editor. While revoking a permission hides this feature for the client within the editor.

Plans revoke the use of the feature, but allow your clients the opportunity to access the feature by upgrading to a higher-tiered plan.

In order for a client to see a locked feature within the editor, they need to have been granted the associating feature permission.

{% hint style="warning" %}
**Heads up:** If on a custom plan, please reach out to your Account Manager to have this feature enabled for your account.
{% endhint %}
