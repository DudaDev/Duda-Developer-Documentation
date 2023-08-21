# How to Grant a User Stats Permission

### Introduction

In this article, we're going to show you how to grant a new user permission to access the stats dashboard. To do this, you will create a new site and a new user. Then, you will grant the new user permission to view the site's stats dashboard. Once that's done, you'll generate an SSO link for the newly created user to log in directly to the stats dashboard.

The code samples below use our [Node Client SDK](../../reference/partner-api-reference/libraries-sdks.md) to perform API calls to the platform.

### Prerequisites

* API Credentials

### 1. Create a New Site

In this step, you're going to [create a new site](../../reference/partner-api-reference/sites.md#create-site-1) for the user to access.

{% tabs %}
{% tab title="Node" %}
```javascript
// we're using the node-fetch package to make http requests
const fetch = require("node-fetch");

// here, we're setting up our request options
const options = {
  method: "POST",
  headers: {
    "Accept": "application/json",
    "Authorization": "Basic " + atob("{username}:{password"),
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    template_id: 1233140, // we're specifying a template id to create the site
  })
}

// lastly, we're invoking fetch with the Create Site endpoint and request options
// we're then assigning the `site_name` property from the response to a `site` variable
const site = fetch("https://api.duda.co/api/sites/multiscreen/create", options)
	.then((response) => {
    return response.site_name;
  });
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'my-api-user',
  pass: 'my-api-pass'
});

// get a list of templates
duda.templates.list()
  .then((templates) => {
  	// return the id of the first template in the array
		return templates[0].template_id;
	})
	.then((template_id) => {
  	// create a new site using the template id
		return duda.sites.create({ template_id });
	})
	.catch((err) => {
  	// handle error
		console.log(err);
	});
```
{% endtab %}

{% tab title="Response" %}
```json
// 200 - Success
{
  "site_name": "146856ab"
}
```
{% endtab %}
{% endtabs %}

### 2. Create a New User

Now that you've created a site, you need to [create a new user](../../reference/partner-api-reference/accounts.md#create-account-1) to grant site permissions to.

{% tabs %}
{% tab title="Node" %}
```javascript
// we're using the node-fetch package to make http requests
const fetch = require("node-fetch");

// here, we're setting up our request options
const options = {
  method: "POST",
  headers: {
    "Accept": "application/json",
    "Authorization": "Basic " + atob("{username}:{password"),
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    account_name: "rickybobby", // the uid for this user
    first_name: "Ricky",
    last_name: "Bobby",
    email: "rbob@duda.co",
    account_type: "CUSTOMER", // sets the user up as a client instead of a team member
  })
}

// lastly, we're invoking fetch with the Create Account endpoint and request options
// the endpoint doesn't return any data, so we're not assigning it to a variable
fetch("https://api.duda.co/api/accounts/create", options);
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'my-api-user',
  pass: 'my-api-pass'
});

const account_name = 'an-account-name';

duda.accounts.create({ account_name })
	.catch((err) => {
		// handle error
  	console.log(err);
	})
```
{% endtab %}

{% tab title="Response" %}
```
// 204 - No Content
```
{% endtab %}
{% endtabs %}

### 3. Grant the Stats Permission

You need to assign the user permission to access the site's stats dashboard. View the full list of available [permissions](../../reference/partner-api-reference/client-permissions.md#list-client-permissions-1).

{% tabs %}
{% tab title="Node" %}
```javascript
// we're using the node-fetch package to make http requests
const fetch = require("node-fetch");

// here, we're setting up our request options
const options = {
  method: "POST",
  headers: {
    "Accept": "application/json",
    "Authorization": "Basic " + atob("{username}:{password"),
    "Content-Type": "application/json",
  },
  body: JSON.stringify([
    "STATS", // we're passing an array of permissions to assign
  ])
}

// lastly, we're invoking fetch with the Grant Permissions endpoint and request options
// the endpoint doesn't return any data, so we're not assigning it to a variable
fetch("https://api.duda.co/api/accounts/rickybobby/sites/" + site + "/permissions", options)
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'my-api-user',
  pass: 'my-api-pass'
});
```
{% endtab %}

{% tab title="Response" %}
```
// 204 - No Content
```
{% endtab %}
{% endtabs %}

### 4. Generate an SSO Link

Lastly, you need to [generate an SSO link](../../reference/partner-api-reference/authentication.md#get-sso-link-1) so that the user you created can log in directly to the site's stats dashboard.

{% tabs %}
{% tab title="Node" %}
```javascript
// we're using the node-fetch package to make http requests
const fetch = require("node-fetch");

// here, we're setting up our request options
const options = {
  method: "GET",
  headers: {
    "Accept": "application/json",
    "Authorization": "Basic " + atob("{username}:{password"),
    "Content-Type": "application/json",
  },
}

// next, we're creating URL parameters to specify the site and page we want to log them into
const params = new URLSearchParams();
params.append("site", site);
params.append("target", "STATS");

// we're then appending the URL parameters to the Get SSO Link endpoint
const url = "https://api.duda.co/api/accounts/sso/rickybobby/link" + params.toString();

// lastly, we're invoking fetch with url we created and request options
// we're logging the URL to the console, but you'll most likely want to email this to the user
fetch(url, options).then((response) => {
  console.log(response.url);
})
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'my-api-user',
  pass: 'my-api-pass'
});
```
{% endtab %}

{% tab title="Response" %}
```json
// 200 - Success

{  
  "url": "http://example.mobilewebsiteserver.com/home/site/146856ab?dm_sso=2!eyJyZXFVdWlkIjoiYzU0Y2E0MzYwNDA2NDgwZDlmZmM2MTIxY2FiOTM2MzAifQ"
}
```
{% endtab %}
{% endtabs %}

### Conclusion

That's it! You successfully created a new site, a user with stats permission, and generated an SSO link for that user to log in directly to the site's stats dashboard. All using Duda's Partner API and a few blocks of JavaScript.
