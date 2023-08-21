# Handlebars & HTML

All custom widgets will load within a `<div>`, with a unique `class` assigned. This class remains static and can be referenced for all instances of the widget in Javascript or CSS.

For the content users enter into the content editor, you can output these values within the HTML using [handlebars](http://handlebarsjs.com/). The HTML content is rendered on the server and delivered down to the client in fully standard HTML.

Duda has several custom helpers that relate back to specific functionality in the platform. This ensures that you follow Duda's common practices and allows you to take advantage of native features more easily.

### Simple Expressions

The value defined in the content library can be used directly within the widget's HTML. Within the HTML, curly brackets surround the variable that you will want to output into your HTML. For example, if you had a text input called headerText, then the code below would print the text input.

{% tabs %}
{% tab title="HTML" %}
```handlebars
<div class="ex">{{headerText}}</div>
```
{% endtab %}
{% endtabs %}

| Input Type        | Additional Details                                                                 |
| ----------------- | ---------------------------------------------------------------------------------- |
| **Text**          |                                                                                    |
| **Dropdown**      | A String of the selected value.                                                    |
| **Icon**          | String containing raw SVG markup.                                                  |
| **Large Text**    | Requires the "triple-stash" `{{{` to avoid HTML escaping.                          |
| **Image**         | String is an absolute URL of the image                                             |
| **Date**          | String formatted in standard universal full date-time pattern in the UTC timezone. |
| **Radio Buttons** | A String of the selected value.                                                    |
| **Slider**        | A String of the selected value.                                                    |

### If statement

`If` statement checks if the value exists or is set to true. It will evaluate to false if it's an empty string, is false, or null. The `if` helper can only test for properties to be true or false – not arbitrary expressions. This is usually combined with a `Checkbox` or `Toggle` input.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#if checkbox}}
	<p>Checkbox is selected / true</p>
{{else}}
	<p>Checkbox is not selected / false</p>
{{/if}}
```
{% endtab %}
{% endtabs %}

| Input Type   | Additional Details |
| ------------ | ------------------ |
| **Checkbox** |                    |
| **Toggle**   |                    |

### Unless

You can also use the `unless` handlebars helper, which is the inverse of `if`. This checks if the value is false.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#unless toggle1}}
	<p>Toggle is disabled</p>
{{else}}
	<p>Toggle is enabled</p>
{{/unless}}
```
{% endtab %}
{% endtabs %}

### Equals

You can use `equals` to define if a specific input equals a string.

{% tabs %}
{% tab title="HTML" %}
```handlebars
{{#equals dropDown "value1"}}
	<p>DropDown equals value1</p>
{{else}}
	<p>Dropdown does not equal value1</p>
{{/equals}}
```
{% endtab %}
{% endtabs %}

| Input Type        | Additional Details                                                                 |
| ----------------- | ---------------------------------------------------------------------------------- |
| **Text**          |                                                                                    |
| **Dropdown**      | A String of the selected value.                                                    |
| **Icon**          | String containing raw SVG markup.                                                  |
| **Image**         | String is an absolute URL of the image                                             |
| **Date**          | String formatted in standard universal full date-time pattern in the UTC timezone. |
| **Radio Buttons** | A String of the selected value.                                                    |
| **Slider**        | A String of the selected value.                                                    |

### Not Equals

You can use `not equals` to define if a specific input does not equal a string.

{% tabs %}
{% tab title="HTML" %}
```handlebars
{{#notEquals dropDown "value1"}}
	<p>DropDown does not equal value1</p>
{{/notEquals}}
```
{% endtab %}
{% endtabs %}

### Decode

Evaluate an input to check if it has a specific value. If they do, you can rewrite it to be a different value. This is great to use if you have a dropdown with many different options. It works by decoding an input, then checking if it equals a specific string. If it does, you can have it output a different string.

{% tabs %}
{% tab title="HTML" %}
```handlebars
{{#decode dropDown 
	"dropDownValue1" "Output this if value is dropDownValue1" 
	"dropDownValue2" "Output this if value is dropDownValue2"	"Default output" }}
{{/decode}}
```
{% endtab %}
{% endtabs %}

For example, if you had a dropdown named color with three entries (Red, Blue and Green), then you can use `decode` to get the output like this:

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#decode color 
	"Red" "My Favorite Color Is Red" 
	"Blue" "My Favorite Color Is Blue" 
	"Green" "My Favorite Color Is Green" "Default output" }}
{{/decode}}
```
{% endtab %}
{% endtabs %}

### Each

`Each` allows you to loop through a list or array of items. This is always linked with the `List` input inside of Widget Builder. While looping through, you will have access to each inner item inside of the list.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
<ul>
{{#each list1}}
	<li>{{listInnerText}}</li>
{{/each}}
</ul>
```
{% endtab %}
{% endtabs %}

Inside of an `each` loop, you are able to access three data variables to aid in the logic and visual output of your widget. `@index` will display the current iteration of the loop, while the `@first` and `@last` variables are booleans compatible with the `{{#if}}` logic tag. The `@index` variable is zero-based, meaning its value will be zero on the first iteration of your loop, and increase by one for each subsequent iteration.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
<ul>
{{#each list1}}
	<li>
    {{#if @first}}First Item!{{/if}}
    {{@index}} {{listInnerText}}
    {{#if @last}}Last Item!{{/if}}
  </li>
{{/each}}
</ul>
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:** The `@index`, `@first` and `@last` data variables are only available inside of an `each` loop.
{% endhint %}

### Links

Links must be handled in a specific way within Duda websites. Duda allows users to choose only valid pages, popups, eCommerce, etc. Due to this, Duda controls the entire output of the anchor markup to automatically format it to perform the correct action when clicked. To use the input of a link, you must use the `custom_link` helper.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#custom_link linkVariableName}}
	<span>Anchor Text or {{linkText}}</span>
{{/custom_link}}
```
{% endtab %}
{% endtabs %}

This will output as standard anchor markup:

{% tabs %}
{% tab title="HTML" %}
```html
<a href=”/about” relevant_attribute=”value”>
	<span>Anchor Text or About Page</span>
</a>
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Heads up: Using Connected Data**

Links does not support connected data. Using `custom_links` with connected data returns an error: "We could not handle your handlebars input properly".

This field should only be used in widgets that will not be connected to data. In order to use connected data with a link, use simple expression with a variable in an HTML anchor tag.\
`<a href={{itemLink}}>`
{% endhint %}

### Buttons

Duda allows you to use our standard button. This allows you to add buttons as parts of widgets, or as a standalone button with additional features. The benefit of doing this is that the button will use Duda's standard classes and thus inherit all global styles for buttons on the website. You can also use the button input design type to easily add style settings for this specific button.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#custom_button btnText class="button-class"}}
{{/custom_button}}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:** In the example above, you can include a custom class on the button, so that in the design settings you can target that button easier.
{% endhint %}

If you want the button to be a link as well, you can surround the button in the #custom\_link helper as well.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#custom_link linkVariableName}}
	{{#custom_button btnText class="button-class"}}
	{{/custom_button}}
{{/custom_link}}
```
{% endtab %}
{% endtabs %}

### String Contains

A logic helper that allows you to check if a string that was input contains a specific string. If it's true, you can output a certain HTML element.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#strContains variableName "test"}}
	Input variable contains "test"
{{else}}
	Input variable does not contain "test"
{{/strContains}}
```
{% endtab %}
{% endtabs %}

### String Replace

Searches through an string that is input by the user and replaces part of it with a new string. Useful for trimming spaces or new lines from inputs into text boxes.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
{{#strReplace variableName "findString" "replaceWith"}}{{/strReplace}}
```
{% endtab %}
{% endtabs %}

### HTML Escaping

By default, handlebars escapes the output of any content added to the widget configuration. If you want to avoid escaping and directly embed the content in the page, you can use the triple-stash output: `{{{exampleVariable}}}`. This is good to use with large text inputs, as you might want to allow users to enter spaces (\
) or full HTML.

{% tabs %}
{% tab title="Handlebars" %}
```handlebars
<p>{{{largeText}}}</p>
```
{% endtab %}
{% endtabs %}
