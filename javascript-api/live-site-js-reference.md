# Live Site JS Reference

### runOnReady

Run code once a page has been fully loaded. By default, Duda websites use AJAX/Animated navigation to change pages. This means that there is no [DOM ready event](https://developer.mozilla.org/en/docs/Web/Events/DOMContentLoaded) when a user browses to a new page of the website. Using this lets you know once the user has either loaded the page fully for the first time or browses to a new page of the website.

{% tabs %}
{% tab title="Example" %}
```javascript
<script>
dmAPI.runOnReady('nameSpace',callbackFn)
</script>
```
{% endtab %}

{% tab title="Example with Arguments" %}
```javascript
<script>
//listen to page load or change and run some code
dmAPI.runOnReady('name',function(){
	//execute some code here
});
</script>
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Argument</th><th width="158">Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>Namespace</strong></td><td>No</td><td>Pass a unique name that won't collide with other runOnReady function calls</td></tr><tr><td><strong>Callback</strong></td><td>No</td><td>Pass a callback function to execute</td></tr></tbody></table>

### loadScript

The best way to load external scripts is through the Duda loadScript function. Using this ensures that the script is loaded asynchronously and the page is ready to handle the script. The script is automatically executed once it's finished. Duda calls the callback function, so any operations you want to take after it is loaded.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
dmAPI.loadScript('https://cdn.jsdelivr.net/npm/typed.js@2.0.9', function() { 
	// run init code after library loads
	var typed = new Typed('.element', {
		strings: ["First sentence.", "Second sentence."],
		typeSpeed: 30
	});
});
</script>
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Argument</th><th width="186">Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>url</strong></td><td>Yes</td><td>A string containing the URL where the JS file lives</td></tr><tr><td><strong>Callback</strong></td><td>No</td><td>Pass a callback function to execute after the script has successfully loaded</td></tr></tbody></table>

### runBeforeAjaxNavigation

Run code once right before a page change is started. Duda uses AJAX to handle page changes on published sites. This method allows you to listen for a page change.

{% tabs %}
{% tab title="Example" %}
```javascript
<script>
dmAPI.runBeforeAjaxNavigation('nameSpace',callbackFn)
</script>
```
{% endtab %}

{% tab title="Example with Arguments" %}
```javascript
<script>
//listen to page change 
dmAPI.runBeforeAjaxNavigation('name',function(){
	//execute some code here
});
</script>
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Argument</th><th width="160">Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>Namespace</strong></td><td>No</td><td>Pass a unique name that won't collide with other runBeforeAjaxNavigation function calls</td></tr><tr><td><strong>Callback</strong></td><td>No</td><td>Pass a callback function to execute</td></tr></tbody></table>

### getSiteName

Get the unique name of the Duda website this code is loading on. This is a unique string that represents a single Duda website. This is usually an 8 or 32 character string.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const siteName = dmAPI.getSiteName();
```
{% endtab %}
{% endtabs %}

### getSiteExternalId

Get the External reference identifier for this website. This is set when the website was created via the API or updated. It is usually an external identifier passed to Duda for integration purposes.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const externalId = dmAPI.getSiteExternalId();
```
{% endtab %}
{% endtabs %}

### getSitePlanID

Get the Duda plan id for the current site.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const planId = dmAPI.getSitePlanID();
```
{% endtab %}
{% endtabs %}

### getCurrentDeviceType

Get the current device type. This function returns `desktop`, `tablet` or `mobile`. The device type detection is done on the server-side via the User-Agent. This always returns the same device type that was detected on the server-side.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const device = dmAPI.getCurrentDeviceType();
```
{% endtab %}
{% endtabs %}

### getNavItems

{% hint style="warning" %}
**Heads up: Deprecated method**

Note, this API is deprecated and will be removed in the near future to improve performance. Use`getNavItemsAsync` to retrieve data on a site's pages in a more performant manner.
{% endhint %}

Returns an array of objects that contains details about the pages of the website. For each page within the website, the following details will be returned.

| Name             | Type     | Description                                                                                                                                                                                           |
| ---------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **title**        | _string_ | The name of the page, as it appears in the navigation list                                                                                                                                            |
| **alias**        | s_tring_ | The internal name of the page. This is unique across the website. It also correlates with the page name in the path                                                                                   |
| **path**         | _string_ | The relative path to the page                                                                                                                                                                         |
| **inNavigation** | _bool_   | If the page is visible to the user. This correlates to the hide page feature in the page settings. Note that this value is respective to the device, so it can be false on desktop and true on mobile |
| **subNav**       | _array_  | An array of nested pages following the same structure. A Duda website can have up to two layers of sub nav. (For a total of 3 layers deep)                                                            |

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
// DEPRECATED - Use getNavItemsAsync
// Assign to nav variable
const navLinks = dmAPI.getNavItems();

// loop through each nav item and print to console
navLinks.forEach(function(e) { 
	console.log(e) 
})

// outputs:
// {title: "HOME", alias: "home", path: "/", inNavigation: false, subNav: Array(0)}
// {title: "SERVICES", alias: "services", path: "/services", inNavigation: true, subNav: Array(3)}
// {title: "TEAM", alias: "team", path: "/team", inNavigation: true, subNav: Array(0)}
// {title: "PRODUCTS", alias: "products", path: "/products", inNavigation: true, subNav: Array(0)}
// {title: "GALLERY", alias: "gallery", path: "/gallery", inNavigation: true, subNav: Array(0)}
// {title: "CONTACT", alias: "contact", path: "/contact", inNavigation: true, subNav: Array(0)}
</script>
```
{% endtab %}
{% endtabs %}

### getNavItemsAsync

This method returns a promise and once resolved, returns an array of objects that contains details about the pages of the website. For each page within the website, the following details will be returned.

| Name        | Type     | Description                                                                                                                                                                                           |
| ----------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **title**   | _string_ | The name of the page, as it appears in the navigation list                                                                                                                                            |
| **alias**   | _string_ | The internal name of the page. This is unique across the website. It also correlates with the page name in the path                                                                                   |
| **uuid**    | _string_ | The internal unique identifier of a specific page. This value is used to update or delete a page using the [pages REST API](../reference/partner-api-reference/pages-v2.md) endpoints.                |
| **path**    | _string_ | The relative path to the page                                                                                                                                                                         |
| **visible** | _bool_   | If the page is visible to the user. This correlates to the hide page feature in the page settings. Note that this value is respective to the device, so it can be false on desktop and true on mobile |
| **subNav**  | _array_  | An array of nested pages following the same structure. A Duda website can have up to two layers of sub nav. (For a total of 3 layers deep)                                                            |

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
// Assign to nav variable
const navLinks = dmAPI.getNavItemsAsync();

// Resolve promise and print to console
navLinks.then((value) => {
  console.log(value);
});

// outputs:
// {title: "HOME", alias: "home", path: "/", inNavigation: false, subNav: Array(0)}
// {title: "SERVICES", alias: "services", path: "/services", inNavigation: true, subNav: Array(3)}
// {title: "TEAM", alias: "team", path: "/team", inNavigation: true, subNav: Array(0)}
// {title: "PRODUCTS", alias: "products", path: "/products", inNavigation: true, subNav: Array(0)}
// {title: "GALLERY", alias: "gallery", path: "/gallery", inNavigation: true, subNav: Array(0)}
// {title: "CONTACT", alias: "contact", path: "/contact", inNavigation: true, subNav: Array(0)}
</script>
```
{% endtab %}
{% endtabs %}

### getCollection

Get data for a given collection on the website. The collection must already exist and the website must be published with it.

{% hint style="warning" %}
**Heads up: Deprecated method**

Note, this API is deprecated and we recommend relying on the [Collections API](collections-js-api.md).
{% endhint %}

{% tabs %}
{% tab title="JavaScript" %}
```javascript
dmAPI.getCollection({collectionName: 'employees'}).then(
	function(data){ 
    console.log(data); 
  }
)

// returns an array of objects from the employees collection. 
// an empty array is returned if an invalid collection is passed
```
{% endtab %}
{% endtabs %}

### drawMap

Use Duda's built in map tool to create a map element. This uses [Duda's integration with Mapbox](https://www.duda.co/blog/duda-adds-new-mapbox-integration-to-its-platform/) to draw a map with a pinned location. When you call the `drawMap` function, you pass a selector. Duda replaces all the inner contents of that element with the map. You also need to pass the latitude and longitude coordinates or an address string.

{% tabs %}
{% tab title="HTML" %}
```html
<script> 
  
// passing address
dmAPI.drawMap(
  {
    container: '.selector' , 
    addressQuery: '577 College Ave., Palo Alto, CA'
  }
); 

// passing latitude + longitude coordinates
dmAPI.drawMap(
  {
    container: '.selector' , 
    lat: 37.4252935, 
    lng: -122.1504151
  }
);

</script>
```
{% endtab %}
{% endtabs %}

### getOpimizedImageURL

Returns a URL to a resized image based on user device or an optional width argument. The original image must be stored in Duda. If the image format is not recognized, the method returna the original URL. This can be used in conjunction with a [custom widget](../custom-widgets/reference/javascript.md) to display appropriately sized images.

{% tabs %}
{% tab title="Javascript" %}
```javascript
<script>
  // return a 500px wide image
  dmAPI.getOptimizedImageURL('<IMAGE_URL>', 500);

	// return a resized image based on user device
	// Mobile: 640px, Tablet: 1280px, Desktop: 1920px
	dmAPI.getOptimizedImageURL('<IMAGE_URL>');

  // usage within a custom widget
  // data and element variables are
  // provided by the widget builder

  data.config.list.forEach(item => {
    var imgsrc = dmAPI.getResizedImageURL(item.image);
    var elem = document.createElement("img");
    elem.setAttribute("src", imgsrc);
    element.appendChild(elem);
  });
</script>
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:** Using the standard device sizes results in a slight performance boost. Specifying a specific width results in images being resized at request time, while the standard sizes are created and saved when the image is added via the API or editor.
{% endhint %}

### subscribeEvent

Subscribe to specific conversion focused events that happen within the website. This allows you to execute a callback function when a conversion event happens. This API is usually combined with custom analytics or tracking solutions that are placed within Duda websites.

Some events pass data into the callback function for you to take further action on.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
//subscribe to form submit event
dmAPI.subscribeEvent(dmAPI.EVENTS.FORM_SUBMISSION, function(data) {
	console.log("Form data is: " + data);
});
</script>
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Argument</th><th width="159">Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>Event Name</strong></td><td>Yes</td><td>Event name (ex. <code>dmAPI.MAP_BUTTON_CLICK</code>)</td></tr><tr><td><strong>Callback</strong></td><td>No</td><td>Pass a callback function to execute</td></tr></tbody></table>

Description of events:

<table><thead><tr><th width="232">Event</th><th width="236">Data provided to Callback</th><th>Description</th></tr></thead><tbody><tr><td><strong>FORM_SUBMISSION</strong></td><td>Object with form data in key-value form</td><td>When a Duda contact form is submitted on the website</td></tr><tr><td><strong>CLICK_TO_CALL</strong></td><td>(none)</td><td>Click to call button is clicked</td></tr><tr><td><strong>EMAIL_BUTTON_CLICK</strong></td><td>(none)</td><td>Click to email button is clicked</td></tr><tr><td><strong>MAP_BUTTON_CLICK</strong></td><td>(none)</td><td>Click to map button is clicked</td></tr><tr><td><strong>SHARE_CLICK</strong></td><td>(none)</td><td>Click to share button is clicked</td></tr><tr><td><strong>SOCIAL_LINK</strong></td><td>(none)</td><td>After an icon within the social icons widget is clicked</td></tr><tr><td><strong>OPENTABLE_CLICK</strong></td><td>(none)</td><td>Click to reserve button is clicked</td></tr><tr><td><strong>NOTIFICATION_LINK_CLICK</strong></td><td>(none)</td><td>When a link within the notification bar is clicked</td></tr><tr><td><strong>NOTIFICATION_LINK_CLOSE</strong></td><td>(none)</td><td>When a notification bar is closed (ex. the "x" is clicked)</td></tr><tr><td><strong>COUPON_CLICK</strong></td><td>(none)</td><td>When a coupon is clicked or viewed on the website</td></tr><tr><td><strong>STORE_ORDER</strong></td><td>(none)</td><td>Once a successful purchase happens within an eCommerce store</td></tr><tr><td><strong>SHOW_POPUP</strong></td><td>(none)</td><td>When a pop-up is displayed on a website. Either from a personalization rule or button click</td></tr><tr><td><strong>PERSONALIZATION_RULE_IMPRESSION</strong></td><td>Personalization rule: {ruleId, ruleType}</td><td>When a personalization rule is successfully loaded on a page</td></tr><tr><td><strong>PERSONALIZATION_RULE_LINK_CLICK</strong></td><td>(none)</td><td>Only runs for links clicked within the 'new row' personalization rule</td></tr><tr><td><strong>VIDEO_PLAY</strong></td><td>(none)</td><td>After a video is clicked and starts to play. Works with video uploads, youtube, vimeo and dailymotion.</td></tr><tr><td><strong>WHATSAPP</strong></td><td>(none)</td><td>After WhatsApp click is done.</td></tr></tbody></table>

### subscribeToAllEvents

Subscribe to all the possible site events that can happen. Note that not all events are 'conversion' events, so make sure you only track the events you specifically want to. You can see all the available events above.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
//subscribe to all events
dmAPI.subscribeToAllEvents(function(eventName, data) {
	console.log('Event: ' + eventName  + ' was called');
});
</script>
```
{% endtab %}
{% endtabs %}

### loadCollectionsAPI

Load the collections API to query the data in your collections programmatically. This API has [filtering, pagination, and sorting options](collections-js-api.md).

{% tabs %}
{% tab title="HTML" %}
```html
<script>
//load the collections API
dmAPI.loadCollectionsAPI().then(api => {
	api.data("my-collection")
		.where("field-name", "eq", "some-value")
		.orderBy("other-field-name")
		.pageSize(10)
		.get()
		.then(json => console.log(json))
})
</script>
```
{% endtab %}
{% endtabs %}

### getCurrentEnvironment

Get the current context of where the page is loaded from. Will return a string with three possibilities:

* `live`: This is the live published website.
* `editor`: The website is currently loaded within the editor environment.
* `preview`: The site is being previewed, before being published, but outside of the editor. This is the exact same version of the website as the editor, and, is often treated the same as the editor.\
  This allows you to customize the experience of your custom code. For example, you might want to not run some analytics javascript inside of the editor, but only on the live website.

{% tabs %}
{% tab title="HTML" %}
```html
<script>
const env = dmAPI.getCurrentEnvironment()
if(env === 'live') {
	// run code on the a live website only
  console.log('the site is live!')
}
</script>
```
{% endtab %}
{% endtabs %}

### getLoggedInMember

Get the identity of the currently logged-in member.

If the user is not authenticated as a member API will return a status 401.

{% tabs %}
{% tab title="HTML" %}
```html
<script>
dmAPI.getLoggedInMember().then(result  => {
  //do something with member data
}
</script>
```
{% endtab %}
{% endtabs %}
