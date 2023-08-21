# Best Practices

This guide offers _tips_ for using the Duda Widget Builder. It will be best understood if you've used the widget builder previously and understand how it works.

If you have your own tips you've come up with while building widgets and feel others would benefit from them, then offer them up with the Suggested Edits link at the top of the page. We will review them and update this page in the event that is relevant to the community.

### ECMAScript 6 Support

If a custom widget uses ES6 within the JavaScript, then it will only work on the published site if the browser supports it. Here is a good [reference](http://kangax.github.io/compat-table/es6/) on browser support for ECMAScript 6 features.

### Finding DOM Elements

It is common with JavaScript to want to select the entire widget or a specific DOM element for manipulation. To do this, we recommend using the `element` object that is passed into the widget function. This is a direct reference to the element wrapper. So for example, if you have a div with the ID of `arrow`, then you’ll want to select it as follows:

This will give you options to both sets the URL of the embed (page you host) and also choose how wide the panel should be.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
// With Vanilla JS
var ele = element.querySelector('#arrow')

// With jQuery
var ele = $(element).find('#arrow')
```
{% endtab %}
{% endtabs %}

This does two good things:

* **Multiple Instances**. If the same widget is added to a page multiple times, the use of element makes sure your search is scoped only within this widget -- not the entire page/document.
* **Speed**. Rather than searching the entire page for a specific ID or class, you only search within this widget.

### Dynamic CSS Class Names

Often it is helpful to dynamically place CSS class names on an element. Using the Widget Builder's drop-down input type makes this easy to accomplish. Placing the CSS class name in the variable of the drop-down allows it to be referenced in the markup via handlebars.

For example, you might want to have a few different layout options that are based on a parent class. If you add the parent class name to the value of the drop-down menu. You might have a layout drop down like this:

<figure><img src="https://files.readme.io/31bde93-Screen_Shot_2019-03-26_at_10.23.59_AM.png" alt=""><figcaption></figcaption></figure>

Then your HTML can look like this:

{% tabs %}
{% tab title="HTML" %}
```html
<div class="parent {{layout}}">
	<div class="title">Something</div>
	<div class="description">Something else</div>
</div>
```
{% endtab %}
{% endtabs %}

This will make sure you directly pass the class as part of the HTML. Make sure that you select the default value, so there’s always an output in the HTML when the widget is first added. The same technique can be applied to the layout selector.

### 3rd Party JS + Font Libraries

We recommend avoiding 3rd party plugins as much as possible. If you need an entire plugin (for example, all of bootstrap) for a single widget/element, it’s probably overkill.

For Duda and the users of your widget, website speed is important. Improving the performance and reducing total download size of a website is critical. Here are a few recommendations:

* **Font Icon Libraries**: One of the fastest ways to slow down a website is embedding unnecessary fonts. One common practice we’ve seen is including a library like font-awesome or icomoon and only use it for a few fonts/icons. If you can, use a single SVG image instead of an entire font library. Often font libraries are \~100kb in size, where a single SVG is a few hundred bytes.
* **UI Libraries**: There are many UI libraries online that make it easy to accomplish a certain design or style. For example, it is common to include a JS library for image sliders or transition effects. It’s important that you’re careful with these, as often you will only use a small percentage of the functionality, while still loading a full library. This is a waste and you should avoid it if possible.

In the event you _must_ use a third-party library, then it should be loaded using JavaScript instead of using the `<script>` tag. This allows you to know when the library is fully loaded and you can then run any type of initialization of the script after you know the resource is loaded in the browser.

Here's an example using the popular JavaScript library [Highcharts](https://highcharts.com/)

{% tabs %}
{% tab title="First Tab" %}
```javascript
$.getScript('https://code.highcharts.com/highcharts.js')
.done(function() {
	$(element).find('.chart_container')..highcharts({
  	xAxis: {
            categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
        },
        series: [{
            name: 'Tokyo',
            data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
        }, {
            name: 'New York',
            data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
        }, {
            name: 'Berlin',
            data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
        }, {
            name: 'London',
            data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
        }]
  });
});
```
{% endtab %}
{% endtabs %}

### Identifying Page Changes

{% hint style="warning" %}
**Heads up: Deprecated**

As of Fall 2021, this recommendation is old and out of date. Duda no longer changes pages via AJAX or similar methods.
{% endhint %}

By default, when a Duda website changes pages, it loads the next page through an AJAX call that replaces only the body content of the website with the next page. This results in faster page changes (as the entire site does not need to re-render). But, this can create some complications with code that might listen specifically for the `DomReady` event. There are functions to help with this: [dmAPI.runOnReady](../../javascript-api/live-site-js-reference.md#runonready) and [dmAPI.runBeforeAjaxNavigation](../../javascript-api/live-site-js-reference.md#runbeforeajaxnavigation). These allow you to know before and after a page has changed.
