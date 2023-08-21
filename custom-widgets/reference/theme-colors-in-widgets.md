# Theme Colors in Widgets

The Duda editor allows users to [set theme colors ](https://support.duda.co/hc/en-us/articles/12952820286615-Theme-Colors)which get reused many times throughout the designing of a website. Custom widgets can take advantage of this by using theme colors in the building of the widget.

[Theme colors are based on CSS variables.](https://developer.mozilla.org/en-US/docs/Web/CSS/Using\_CSS\_custom\_properties) In order to manage a single color across the entire website.

When implementing colors in your widget, you can leverage the existing colors in the site with the following two variables:

* Primary: `--color_1`
* Secondary: `--color_2`

When writing widgets, you can leverage this on your own:

CSS

```css
.primary-action {
	background-color:var(--color_1,#ffcc00)
}
.secondary-color {
  background:var(--color_2,#f1f1f1)
}
/* Notice the fallback colors (#ffcc00,#f1f1f1) in the variable, incase custom colors do not exist on the site yet */
```

### Use cases

1. Widgets with actions. If your widget has some action, like expanding a collapsed area, you can use the primary color (`--color_1`) to color your action element/button with the primary color.
2. If you have some text that you want to highlight by setting a slightly different background, you can use the secondary color (`--color_2`) and set the background to that.

You should make sure that these colors can be edited easily in the design section of your widget.
