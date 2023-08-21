# How to Setup Pages for Content Injection

In this article, you will learn how to set up a page to inject content into using Duda's API. To do this, you will update the innerHTML, add a custom DOM attribute, and change a style property.

**NOTE**: You can use an existing site to follow along or create a site using the same template "Online Education" (1202068).

{% hint style="warning" %}
**Heads up: Content Injection is recommended for sites that will not be updated in the editor**

Once widgets are updated in the editor, the content injection tags are removed from the element and cannot be updated via API.
{% endhint %}

### Prerequisites

* API credentials
* Access to Developer Mode
* Familiarity with HTML

### 1. Access Developer Mode for the site

Log into the Duda web interface and access developer mode for the site you're working on.

<figure><img src="https://files.readme.io/717eda6-access-developer-mode.gif" alt=""><figcaption></figcaption></figure>

### 2. Add the `data-inject` attribute to target elements

Specify an identifier in the `data-inject` attribute for each target element. The below code sample uses `title` and `subtitle` for the identifiers.

{% tabs %}
{% tab title="HTML" %}
```html
<h1 class="m-text-align-left" style="letter-spacing: initial;" localization_key="templates.custom.b3duQNe.33">
  <!-- set 'title' as the data-inject value -->
  <span data-inject="title" style="display: initial;" no_space_b="true" no_space_e="true">
    Start your career with a leap
    <br/>
  </span>
</h1>

<p class="m-text-align-left" no_space_b="true" no_space_e="true" localization_key="templates.custom.OUuWUgS.34">
  <!-- set 'subtitle' as the data-inject value  -->
  <span data-inject="subtitle" style="display: initial; color: rgb(255, 255, 255);" no_space_b="true" no_space_e="true">
    Want your future to start right now? We've got the tools to make it happen. Real skills for real jobs.&nbsp;
  </span>
</p>
```
{% endtab %}
{% endtabs %}

### 3. Call the Content Injection API to update the target element(s)

Now that you have a couple of elements set up with the `data-inject` attribute, you can call the Content Injection API to update the target element(s).

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
  body: JSON.stringify(updates), // see the 'Updates' tab for the data structure
}

// lastly, we're invoking fetch with the Content Injection endpoint and request options
fetch("https://api.duda.co/api/sites/multiscreen/inject-content/{site_name}", options);
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'username',
  pass: 'password'
});

duda.content.injectedContent.create({
  site_name: 'site-name',
  raw_body: updates
});
```
{% endtab %}

{% tab title="Updates" %}
```javascript
const updates = [
  {
    "type": "INNERHTML",
    "key": "title",
    "value": "Leap into your next career"
  },
  {
    "type": "INNERHTML",
    "key": "subtitle",
    "value": "Are you looking to jump into a new industry? Watch our courses to learn the skills required to do so."
  },
  {
    "type": "DOMATTR",
    "key": "title",
    "value": "title-custom-value",
    "refs": [
      "data-custom"
    ]
  },
  {
    "type": "DOMATTR",
    "key": "subtitle",
    "value": "subtitle-custom-value",
    "refs": [
      "data-custom"
    ]
  },
  {
    "type": "CSS",
    "key": "title",
    "value": "red",
    "refs": [
      "color"
    ],
    "important": true
  },
  {
    "type": "CSS",
    "key": "subtitle",
    "value": "red",
    "refs": [
      "color"
    ],
    "important": true
  }
]
```
{% endtab %}
{% endtabs %}

### 4. Publish the site to apply the Content Injection updates

Publish (or republish) the site to apply the Content Injection updates.

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
  }
}

// lastly, we're invoking fetch with the Publish Site endpoint and request options
fetch("https://api.duda.co/api/sites/multiscreen/publish/{site_name}", options);
```
{% endtab %}

{% tab title="Node SDK" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: 'username',
  pass: 'password'
});

duda.sites.publish({
  site_name: 'site-name'
});
```
{% endtab %}
{% endtabs %}

**Before**

<figure><img src="https://files.readme.io/b65171a-before-updates.png" alt=""><figcaption></figcaption></figure>

**After**

<figure><img src="https://files.readme.io/fe2bc1c-after-updates.png" alt=""><figcaption></figcaption></figure>

That's it! You successfully set up a couple of elements for content injection and applied updates to them via Duda's Content Injection API. All using Duda's Partner API and a few blocks of JavaScript.
