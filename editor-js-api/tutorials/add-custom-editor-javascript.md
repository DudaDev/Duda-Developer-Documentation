---
description: >-
  Customize the experience your customers have while creating or updating their
  site.
---

# Add Custom Editor JavaScript

### Getting Started

Click **White Label**, then click **Custom Branding** to navigate to the Custom Branding page. In the sidebar, click **HTML/CSS**. This opens the code editor where you can begin using the Editor JS API.

<figure><img src="https://files.readme.io/0ba246c-Screen_Shot_2022-04-05_at_1.21.45_PM.png" alt="1406"><figcaption><p>Custom branding UI. The HTML/CSS button can be seen in the lower left corner.</p></figcaption></figure>

The HTML and CSS editor opens in a modal where you can add your custom code. Any HTML is appended to the body tag of the editor and any CSS is appended after the built-in stylesheets. Script tags are allowed within your HTML to allow for custom behaviors within the editor.

<figure><img src="https://files.readme.io/ca91b0b-Screen_Shot_2022-04-05_at_1.33.17_PM.png" alt=""><figcaption></figcaption></figure>

### Wait for the Editor to Load

In most circumstances you want the editor UI to fully load before executing your own JavaScript. Any use of the Editor JS API _requires_ you to wrap your code in a callback on the browser `load` event.

{% tabs %}
{% tab title="HTML" %}
```html
<script>
  window.addEventListener("load", function () {
    // it is now safe to access the Editor JS API
    alert(platform.data.site.name);
  });
</script>
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know: Script Tags are Required**

Remember your code is appended as HTML before the closing body tag. You must wrap any JavaScript in a script tag, or the browser will interpret it as plain text.
{% endhint %}
