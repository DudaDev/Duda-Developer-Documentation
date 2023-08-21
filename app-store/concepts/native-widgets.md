---
description: Developing native Duda widgets for your app using Duda's Widget Builder
---

# Native Widgets

### The benefits of native widgets

All of Duda's native widgets share some common behaviors, thus creating a native standardized experience for Duda's users. By building your widgets with Duda Widget Builder, you can easily develop widgets that demonstrate these common behaviors and create a native experience for Duda users.

The benefits of having a native behavior for your widgets are:

1. Increasing adoption by earning users' trust. Native widgets are perceived to be of high quality for the website developer, and more importantly for the website visitor.
2. Increasing adoption by reducing friction: Duda users are familiar with widgets' native behaviors. When your widgets work in the same way, users will easily add and configure your widget as they won't need to learn new practices.
3. **Coming soon:** Discover apps via widgets: Duda users discover new site capabilities by browsing in the widgets menu. Duda users perform more than 10K widget searches each day. Having your widget appear in the search results will increase the discoverability of your app and will increase adoption.

### Native behaviors of Duda widgets

Duda's [Widget Builder](../../custom-widgets/concepts/widget-builder-overview.md) is a powerful tool for developing native Duda widgets. The Widget Builder allows you to create all the native behaviors of Duda widgets:

1. **Drag and Drop, Cut and Paste:** All widgets are available on the widgets menu, from where users can drag and drop them into the editor to position within the site. Users can easily move widget across the and resize wi
2. **Content Menu:** A quick menu allows users to configure widget content and behavior. Duda supplies you with a UI to configure a [variety of input types ](../../custom-widgets/reference/content-editor.md)to control your widget content and behavior.
3. **Design Menu:** A quick menu allows users to configure widget appearance. Duda supplies you with a UI to configure a [variety of input types ](../../custom-widgets/reference/design-editor.md)to transfer parameters to your widget to configure its design.

### Best practices for App Widgets

To start building your widget, follow the Widget Builder [documentation ](../../custom-widgets/concepts/widget-builder-overview.md).\
Duda expects you to build your widget according to the following guideline to ensure native widget experience for Duda users.

#### Sync widget site-specific behavior and configuration with the app-server

On Duda's app store, each app may have many installations, sites it's active on. During the installation process, Duda sends a Callback API request to the app server that includes the `site name`. Most app widgets are expected to behave differently between sites, based on site-specific data, user configuration, or user-generated content.\
Some of these behavior differences will be achieved using the Widget Builder abilities, for example, configuring colors using the design menu or widget layout using the content menu. However, for some behavioral differences, the capabilities of the Widget Builder might not be enough. In such cases, app-server would be the source of truth for site-specific behavior.\
To sync widget behavior with configuration persisted on your app servers, you should use the `site name` and an external Id. The `site name` is accessible on the widget context via the [`getSiteName`](../../javascript-api/live-site-js-reference.md#getsitename) function.
