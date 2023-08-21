# How to Set Up the Simple Editor

The Simple Editor empowers your customers to independently create beautiful websites in minutes, without advanced technological or design skills required. The flow offers customizable templates and sections that can be populated with your customers’ data and content. This guide walks you through how to set up the Simple Editor for your customers.

{% hint style="warning" %}
**Heads up:** This is a paid feature available for Managed plans. To upgrade your plan or purchase the Simple Editor, [schedule time with our team](https://www.duda.co/contact).
{% endhint %}

To work with this guide, make sure you have the following items ready:

* Your Duda API credentials
* Access to the Duda dashboard
* Familiarity with using the Duda API to create a website. To learn more, see the [Do It Yourself guide](do-it-yourself.md).

### 1. Create New Website

You need to create a new website before your customers can access the platform. To create a new website, use the [POST /sites/multiscreen/create](../../reference/partner-api-reference/sites.md#create-site-1) API endpoint. When creating a website, you are required to pass a `template_id` parameter. This lets Duda know which template to create the site from. A default `template_id` can be provided which you can change later. For this example, we are using the ‘Blank Side Bar Template’ which has a `template_id` of 1027437.

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST -i https://api.duda.co/api/sites/multiscreen/create \
    -u 'APIusername:APIpassword' \
    -H 'Content-Type: application/json' \
    -d '{"template_id": "1027437"}'
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
```javascript
{
    "site_name":"28e1182c"
}
```
{% endtab %}
{% endtabs %}

### 2. Create Customer Account

After creating the website, you need to create a customer account to access the website. The customer account represents the customer who owns the website. To create a customer account, use the [POST /accounts/create](../../reference/partner-api-reference/accounts.md#create-account-1) API endpoint.

When creating the customer account, the only required field is `account_name`. This is a unique identifier across your Duda account. It can be an email address, but it doesn't have to be. If you do not have a real identifier for the customer, you can use a random string as the `account_name` and then change it later. This ensures that the user you create is unique among others in the account.

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

### 3. Grant Customer Access

After you create a website and customer account, you need to give the customer account access to the website and set permissions for which actions they can take and which parts of the platform they have access to. To grant access, use the [POST /accounts/{account\_name}/sites/{site\_name}/permissions](../../reference/partner-api-reference/client-permissions.md#grant-site-access-1) API endpoint. You need to grant the customer account edit, reset, publish, and republish permissions.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/accounts/tmp_5903a16748c8c_1493410151/sites/28e1182c/permissions \
-d '{"permissions":["REPUBLISH","RESET","EDIT","PUBLISH"]}'
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
    "REPUBLISH",
    "EDIT",
    "PUBLISH"
  ]
})
 .catch((err) => console.error(err));
```
{% endtab %}
{% endtabs %}

### 4. Set Plan ID

You need to set the `plan ID` for the website to help you differentiate between websites built using the standard editor and websites built using the Simple Editor. This allows you to keep track of the products your customers are using so that you can bill them accordingly. To set the `plan ID`, use the [POST sites/multiscreen/{site\_name}/plan/{plan\_id}](../../reference/partner-api-reference/site-plans.md#update-site-plan-1) API endpoint.

If you do not have a custom Plan ID, contact your Account Manager and they will generate one for you.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/sites/multiscreen/{site_name}/plan/{plan_id} \
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know: Optional Step**

If you already have your clients' data stored, you can use the [Update Content Library API endpoint](../../reference/partner-api-reference/site-content.md#update-content-library-1) to push their data into the Simple Editor site. If you do this before sending your customer into the Simple Editor flow, their data will be prepopulated in the onboarding fields when they begin the website building process. The customer can edit or remove the prepopulated data at any time.
{% endhint %}

### 5. Generate SSO Link

You need to generate a SSO link for the customer account to log into the Simple Editor. To generate a SSO link, use the [GET /accounts/sso/{account\_name}/link](../../reference/partner-api-reference/authentication.md#get-sso-link-1) API endpoint with `RESET_BASIC` as the target. The generated SSO link takes the customer to the onboarding flow.

You can also use this endpoint to generate a SSO link for existing customers with sites. When making the call, make sure to use an account name and a site assigned to that customer account in your parameters.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \ 
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/accounts/sso/tmp_5903a16748c8c_1493410151/link?target=RESET_BASIC&site_name=28e1182c
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
  target: 'RESET_BASIC'
})
 .then((resp) => console.log(resp.url))
 .catch((err) => console.error(err));
```
{% endtab %}
{% endtabs %}

Once your customer receives their SSO link, they can use it to access the Simple Editor where they will be prompted to begin the website building process.
