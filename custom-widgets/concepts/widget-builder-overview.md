# Widget Builder Overview

{% hint style="info" %}
**Good to know:** To learn more, check out [Building Custom Widgets](https://university.duda.co/building-custom-widgets) on Duda University.
{% endhint %}

Duda’s Widget Builder allows you to build your own custom widgets and make them available to your customers within the website editor. You can design beautiful widgets that look and act exactly like all other widgets within the Duda platform. The Widget Builder supports standard Duda input options for both the content and design of widgets, to help maintain consistency of UI and experience for customers building websites. This means you can accept a text input as content or a background image as a design of the element.

{% hint style="warning" %}
**Heads up:** Custom widgets do not support the multi-language site feature.
{% endhint %}

### Code

A custom widget is composed of a combination of HTML, CSS, and JavaScript. View the guides for each technology to learn more about how to use each language when building a widget.\
[HTML](../reference/handlebars-and-html.md)\
[Javascript](../reference/javascript.md)

When developing a widget, it is your responsibility to support the code that gets output on the website. All of the code you write will be exactly output on the website. We recommend that you use standard browser APIs and features that are commonly supported across the majority of browsers.

### Content & Design Editor

The Content and Design editors allow you to define the input options of each widget. This allows you to use standard inputs, such as text, images, links, lists, and more.

[Content Editor](../reference/content-editor.md)\
[Design Editor](../reference/design-editor.md)

These inputs dynamically update the widget's HTML, JavaScript or CSS, allowing widgets to appear unique and customizable wherever they are being used. By using the standard input options that Duda provides, you keep a consistent editing interface for all users of the platform. Design inputs allow you to assign a custom CSS selector to define which HTML elements on the page will be assigned these values directly.

### Publishing

Publishing a widget takes the current code, options, etc., and makes it available to your users. Until a widget is published, it is only visible to account owners or staff members that have the Widget Builder permission. Code that you’re currently working on is considered in draft and can only be viewed in the preview.

The first time you publish a widget, it will be published as version 1. Each time you republish, the version is incremented to another version. When republishing you are prompted to `auto update` all existing instances of that widget on live sites. This feature is off by default. Auto update can be useful, but it is highly recommended to test any widget updates before pushing to all sites.

If auto update is not selected, all changes you make to widgets (such as adding CSS, JS, etc.) will not alter widgets that are added to websites. If a user has already added a widget under an old version, they will continue to be able to use that widget version, but will also be presented with an upgrade message asking them to upgrade.

### Custom Widget vs HTML Widget

Once published, custom widgets will be accessible within the widget menu of the website editor. This can provide a better user experience by allowing users to easily drag-and-drop these widgets on their site and easily configuring them through the content and design menus.

Building a custom widget is recommended for:

* Building reusable elements
* Elements that will require user input for customization
* Accessing and inheriting Duda's global styles
* Using connected data

An HTML widget can be used for one-time code integrations on a website. This solution is a great option for adding 3rd party scripts or code that doesn't require customization and can easily be placed within the widget's input.
