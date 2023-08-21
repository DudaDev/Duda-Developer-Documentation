# Editor Events

The editor dispatches various events during normal operation. Add event listeners using the different events.

### Before Site Publish

`platform.events.names.BEFORE_SITE_PUBLISH`

Fires after clicking **Publish** or **Republish** buttons, but before any actions have taken place as a result of the click. This event can be canceled by using `event.preventDefault();`

The example below asks the user for confirmation when the publish button is clicked. If the user cancels, then the site is not published.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
platform.events.on(platform.events.names.BEFORE_SITE_PUBLISH, (event) => {
  if (confirm("Are you sure you want to publish your site?")) {
    console.log("Continue with publishing the site.");
  } else {
    console.log("Do not continue with publishing the site.")
    event.preventDefault();
  }
})
```
{% endtab %}
{% endtabs %}

### After Site Publish

`platform.events.names.AFTER_SITE_PUBLISH`

Fires after the site is published or republished.

This example displays a simple popup after publishing the site:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
platform.events.on(platform.events.names.AFTER_SITE_PUBLISH, (event) => {
  const render = ({key, close, container}) => {
  	container.innerHTML = '<h1>Congrats on publishing your site!</h>';
  };
  platform.ui.openPopup('site-published-popup', {
  	height: 400, width: 600, render
  });
})
```
{% endtab %}
{% endtabs %}

### Home Button Clicked

`platform.events.names.EDITOR_HOME_BUTTON_CLICKED`

Fires after the home button is clicked. This event can be canceled by using `event.preventDefault();`

This example computes a new URL to redirect the user to when the home button is clicked. In this case, it builds the new URL with the account name of the editor user by using the `platform.data` object to get the account name.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
platform.events.on(platform.events.names.EDITOR_HOME_BUTTON_CLICKED, (event) => {
  event.preventDefault();
  const url = `https://dashboard.myapp.com/${platform.data.account.name}/`;
  window.location.href=url;
})
```
{% endtab %}
{% endtabs %}
