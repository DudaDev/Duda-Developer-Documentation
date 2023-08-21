# Upsell + Publish Flows

### Publish and Upsell Flow

While integrating with Duda you may want to upsell more features to your customers, such as publishing the website. Duda supports two scenarios for when you want to offer an upsell option to users:

* Customer is trying to publish a website for the first time.
* Customer is trying to use a feature that is locked.

### Customize Publish Flow

During these scenarios, it is important to make sure that the customer has a smooth and uninterrupted experience while upgrading. Duda offers two methods for doing this:

* Open Lightbox/Iframe
* Redirect users to an external URL

For both options, Duda will append URL parameters that give you additional context about who the user is and what information to pass along.

Under White Label, select _API Access_ and click _Customize publish flow_, then choose the option most appropriate for your workflow.

<figure><img src="https://files.readme.io/a9890e0-Screen_Shot_2022-06-30_at_9.09.28_AM.png" alt=""><figcaption></figcaption></figure>

### Open iframe in a Lightbox (Recommended)

This option will allow you to open a dedicated upgrade page over the website builder that looks like the following:

<figure><img src="https://files.readme.io/56a2459-Screen_Shot_2021-08-11_at_3.17.21_PM.png" alt=""><figcaption></figcaption></figure>

#### Interact with Parent iframe

The page within the iframe can communicate with the Duda editor (parent frame) through simple JavaScript APIs.

To use Duda's JavaScript API, you will need to embed the following script into your upgrade page:

```
<script async src="https://my.duda.co/_dm/s/common/scripts/publishOverlayAPI.js"></script>
```

Once you've embedded this, you'll be able to call the following JavaScript properties:

**Publish Done or Finished**

If using the _Redirect without publishing_ or _iframe without publishing_ options, a site will need to be published via the [API](../../reference/partner-api-reference/sites.md#publish-site-1).

Additionally, you can call this function to tell Duda to refresh the editor. This will update the user with the current status of the website.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
publishOverlayAPI.publishDone()
```
{% endtab %}
{% endtabs %}

**Website Upgrade Complete**

If you upgrade the site plan or permissions via the [API](../../reference/partner-api-reference/site-plans.md#update-site-plan-1) while the user is interacting with the upgrade page, you need to call the upgradeDone() function call to grant the user access to the newest features you've enabled.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
publishOverlayAPI.upgradeDone()
```
{% endtab %}
{% endtabs %}

**Close Overlay**

To close the overlay, you can call the publishOverlayAPI.closeOverlay() function to close the iframe and let the user continue to edit/build their website.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
publishOverlayAPI.closeOverlay()
```
{% endtab %}
{% endtabs %}

### Redirect Upon Publish

Instead of using an iframe, you can redirect users to an external URL that you host.

There are two options for redirecting to an outside URL:

* **Publish and redirect:** When this option is selected, the website publish process will continue and the user will be redirected to your external upgrade flow.
* **Redirect without publishing (most common):** Redirect the user to complete the upgrade/registration and do not publish the website. This will require you to offer the option to publish the website (via the API) for your customers.
