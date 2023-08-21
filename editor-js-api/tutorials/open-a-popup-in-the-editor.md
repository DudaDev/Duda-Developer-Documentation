# Open a Popup in the Editor

The Editor JS API provides a `platform.ui` object to manipulate the UI of the editor. Currently, the only piece of UI available is a `popup` component. The popup provides a convenient container within which you can place your own interface. Once a popup opens, the Editor JS API executes a `render` function where code should be placed to build a UI. See the [Platform UI](../reference/platform-ui.md) reference for all available parameters to the `openPopup` method and the arguments provided to the `render` function.

Follow the instructions in the [Adding Custom Editor JavaScript](add-custom-editor-javascript.md) tutorial to open the custom HTML editor. Paste the following code in the HTML editor and click **Done** to save the code and close the modal. Make sure to include the surrounding script tags when copying the code.

{% tabs %}
{% tab title="HTML" %}
```html
<script>
  function render(args) {
    // container is the DOM element of the popup itself.
    args.container.innerHTML = '<iframe src="https://example.org" width="500" height="300"></iframe>';
  }
	
  window.addEventListener("load", function () {
	  platform.ui.openPopup("custom-editor-popup", {
      width: 500,
	    height: 300,
	    render
	  });
  });
</script>
```
{% endtab %}
{% endtabs %}

This code opens a popup immediately after entering the editor. First, wait for the editor to fully load before calling the `openPopup` method with options for the width, height, and render function. The render function uses the `container` argument to insert an iframe into the modal and display a website.
