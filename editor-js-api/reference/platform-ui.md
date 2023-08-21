# Platform UI

Use `platform.ui` to create and modify UI elements in the editor.

### Popups

The platform.ui.openPopup method opens a popup to display content to the user in the editor.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
const render = ({key, close, container}) => {
	container.innerHTML = 'Hi there from within popup';	
};

platform.ui.openPopup('my-popup-key', {
	height: 400, width: 600, render
});
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th>Property</th><th width="141">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>width</strong></td><td><em>int</em></td><td>Width dimension of the popup in px</td></tr><tr><td><strong>height</strong></td><td><em>int</em></td><td>Height dimension of the popup in px</td></tr><tr><td><strong>render</strong></td><td><em>function</em></td><td>Add custom content and behavior to the popup by using this function to return the popup element.<br><br>Arguments:<br>key → popup's key<br>close → close handler function to close the popup<br>container → popup container DOM element</td></tr><tr><td><strong>onClose</strong></td><td><em>function</em></td><td>Callback when the popup is closing</td></tr><tr><td><strong>closeOnEsc</strong></td><td><em>bool</em></td><td>Escape key closes the popup</td></tr><tr><td><strong>closeOnClickOutside</strong></td><td><em>bool</em></td><td>Clicking outside of the popup closes the popup</td></tr></tbody></table>
