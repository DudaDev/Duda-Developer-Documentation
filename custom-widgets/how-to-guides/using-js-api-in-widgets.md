# Using JS API in Widgets

Widgets built in Duda's Widget builder, also known as custom widgets, have access to all site-level Javascript APIs. This includes [Javascript APIs](../reference/javascript.md) and the [Collections API](../../javascript-api/collections-js-api.md). While they are different APIs and functionalities, they can be used in tandem.

This works because widgets are rendered directly as part of the [primary page's DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document\_Object\_Model). So, they have access to all other functions.

### Using the dmAPI

In widget builder, you can simply use all `dmAPI` functions directly into the Javascript of the widget you are building. As an example, you can use the `dmAPI.loadScript()` function to pull in a third-party script. Here's an example of loading the [Splide](https://splidejs.com/) Image Slider script:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
dmAPI.loadScript('https://www.jsdelivr.com/package/npm/@splidejs/splide?path=dist',function() {
    // run code here
    new Splide( '.splide' ).mount();
})
```
{% endtab %}
{% endtabs %}

This will look like the following inside of the widget builder:

<figure><img src="https://files.readme.io/77ce9b2-widget-builder-load-splide.jpg" alt="811"><figcaption><p>Using the dmAPI to load a 3rd party script in the widget builder</p></figcaption></figure>

### Example #2 - Collections

In widget builder, you can also leverage the [Collections API](../../javascript-api/collections-js-api.md) as well to get data from a [Site Collection](../../reference/partner-api-reference/collections.md#collection-object). In order to use this, you must know the collection name ahead of time.

Here's an example of getting collection data in widget builder:

<figure><img src="https://files.readme.io/5a43571-collections-in-wb.png" alt="894"><figcaption><p>Using the collections API to load data from a collection.</p></figcaption></figure>
