# Site Wide HTML

Duda’s App Store allows app providers to inject code into all the pages of a Duda site. The code injected by providers will be stored in a dedicated DB table and rendered at the end of the BODY section of all the pages of a site.

This functionality is designed to support:

1. 'Floating' widgets
2. Configuration code and objects which interacts with markup widgets.

### Injecting floating widgets

To inject the code of your floating widget, use the following site REST API call:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST {api_endpoint}/api/integrationhub/application/site/{{site name}}/sitewidehtml -H 'Authorization: Basic {{basicAuth base64}}' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json' -H 'cache-control: no-cache' -d '{"markup": "YOUR MARKUP HERE"}'
```
{% endtab %}
{% endtabs %}

You can use the GET operation to get the current code injected to a site.\
To remove an injected code, the app provider should POST and empty string via API.

The injected code:

1. Will be available in the editor (design time) right after its injection
2. Will start working on the runtime site only after a user publishes the site (or republished it).

{% hint style="warning" %}
**Heads up: Updating the code requires to republish the site to take affect**

If you update the code via API, the new code will be available in the editor/preview modes immediately.&#x20;

However, the updated code won't be available on the runtime site (the public site) until the user republishes the site.
{% endhint %}

To remove an injected code, the app provider should POST and empty string via API.

### Using Global Design with floating widgets

Duda's user can specify [the Site Theme](https://support.duda.co/hc/en-us/articles/12984669833879-Site-Theme) that is applied to all site elements having the appropriate classes. To automatically apply the Global Design to you floating widget you should:

1. Create a code snippet composed only from HTML [Content Flow](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content\_categories#Main\_content\_categories) tags, and apply the relevant CSS classes to that content. Please consult Duda's App Store team ([app-developer-support@duda.co](mailto:app-developer-support@duda.co)) to find the relevant classes for your snippet.
2. Inject this content to the site using the `/api/integrationhub/application/site/{{site name}}/sitewidehtml` enpoint. Add a `location` param on the request body and assign the value `CONTENT_END` to it.
3. Inject any other no [Content Flow](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content\_categories#Main\_content\_categories) tags such as `<script>` tags using _another_ API call to `/api/integrationhub/application/site/{{site name}}/sitewidehtml` enpoint with `BODY` value for the `location` param.

See example for injecting a button that uses the global design:

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST {api_endpoint}/api/integrationhub/application/site/{{site name}}/sitewidehtml -H 'Authorization: Basic {{basicAuth base64}}' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json' -H 'cache-control: no-cache' -d '{"markup": "<div>My content</div>", "location":"CONTENT_END"}'
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST {api_endpoint}/api/integrationhub/application/site/{{site name}}/sitewidehtml -H 'Authorization: Basic {{basicAuth base64}}' -H 'X-DUDA-ACCESS-TOKEN: Bearer XXX-XXXXX-XXXXX' -H 'Content-Type: application/json' -H 'cache-control: no-cache' -d '{"markup": "<script>My script</script>", "location":"BODY"}'
```
{% endtab %}
{% endtabs %}

### Enabling the code of floating widgets to interact with the Duda editor

{% hint style="warning" %}
**Heads up: Must for floating widgets**

All floating widgets injected using this mechanism must be configured to interact with the editor.
{% endhint %}

The Duda editor is composed of two main sections:

1. An iframe containing the website, rendered in the same way as the site’s runtime.
2. The editor itself.

The editor is aware of Duda’s markup in the rendered iframe, and changes its behavior:

1. Mouse hover over Duda’s markup widgets will highlight them with a blue wrapper.
2. A click/right-click on Duda’s markup widgets will not result in the widgets’ regular behavior but will trigger a context menu popup.
3. Dragging a widget will move it around the site and update markup accordingly.

When the user switches to ‘preview’ mode in the editor, the site’s behavior returns to normal.

<figure><img src="https://files.readme.io/6752353-editor_iframe_and_context_menu.PNG" alt="1229"><figcaption><p>Red: Duda site previewed in the editor, Green: widget context menu.</p></figcaption></figure>

### Registering floating widgets in the editor

To allow injected floating widgets to behave a native way in the editor, Duda will enables app providers to register DOM elements in a way accessible to the editor via an interface.\
The editor will handle registered elements under a similar logic as Duda’s widgets:

1. Mouse hovers will trigger highlighting of the element.
2. Click/right-click will trigger a context menu with links referring to your app's iframe.

On preview mode, the widgets will act normally.

### How to register your widget?

Add to the floating widget a script which uses the function `window.dmInlineEdit.externalElements.register_`and pass an object of the following format:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
<script>
window.dmAPI.registerExternalRuntimeComponent({
    appUuid:'appUuid',
    'elements': [
        {
            selector:'#something',
            'contextMenuItem' :[
                {
                    label: {
                        branded: {
                            'en':'Configure widget from APPName console',
                            'es':'Configurar widget desde la consola del APPName'
                        },
                        wl: {
                            'en':'Configure widget from APP console',
                            'es':'Configurar widget desde la consola APP'
                        }
                    },
                    'ssoPostFix':'widget/settings',
                    'queryParams': [
                         {
                             name:'section',
                             value:'website-widgets'
                         }
                     ]
                }
            ]
        }
    ]
});
</script>

<!--- Your floating widget code here --->
<script>...</script>
```
{% endtab %}
{% endtabs %}

Where:

1. _appUuid_ is your app's UUID
2. _elements_ is an array of DOM elements of your widget.
3. _selector_ is the selector which Duda editor use to select the DOM elements of your widget.
4. _label - branded/wl_ is an array of strings which will be displayed as links in the context menu of the widget.

When the user clicks on the links in the context menu, Duda will direct the user into your app's iframe. Duda would use the _ssoPostFix_ and _queryParams_ to enrich the [iframe SSO link](../concepts/single-sign-on.md). Thus the links can refe

### Responding to layout changes in the editor

The Duda editor allows the user to switch between Desktop, Tablet, and Mobile views. These changes are not detectable in a regular way by site elements. To get the current editor view, use the following API, which returns `desktop`, `tablet`, or `mobile`:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const currDevice = dmAPI.getCurrentDeviceType();
```
{% endtab %}
{% endtabs %}

### Refreshing the editor from your app's iframe

If your app performs changes to the site while the user in the context of the iframe, you can use an API to ask the editor to refresh the site.\
This is useful when the user makes changes on the iframe which affects the site-wide code and requires it to reload for changes to take effect.

To do that, you should send a [postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) from your child frame to the Duda parent.

Duda provides a simple JS SDK/Library for you to use which adds a simple function call to refresh the editor. The URL for this Library is passed as a URL on the [SSO to open your app](../reference/sso.md). We recommend relying on this URL to embed the JS library, as we'll update it as we add new options in the future.

To refresh the editor via Post Message:

1. Embed the JS SDK in your application page. Duda passes the source of this file as the iframeSDKSrc. [Here's an example of it.](https://sandbox-ms-cdn.multiscreensite.com/integrationhub/1027/res/sdk/iframe.js)
2. Run the function `_dAPI.refresh()`
