# External Apps

When building a custom widget the javascript for that widget lives in a single function. This code must be maintained as part of the custom widget and updated within the Widget Builder only. This works great for most widgets; however, this can pose challenges for a widget that require a significant amount of javascript. This is where you can use an external app to manage the logic of your custom widget.

{% hint style="warning" %}
**Heads up:** This functionality is currently in BETA. Feel free to try it out and let us know any feedback you have.
{% endhint %}

### renderExternalApp

The Widget Builder now offers an easy way to do that - by using a new API referenced at `api.scripts.renderExternalApp`. Here's how it is used within the Javascript section of your custom widget.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
function(element, data, api) {
   api.scripts.renderExternalApp(<scriptSrc>, <container>, <props>, <options>)
}
```
{% endtab %}
{% endtabs %}

| Parameter                  | Description                                                                    |
| -------------------------- | ------------------------------------------------------------------------------ |
| **scriptSrc \***           | The src of the external script                                                 |
| **container \***           | The DOM element to render the external app into                                |
| **props**                  | Props that are passed into the external app                                    |
| **options.amd**            | Should the external app be lazy loaded. Using `require.js`. Defaults to `true` |
| **options.name**           | If not using `amd` this should specific the global name of the app             |
| **options.keepSubtree**    | Clean the subtree on every widget update. Defaults to `false`                  |
| **options.additionalData** | Object containing additional data passed to the external app on `init`         |

### External App Code

The app should expose `init` and `clean` methods with the following signature:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
export function init({ container, props, ...additionalData }) {
  // render you app into `container`, passing it `props` if needed
}

export function clean() {
  // cleanup for the app
}
```
{% endtab %}
{% endtabs %}

Here's what this looks like in the Widget Builder

{% tabs %}
{% tab title="JavaScript" %}
```javascript
function(element, data, api) {

  // define the script src
  var scriptSrc = 'https://duda-widget-poc.s3.amazonaws.com/static/js/duda-widget.js';

  // render the app
  api.scripts.renderExternalApp(scriptSrc, element, {
      // the external app will get a `userName` prop
      // that mirrors the `accountName` field from the widget editor
      userName: data.config.accountName,
      // the external app will get a `type` prop
      // that mirrors the `mode` field from the widget editor
      type: data.config.mode,
  });
}
```
{% endtab %}
{% endtabs %}

### React/Angular/Vue apps

For code that is written in a framework, and built using an external build tool (for example, Webpack) - the usage in the widget builder is as follows:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
function(element, data, api) {

  // define the script src
  var scriptSrc = 'https://duda-widget-poc.s3.amazonaws.com/static/js/duda-widget.js';

  // render the app
  api.scripts.renderExternalApp(scriptSrc, element, {
      bw: !!data.config.bw,
      userName: data.config.accountName,
      theme: data.config.theme,
      type: data.config.mode,
      backToList: data.config.backToList
  });
}
```
{% endtab %}
{% endtabs %}

The app should be built as AMD

[Example app code](https://github.com/DudaDev/react-widget-demo)\
[Built code (minified)](https://duda-widget-poc.s3.amazonaws.com/static/js/duda-widget.js)\
[Example site](http://react-widget-poc.multiscreen.d1test.biz/)

### Vanilla JS apps

For code that is written without a build system (or that is not built as `amd`), some additional properties should be passed (namely, `amd` and `name`):

{% tabs %}
{% tab title="JavaScript" %}
```javascript
function(element, data, api) {

  var vanillaScriptSrc = 'https://duda-widget-poc.s3.amazonaws.com/static-noamd/index.js';

  // render the app (safe to be called multiple times)
  api.scripts.renderExternalApp(vanillaScriptSrc, element, {
      areaFill: data.config.areaFill,
      title: data.config.title,
      subtitle: data.config.subtitle,
      zoomable: data.config.zoomable
  }, { amd: false, name: 'chart' });
}
```
{% endtab %}
{% endtabs %}

The App should expose `init` and `clean` as well.

[Example](https://github.com/DudaDev/react-widget-demo/blob/no-amd/src/index.js)\
[Example site](http://react-widget-poc-vanilla.multiscreen.d1test.biz/)
