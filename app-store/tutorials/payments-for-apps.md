# Payments for Apps

### App payment concepts

All payments for apps under the Duda App Store are:

* Subscription-based
* Follow a 'do not renew' policy when canceled

### Subscription-based

All app payments are based on _subscriptions_. This means once a user purchases an app with a paid plan, they start a subscription. The subscription will recur based on the date the App was upgraded. Duda supports _monthly_ and _annual_ subscriptions.

{% hint style="info" %}
**Good to know: Setting price**

Prices are not set in the app's manifest. To configure prices, contact the Duda App Store team.
{% endhint %}

{% hint style="warning" %}
**Heads up: Limited support for annual plans**

Currently, Duda does not support presenting both monthly and annual plans for users in the Duda Editor UI. Apps can choose whether to use monthly **or** annual plans.\
We plan to add support for both soon.
{% endhint %}

### Do not renew

Once the user asks to stop paying for an app, Duda stops the renewal of the subscription. Duda won't refund users for the remaining unused period.

Examples:

1. The user purchased a monthly subscription with a price of $10 on January 10th. On February 10th the subscription was renewed. On February 15th the user removed the app. Duda won't renew the subscription on the coming renewal date of March 10th and won't refund the user for the period of February 16th - March 9th.
2. The user purchased an annual subscription with a price of $100 on January 10th, 2019. On February 15th the user removed the app. Duda won't renew the subscription on the coming renewal date of January 10th, 2020 and won't refund the user for the period of February 16th, 2019 - January 9th, 2020.

### Getting subscription details

Duda sends apps events on subscription creation and changes. You can persist these events to track your app's subscriptions and forecast revenues.

{% hint style="info" %}
**Good to know:** Read more on setting up plans for you app on the [App Plans and Upgrades](plans-and-upgrades.md) page.
{% endhint %}

### App installation

When apps are installed, the details of the subscription are included in the Installation Callback send by Duda to your app:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "auth": {
        "type": "bearer",
        "authorization_code": "XXX-XXXXX-XXXXX",
        "refresh_token": "YYY-YYYYY-YYYYY",
        "expiration_date": 1554254560438
    },
    "api_endpoint": "https://api-sandbox.duda.co",
    "installer_account_uuid": "10",
    "account_owner_uuid": "12",
    "user_lang": "en",
    "app_plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
    "recurrency": "MONTHLY",
    "site_name": "1501ccca016a4220861ef07fe2c8eb0d",
    "free": true
}
```
{% endtab %}
{% endtabs %}

_app\_plan\_uuid_ notes the plan selected by the user. _recurrency_ notes if the subscription is monthly or annual.\
Note that installations with a free plan won't include the _recurrency_ attribute.

### Upgrade/Downgrade

When apps are upgraded or downgraded, the details of the subscription are included in the Upgrade Callback send by Duda to your app:

{% tabs %}
{% tab title="JSON" %}
```json
{
    "app_plan_uuid": "paln_uuid",
    "recurrency": "MONTHLY",
    "site_name": "1501ccca016a4220861ef07fe2c8eb0d"
}
```
{% endtab %}
{% endtabs %}

_app\_plan\_uuid_ notes the plan selected by the user. _recurrency_ notes if the subscription is monthly or annual.

### Ending the subscription

When paid apps are uninstalled, Duda sends an Uninstall Callback to your app:

JSON

```json
{"site_name":"1501ccca016a4220861ef07fe2c8eb0d","free":false}
```

As noted on the [do not renew](payments-for-apps.md) section, you should expect to be paid until the end of the subscription.

{% hint style="warning" %}
**Heads up: Downgrade to a free plan**

Duda currently does not support downgrading from a paid plan to a free plan.\
Users can uninstall a paid app and reinstall it again with a free plan to achieve a similar result.
{% endhint %}

### Billing when users are switching between plans

Users may switch plans before the subscription is renewed.\
In case the user moves to a plan with a higher price Duda will _prorate_ payments, meaning Duda will take the unused funds as partial payment for the new subscription. See the following examples:

### Monthly proration

1. The user purchased a monthly subscription with a price of $10/month on January 10th. The user is billed for $10.
2. On February 10th the subscription was renewed. The user is billed for $10.
3. On February 15th the user switched to a $15/month subscription.
4. Duda cancels the previous subscription and creates a new $15/month subscription that renews on the 15th of each month.
5. Duda uses the $8.06 unused funds ($10 \* 25 unused days between February 15th - March 10th / 31 days of the subscription), as the user already committed to paying these funds on the day of the $10/month subscription renewal.
6. On February 15th, the user is billed for $6.84 for the period February 15th - March 14th ($15 - $8.06).
7. On March 15th, the user is billed for $15 for the period March 15th - April 14th, and so on.

### Monthly to annual proration

1. The user purchased a monthly subscription with a price of $10/month on January 10th, 2019. The user is billed for $10.
2. On February 10th the subscription was renewed. The user is billed for $10.
3. On February 15th the user switched to an annual $100/year subscription.
4. Duda cancels the previous subscription and creates a new $100/year subscription that renews on February 15th of each year.
5. Duda uses the $8.06 unused funds ($10 \* 25 unused days between February 15th - March 10th / 31 days of the subscription), as the user already committed to paying these funds on the day of the $10/month subscription renewal.
6. On February 15th, the user is billed for $91.84 for the period February 15th, 2019 - February 14th, 2020 ($100 - $8.06).
7. On February 15th, 2020, the user is billed for $100 for the period February 15th, 2020 - February 14th, 2021, and so on.

### Annual proration

1. The user purchased an annual subscription with a price of $100/year on January 10th, 2019. The user is billed for $100.
2. On February 15th the user switched to an annual $150/year subscription.
3. Duda cancels the previous subscription and creates a new $150/year subscription that renews on February 15th of each year.
4. Duda uses the $87.39 unused funds ($100 \* 319 unused days between February 15th, 2019 - February 14th, 2020 / 365 days of the subscription), as the user already committed to paying these funds on the creation day of the $100/year subscription renewal.
5. On February 15th, the user is billed for $62.60 for the period February 15th, 2019 - February 14th, 2020 ($150 - $87.39).
6. On February 15th, 2020, the user is billed for $150 for the period February 15th, 2020 - February 14th, 2021, and so on.

{% hint style="info" %}
**Good to know: When to expect prorations?**

The month in which prorated payments will be paid by Duda to app partners is dependant on the exact day of the month Duda collects payments from clients. Thus, you may receive the prorated payment in later months.
{% endhint %}

{% hint style="info" %}
**Good to know:** Only upgrades are prorated

Currently, the App Store UI does not support downgrades. However, uninstalling a paid app and reinstalling it soon after with a lower-priced plan would result in a de-facto downgrade.\
When users switch from a higher-priced plan to a lower-priced plan, the unused funds are not counted toward the purchase of the new subscription.\
For example, a user who purchased a $150/year subscription in January 2019 and switches to a $100/year subscription in December 2019 will be billed with $100 for the period of December 2019 - December 2020 on the day of changing plans. Duda won't prorate the unused $12.5.
{% endhint %}
