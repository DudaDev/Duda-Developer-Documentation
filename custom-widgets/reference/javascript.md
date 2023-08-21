# Javascript

As part of widgets, Duda allows you to use standard JavaScript. This can be used to load content, add custom functionality and more. We also give you easy access to both the DOM element, data input to the widget and a few helper values passed into the callback. Below is a list of helper objects.

All the Javascript you include in the widget is executed when the widget is loaded on the page, from a callback function. In the function, there are three variables passed in: `element`, `data`, and `api`. Each is documented below.

### Element

A direct reference to the wrapper `<div>` DOM element of this widget. Here's an example of how you can interact with the element.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
/** 
Example #1 - Simple JS command
**/ 
console.log("Element Class List: " + element.classList);
//Output: "Element Class List: widget-366254 dmCustomWidget"

/** 
Example #2 - with jQuery
**/
$(element).find('.childClass')
```
{% endtab %}
{% endtabs %}

### Data

The data object includes several child fields which help you code custom solutions. Below is each

#### Config

Accessed from `data.config` object. This contains variables of all the inputs entered in either the design or content section of the widget. If an input does not have a value (blank by default) then it will not be added to the `data.config` object.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
/**
	Each input from the content section can be accessed through it's variable name: 
**/
console.log("Input with variable name text1 value is: ",data.config.text1)
```
{% endtab %}
{% endtabs %}

Below is a list of all the inputs and the type of data you can expect when referencing via Javascript:

| Input Type     | JS Data Type       | Additional Details                                                                                                                                                                                                                                                                                                                      |
| -------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Text**       | s_tring_           |                                                                                                                                                                                                                                                                                                                                         |
| **Image**      | s_tring_           | String is an absolute URL of the image                                                                                                                                                                                                                                                                                                  |
| **Icon**       | s_tring_           | String containing raw SVG markup. Can be appended directly to the DOM.                                                                                                                                                                                                                                                                  |
| **Dropdown**   | s_tring_           | String with the selected field from the drop down.                                                                                                                                                                                                                                                                                      |
| **List**       | a_rray of objects_ | Contains all nested items                                                                                                                                                                                                                                                                                                               |
| **Large Text** | s_tring_           | String of rich text values. Can contain markup for inline styles.                                                                                                                                                                                                                                                                       |
| **Date**       | _int_              | A unix timestamp of the selected data                                                                                                                                                                                                                                                                                                   |
| **Radio**      | s_tring_           | A String of the selected value                                                                                                                                                                                                                                                                                                          |
| **Toggle**     | b_ool_             |                                                                                                                                                                                                                                                                                                                                         |
| **Slider**     | s_tring_           | A string of the selected value                                                                                                                                                                                                                                                                                                          |
| **Checkbox**   | b_ool_             |                                                                                                                                                                                                                                                                                                                                         |
| **Link**       | o_bject_           | <p>An object containing link details, structued as follows:<br><code>{ "value": "http://www.duda.co", "label": "", "type": "url", "href": "http://www.duda.co", "raw_url": "http://www.duda.co", "target": "_blank" }</code></p>                                                                                                        |
| **Video**      | o_bject_           | <p>Object of the video selected (uploaded, youtube, etc..).<br><code>{ "videoUrl": "https://vid.cdn-website.com/a951ccfe/videos/Vnhi0p8OQVy2sYi7mU13_My+First+Day+Driving1-v.mp4", "poster": "https://irp.cdn-website.com/a951ccfe/dms3rep/multi/Vnhi0p8OQVy2sYi7mU13_My+First+Day+Driving1.v2.0000000.jpg", "type": "cdn" }</code></p> |

#### Device Type

A string containing the device that Duda detected as visiting the website. Can be accessed from: `data.device`. Allows you to change functionality based on device type. There are three possible values: `desktop`, `tablet` and `mobile`.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
if (data.device==="mobile") {
	//do something if mobile
} else {
	//do something if desktop or tablet
}
```
{% endtab %}
{% endtabs %}

#### In editor

A boolean value if the widget is currently in the editor or being viewed on a live website/preview. Accessed from `data.inEditor`.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
if (data.inEditor) {
	//do something if in editor
} else {
	//do something regular if outside editor
}
```
{% endtab %}
{% endtabs %}

#### Page Name

Access the name of the page the widget is currently being viewed from. This is the name the user has entered in the page settings while designing the site. Accessed from `data.page`.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
alert("Current page is: " + data.page);
//Out: "Current page is: home"
```
{% endtab %}
{% endtabs %}

#### Element ID

Access the unique ID assigned to this element. The ID is unique to the page it is on (not across the whole site). Can be accessed via `data.elementId`.

#### Site ID

Access the unique Site ID for the site across all of Duda. Also referred to as the `site_name`. Accessed via `data.siteId`.

#### Locale

Returns the two letter language code for the currently selected language. Accessed via `data.locale`.

### API

API contains helper functions to perform additional functionality on the site. This includes things like getting [Collections API](../../javascript-api/collections-js-api.md), localization settings of a widget, and [Rendering External Apps](../tutorials/external-apps.md).
