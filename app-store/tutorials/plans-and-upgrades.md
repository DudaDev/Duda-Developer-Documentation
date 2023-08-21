# Plans and Upgrades

A plan relates to the features you deliver to a customer. Plans can be connected to a paid subscription. Every App must have at least one plan, even if it is not a paid application (free). In most cases, when users install an application, they're prompted to select a plan before starting the install. The selected plan is passed along as part of the [installation callback](lifecycle-events.md).

## Subscriptions & Plans

Duda supports a linear plan structure with subscriptions. This means that apps can only have a single active subscription and plan at a time. Users can upgrade to plans when they need to access features that are not available on the current plan.

### Plans basics

1. Each app must have plan(s) in order to be installed on a site.
2. Each installation must include an active plan.
3. Plans can be free, trial, or paid.
4. [Free-trial](plans-and-upgrades.md#setting-up-a-free-trial) plans are supported on the provider side.
5. Duda supports a linear plan structure:
6. Each plan has a grade, an integer.
7. Users can upgrade from the active plan to plans with higher grade.
8. Downgrades are currently not supported.

### Defining plans in the manifest

Plans are defined in the app manifest, under the `app_plans` property, using the following format:

{% tabs %}
{% tab title="JSON" %}
```json
"app_plans": [
        {
            "plan_uuid": "332653a3-df51-45ce-a873-fbb0b1ccb49f",
            "plan_type": "FREE",
            "is_hidden": false,
            "plan_grade": 0,
            "plan_profiles": {
                "en": {
                    "plan_name": "First",
                    "plan_subtitle": "Start...",
                    "plan_features": [
                        "My first feature",
                        "<strong>My best feature</strong>",
                        "another feature"
                    ]
                }
            }
        },
        {
            "plan_uuid": "bd50e369-e7d4-4246-83d4-e190038e7f07",
            "plan_type": "PAID",
            "is_hidden": false,
            "plan_grade": 1,
            "plan_profiles": {
                "en": {
                    "plan_name": "Second",
                    "plan_subtitle": "...Finish",
                    "plan_features": [
                        "My first feature",
                        "<strong>My best feature</strong>",
                        "another feature"
                    ]
                }
            }
        }
    ]
```
{% endtab %}
{% endtabs %}

### Plan properties

Below is a list of each property of the plan's manifest configuration.

{% hint style="warning" %}
**Heads up: Localizing plans**

Please pay attention to localizing the profiles of plans. This is required to facilitate the wide adoption of your app.
{% endhint %}

<table><thead><tr><th width="330">Property</th><th width="162.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>app_plans</strong></td><td>a<em>rray of objects</em></td><td>The entire object that contains details of the App Plans available. Each object in the array is a specific plan.</td></tr><tr><td><strong>app_plans[x].plan_uuid</strong></td><td><em>string</em></td><td>A Duda platform wide global identifier for the plan. Plan UUIDs are immutable and generated by Duda.</td></tr><tr><td><strong>app_plans[x].plan_type</strong></td><td><em>enum</em></td><td>Specifies the plan type. Can be either FREE, TRIAL or PAID.</td></tr><tr><td><strong>app_plans[x].is_hidden</strong></td><td><em>bool</em></td><td>The plan is not presented to the user on the plans selection page during install and upgrade flows. Hidden plans are presented as part of the app info under the 'learn more' link in the App Store. The only way to sell this plan is by upgrading to it through the upgrade process <a href="https://developer.duda.co/docs/app-plans-and-upgrades#section-upgrade-flow">triggered by your App</a>.</td></tr><tr><td><strong>app_plans[x].is_default</strong></td><td><em>bool</em></td><td>Default plans will be installed automatically once the user confirm to install the app. Duda will bypass the plan selection screen. Default plans must be free. App cannot have more then one default plan.</td></tr><tr><td><strong>app_plans[x].plan_grade</strong></td><td><em>int</em></td><td>The logical order in which plans should be displayed. 0 should be your lowest plan, with it incrementing up for each plan higher that you sell.</td></tr><tr><td><strong>app_plans[x].plan_profiles</strong></td><td><em>string-object</em></td><td>For each language your application supports, you should fill out the plan profile to correspond with that language.</td></tr><tr><td><strong>app_plans[x].plan_profiles["lang"]</strong><br><strong>.plan_name</strong></td><td><em>string</em></td><td>The unique name of the plan. This will be displayed to users in the UI.</td></tr><tr><td><strong>app_plans[x].plan_profiles["lang"]</strong><br><strong>.plan_subtitle</strong></td><td><em>string</em></td><td>A short description of the plan. For example, who it's good for or what benefit it gives the most.</td></tr><tr><td><strong>app_plans[x].plan_profiles["lang"]</strong><br><strong>.plan_features</strong></td><td><em>array of strings</em></td><td>A bullet point list of features which are available in that plan.</td></tr></tbody></table>

### Configuring your plans

Not every part of the manifest plan data can be updated by you. This is because, on the Duda side, there are many steps we need to go through in order to set up plans and contracts for selling. Please contact us if you need changes or new plans added.

### Supported updates

App partners can do the following by updating the app's manifest:

* Add/delete localized plan profile
* Edit the localized plan profiles
* Change the `is_defualt`, and `is_hidden` flags
* Change the grades
* Change `plan_type` from FREE to TRIAL

### Unsupported updates

The following cannot be done by app providers:

* Add/delete plans
* Change plan UUID
* Set plan price
* Change `plan_type` from FREE or TRIAL to PAID

The above actions can be done only by Duda's team.

## Initiating the upgrade flow

The flow of upgrading the active plan of an app can start in several ways.

### The user clicks 'upgrade' on the App Store

When the user clicks on _upgrade_ button in the App Store the upgrade flow will start. Duda will present the user a selection screen with all plans with higher grades that are not flagged as _hidden_.

### From the app's iframe via post message

When your app is open within Duda, as an iframe you can send a [postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) from your child frame to the Duda parent.

Duda provides a simple JS SDK/Library for you to use which adds a simple function call to start the upgrade. The URL for this Library is passed as a URL on the [SSO to open your app](../concepts/single-sign-on.md). We recommend relying on this URL to embed the JS library, as we'll update it as we add new options in the future.

To initiate the upgrade flow via Post Message:

1. Embed the JS SDK in your application page. Duda passes the source of this file as the iframeSDKSrc. [Here's an example of it.](https://sandbox-ms-cdn.multiscreensite.com/integrationhub/1027/res/sdk/iframe.js)
2. Run the function `_dAPI.upgrade({planData})`, where `planData` is an object containing configuration for the upgrade flow: `appId` with your app UUID, `type` of `upgradeApp`
3. You can control the plans the user would see by adding optional parameters:
4. `planId` with the UUID of the requested plan: the user will be presented only with that plan. It can be a hidden plan.
5. `plansList` with an array of plan UUIDs: the user will be present with the plans passed in the array, including hidden plans passed on the list..
6. If you don't specify `planId` or `plansList`, the user will be presented with the [default plan selection screen](plans-and-upgrades.md).

#### Embedding the SDK

Using the SDK path passed in the SSO link.

{% tabs %}
{% tab title="HTML" %}
```html
<script src={{SDK path sent in the SSO link}}"></script>
```
{% endtab %}
{% endtabs %}

#### Presenting a specific plan

{% tabs %}
{% tab title="JavaScript" %}
```javascript
let dudaUpgradeConfig = {
  type: 'upgradeApp',
  appId: 'myApp',
  planId: '4725fcf8-1256-4d5c-803c-69385b565ced'
};
```
{% endtab %}
{% endtabs %}

#### Presenting several plans from a list

{% tabs %}
{% tab title="JavaScript" %}
```javascript
let dudaUpgradeConfig = {
  type: 'upgradeApp',
  appId: 'myApp',
  plansList: ['4725fcf8-1256-4d5c-803c-69385b565ced','58b18228-6f9e-4942-bfb5-1d3a06981ce9']
};
```
{% endtab %}
{% endtabs %}

### Using a deep link

The following deep links will initiate the upgrade flow:

1. No plan specified:\
   https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}\&upgrade=true
2. With a specific plan:\
   https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}\&upgrade=true\&planId={plan\_uuid}

See [deep links](../reference/deep-links.md) guide.

### Upgrade flow UI

{% hint style="info" %}
**Good to know: Who can upgrade?**

Duda's users are divided into two groups:

1. Staff: web pros who work for web agencies. Also known as _Duda aware_ users.
2. Clients: the owners of the websites.

_**Clients are never presented with prices nor asked to confirm payments.**_\
Therefore, when clients start the upgrade flow, Duda would present them with a 'contact your site admin' message.
{% endhint %}

1. The upgrade flow starts with Duda presenting the user with a plan selection screen. In case no plan was specified by the upgrade-flow initiator, Duda will present all plans with higher grades that are not flagged as _hidden_. Duda will also present the active plan as non-selectable to allow the user to compare features.
2. Depending on the account type, the user is asked to provide/confirm payment details.
3. Duda presents the user with a progress bar. Meanwhile, Duda sends the app an upgrade callback and waits for a 200 HTTP status code.
4. Once a 200 response is received, Duda opens the app iframe and directs the user.

### Handling upgrade callbacks

Duda sends a callback of the following format to the `updowngrade_installation_endpoint` listed in the manifest:

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

Duda then waits for the endpoint to respond with a 200 HTTP status code.\
As with the installation process, the app can use site-REST API to get information and perform actions while Duda waits for the response.

### Setting up a free trial

Duda supports either a free trial or free version of your application. On the Duda side, these are the same mechanism that allows for the free install. If you want to implement a free trial, you will need to lock access to your application after X days (14, 30, etc..) and force the user to upgrade to a higher plan before they get access.

To display a trial plan you should set `plan_type` to TRIAL with grade 0 and set the `default_plan_uuid` property of the manifest to this plan. When installing the app via the UI, Duda will not preset the user with a plan selection screen and install the app with the default plan.