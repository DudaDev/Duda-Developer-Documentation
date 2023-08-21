# Do It Yourself

Do-it-yourself (DIY) flows allow customers to start at your website and proceed directly into your white labeled Duda portal. The goal is to enable users to start building a website, without need for service providers to enable any type of access for themselves. Customers will then use the Duda editor to build their own website.

Duda can support several different types of flows, such as freemium (where users can access the website builder without paying), paid flows and more. This guide will walk through a freemium style flow, where users will be able to access the website builder without registering for an account.

{% hint style="warning" %}
**Heads up: Custom plans only**

This example uses the Single Sign-on feature, which is only available to custom plan accounts.
{% endhint %}

### Requirements

To work with this guide, you’ll need to make sure you have the following items ready:

* Your Duda [API credentials](../../#api-credentials)
* Access to the Duda dashboard
* PHP development environment. Our examples are given in PHP although any language can be used.

{% hint style="info" %}
**Good to know:** The full PHP code from this guide is available [here](https://du-cdn.multiscreensite.com/duda\_website/img/developers/DIY-Fremium-Full-and-Steps.zip).
{% endhint %}

### 1. Create New Site

A website is required to be created before a user can access the platform. When creating a website, you are required to pass a `template_id` parameter. This lets Duda know which template to start the site from. A default template\_id can be provided which the user can change later . In this case, we will start from the ‘Blank Side Bar Template’ which has a template\_id of 1027437.

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST -i https://api.duda.co/api/sites/multiscreen/create \
    -u 'APIusername:APIpassword' \
    -H 'Content-Type: application/json' \
    -d '{ "template_id": "1027437"}'
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda(
  user: 'api-user',
  pass: 'api-pass'
);

duda.sites.create({ 
  template_id: "1027437" 
})
 .then((resp) => console.log(resp.site_name))
 .catch((err) => console.error(err));
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "site_name":"28e1182c"
}
```
{% endtab %}
{% endtabs %}

Learn more about the [POST /sites/multiscreen/create](../../reference/partner-api-reference/sites.md#create-site-1) API endpoint.

### 2. Create Customer Account

After creating the website, our next step is creating an account to access the site. Accounts represent the customer who owns the site. When creating an account the only required field is `account_name`. This is a unique identifier across your Duda account. It can be an email address, but doesn't have to.

Since we might not know a real identifier for this customer, we use a random string as the account\_name. This can be changed later. This ensures that the user we are creating is unique among others in the account.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' -H 'Content-Type: application/json' \
-X POST -i -k https://api.duda.co/api/accounts/create \
-d '{"account_name":"tmp_5903a16748c8c_1493410151"}'
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda(
  user: 'api-user',
  pass: 'api-pass'
);

duda.accounts.create({ 
  account_name: "tmp_5903a16748c8c_1493410151" 
})
 .catch((err) => console.error(err));
```
{% endtab %}
{% endtabs %}

Learn more about the [POST /accounts/create](../../reference/partner-api-reference/accounts.md#create-account-1) API endpoint.

### 3. Grant Access

After we’ve created a website and account, we need to give the customer access to the newly created website. As part of the granting access, we need to set which permissions the user will have access to. You can use this feature to decide which parts of the platform a user should have access to. In the example below, we exclude Developer Mode, eCommerce and Backups from the customer.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/accounts/tmp_5903a16748c8c_1493410151/sites/28e1182c/permissions \
-d '{"permissions":["PUSH_NOTIFICATIONS","REPUBLISH","EDIT","INSITE","PUBLISH","CUSTOM_DOMAIN","RESET","SEO","STATS_TAB","BLOG"]}'
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda(
  user: 'api-user',
  pass: 'api-pass'
);

duda.accounts.permissions.grantSiteAccess({
  account_name: 'tmp_5903a16748c8c_1493410151',
  site_name: '28e1182c',
  permissions:[
    "PUSH_NOTIFICATIONS",
    "REPUBLISH",
    "EDIT",
    "INSITE",
    "PUBLISH",
    "CUSTOM_DOMAIN",
    "RESET",
    "SEO",
    "STATS_TAB",
    "BLOG"
  ]
})
 .catch((err) => console.error(err));
```
{% endtab %}
{% endtabs %}

Learn more about the [POST /accounts/{account\_name}/sites/{site\_name}/permissions](../../reference/partner-api-reference/client-permissions.md#grant-site-access-1) API endpoint.

### 4. Log Customer into Editor

Now that the customer account has access to the new site, we can get the user started. We will generate a SSO link and redirect the user to this link which will send them into the Duda editor. This will allow us to send the user to the template selection page and get started.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \ 
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/accounts/sso/tmp_5903a16748c8c_1493410151/link?target=SWITCH_TEMPLATE&site_name=28e1182c
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda(
  user: 'api-user',
  pass: 'api-pass'
);

duda.accounts.authentication.getSSOLink({ 
  account_name: 'tmp_5903a16748c8c_1493410151',
  site_name: '28e1182c',
  target: 'RESET_SITE'
})
 .then((resp) => console.log(resp.url))
 .catch((err) => console.error(err));
```
{% endtab %}

{% tab title="Response" %}
```json
{  
  "url": "http://example.mobilewebsiteserver.com/home/site/146856ab?dm_sso=2!eyJyZXFVdWlkIjoiYzU0Y2E0MzYwNDA2NDgwZDlmZmM2MTIxY2FiOTM2MzAifQ"
}
```
{% endtab %}
{% endtabs %}

Learn more about the [GET /accounts/sso/{account\_name}/link](../../reference/partner-api-reference/authentication.md#get-sso-link-1) API endpoint.

{% hint style="info" %}
**Good to know: SSO - Target**

In our example we provide a target of `SWITCH_TEMPLATE` when generating the SSO link. This sends the user to the template selection page. If the template\_id provided in Step 1 should not be changed, then the target parameter can be removed to send the user directly to the editor.
{% endhint %}
