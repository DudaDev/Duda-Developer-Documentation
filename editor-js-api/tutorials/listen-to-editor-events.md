# Listen to Editor Events

Events in the editor can be assigned callbacks allowing partners to override or extend the default behavior of the event. See the [Editor Events](../reference/editor-events.md) reference for a list of all available events.

Follow the instructions in the [Adding Custom Editor JavaScript](add-custom-editor-javascript.md) tutorial to open the custom HTML editor. Paste the following code in the HTML editor and click **Done** to save the code and close the modal. Make sure to include the surrounding script tags when copying the code.

{% tabs %}
{% tab title="HTML" %}
```html
<script>	
	window.addEventListener("load", function () {
	  platform.events.on(
	    platform.events.names.EDITOR_HOME_BUTTON_CLICKED,
	    function (event) {
	      event.preventDefault();
				window.location.href = 'https://duda.co';
	    }
	  );
	});
</script>
```
{% endtab %}
{% endtabs %}

This code overrides the home button located in the header of the editor in order to redirect to the Duda website, instead of navigating to the sites dashboard. First, wait for the editor to fully load before adding a callback function to the `EDITOR_HOME_BUTTON_CLICKED` event. The callback function cancels the original action of the button and updates the browser location to the Duda website.
