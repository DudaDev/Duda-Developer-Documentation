---
description: A step-by-step guide on how to build a custom form widget.
---

# Build a Custom Form Widget

The Widget Builder can be used to create and design widgets to help maintain consistency in the UI and experience for customers building websites. This guide walks you through the steps on how to build a custom form widget from beginning to end using our Widget Builder. By the end of this guide you will have created a simple contact form that sends data to an external API endpoint.

{% hint style="info" %}
**Good to know:** To learn more, check out [Building Custom Widgets](https://university.duda.co/building-custom-widgets) on Duda University.
{% endhint %}

### Form Widget

A form widget is used to collect information. This information can be sent directly to a user's inbox or it can be sent to an API that can then generate and trigger a workflow. In this guide, we will build a form widget that collects business information. This business information will be passed to an API endpoint that will trigger the creation of an [Instant Website](../../partner-api/tutorials/instant-websites.md). Following is an example of the form you will create using this guide.

<figure><img src="https://files.readme.io/9477710-screencapture-rise-agency-responsivewebsitebuilder-io-home-site-5b1c4901-home-2022-03-01-13_28_31.png" alt="" width="375"><figcaption></figcaption></figure>

We will start by creating a new widget and calling it Instant Site Form Widget.

### 1. Custom Code

Our card widget will use custom HTML, Javascript, and CSS that are defined below.

#### HTML

In the HTML section, place the following HTML.

{% tabs %}
{% tab title="HTML" %}
```html
<form id="myForm" class="dmRespDesignRow">
    <h4 class="dmforminput small-12 dmRespDesignCol medium-12 large-12 section-title">GENERAL INFO</h4>
    <div class="dmforminput dmRespDesignCol">
        <label>Business Name</label>
        <input type="text" name="name">
    </div>
    <div class="dmforminput small-12 dmRespDesignCol medium-4 large-6">
        <label>Phone</label>
        <input type="tel" name="tel">
    </div>
    <div class="dmforminput required  small-12 dmRespDesignCol medium-4 large-6">
        <label>Business Email</label>
        <input type="email" name="email">
    </div>
    <div class="dmforminput required  small-12 dmRespDesignCol medium-12 large-12">
        <label>Business Address</label>
        <input id="address" type="text" name="address" placeholder="">
    </div>
    <h4 class="dmforminput small-12 dmRespDesignCol medium-12 large-12 section-title">BUSINESS HOURS</h4>
    <div id="hours-container">
        <div class="dmforminput small-12 dmRespDesignCol medium-12 large-12 direction-text">Select the days</div>
        <div class="dayButtons dmforminput dmRespDesignCol large-12">
            <div title="SUN" class="dmRespDesignCol medium-1 large-1 day-border days">
                <div class="day">
                    <span>Su</span>
                </div>
            </div>
            <div title="MON" class="dmRespDesignCol medium-1 large-1 day-border days selected-day ">
                <div class="day">
                    <span>M</span>
                </div>
            </div>
            <div title="TUE" class="dmRespDesignCol medium-1 large-1 day-border days selected-day ">
                <div class="day">
                    <span>T</span>
                </div>
            </div>
            <div title="WED" class="dmRespDesignCol medium-1 large-1 day-border days selected-day ">
                <div class="day">
                    <span>W</span>
                </div>
            </div>
            <div title="THU" class="dmRespDesignCol medium-1 large-1 day-border days selected-day ">
                <div class="day">
                    <span>Th</span>
                </div>
            </div>
            <div title="FRI" class="dmRespDesignCol medium-1 large-1 day-border days selected-day ">
                <div class="day">
                    <span>F</span>
                </div>
            </div>
            <div title="SAT" class="dmRespDesignCol medium-1 large-1 days day-border">
                <div class="day">
                    <span>Sa</span>
                </div>
            </div>
        </div>

        <div class="dmforminput small-12 dmRespDesignCol medium-12 large-12 direction-text">Select opening hours</div>
        <div class="dmforminput small-12 dmRespDesignCol medium-4 large-6">
            <label for="open">Open</label>
            <select name="open" id="open"> 
    <option>00:00</option><option>00:30</option><option>01:00</option><option>01:30</option><option>02:00</option><option>02:30</option><option>03:00</option><option>03:30</option><option>04:00</option><option>04:30</option><option>05:00</option><option>05:30</option><option>06:00</option><option>06:30</option><option>07:00</option><option>07:30</option><option>08:00</option><option>08:30</option><option>09:00</option><option>09:30</option><option>10:00</option><option>10:30</option><option>11:00</option><option>11:30</option><option>12:00</option><option>12:30</option><option>13:00</option><option>13:30</option><option>14:00</option><option>14:30</option><option>15:00</option><option>15:30</option><option>16:00</option><option>16:30</option><option>17:00</option><option>17:30</option><option>18:00</option><option>18:30</option><option>19:00</option><option>19:30</option><option>20:00</option><option>20:30</option><option>21:00</option><option>21:30</option><option>22:00</option><option>23:00</option><option>23:30</option><option>24:00</option>
    </select>
        </div>
        <div class="dmforminput small-12 dmRespDesignCol medium-4 large-6">
            <label for="close">Close</label>
            <select name="close" id="close"> 
    <option>00:00</option><option>00:30</option><option>01:00</option><option>01:30</option><option>02:00</option><option>02:30</option><option>03:00</option><option>03:30</option><option>04:00</option><option>04:30</option><option>05:00</option><option>05:30</option><option>06:00</option><option>06:30</option><option>07:00</option><option>07:30</option><option>08:00</option><option>08:30</option><option>09:00</option><option>09:30</option><option>10:00</option><option>10:30</option><option>11:00</option><option>11:30</option><option>12:00</option><option>12:30</option><option>13:00</option><option>13:30</option><option>14:00</option><option>14:30</option><option>15:00</option><option>15:30</option><option>16:00</option><option>16:30</option><option>17:00</option><option>17:30</option><option>18:00</option><option>18:30</option><option>19:00</option><option>19:30</option><option>20:00</option><option>20:30</option><option>21:00</option><option>21:30</option><option>22:00</option><option>23:00</option><option>23:30</option><option>24:00</option>
    </select>
        </div>
    </div>
    <h4 class="dmforminput small-12 dmRespDesignCol medium-12 large-12 section-title">SERVICES</h4>
    <div class="dmforminput small-12 dmRespDesignCol medium-12 large-12 direction-text">Select up to 6</div>
    <div class="dmforminput small-12 dmRespDesignCol medium-4 large-6">
        <div class="contact-checkable-container">
            <input name="service1" id="service1" type="checkbox" value="true" class="checkable-input">
            <label for="service1" class="for-checkable">
               <label for="service1" class="custom-contact-checkable"></label>
            <span class="service">Service 1</span>
            </label>
        </div>
        <div class="contact-checkable-container">
            <input name="service2" type="checkbox" value="true" id="service2" class="checkable-input">
            <label for="service2" class="for-checkable"> 
           <label for="service2" class="custom-contact-checkable"></label>
            <span class="service">Service 2</span>
            </label>
        </div>
        <div class="contact-checkable-container">
            <input name="service3" type="checkbox" value="true" id="service3" class="checkable-input">
            <label for="service3" class="for-checkable">
              <label for="service3" class="custom-contact-checkable"></label>
            <span class="service">Service 3</span>
            </label>
        </div>
    </div>
    <div class="dmforminput small-12 dmRespDesignCol medium-4 large-6">
        <div class="contact-checkable-container">
            <input name="service4" id="service4" type="checkbox" value="true" class="checkable-input">
            <label for="service4" class="for-checkable">
               <label for="service4" class="custom-contact-checkable"></label>
            <span class="service">Service 4</span>
            </label>
        </div>
        <div class="contact-checkable-container">
            <input name="service5" type="checkbox" value="true" id="service5" class="checkable-input">
            <label for="service5" class="for-checkable"> 
           <label for="service5" class="custom-contact-checkable"></label>
            <span class="service">Service 5</span>
            </label>
        </div>
        <div class="contact-checkable-container">
            <input name="service6" type="checkbox" value="true" id="service6" class="checkable-input">
            <label for="service6" class="for-checkable">
              <label for="service6" class="custom-contact-checkable"></label>
            <span class="service">Service 6</span>
            </label>
        </div>
    </div>

    <div class="dmforminput small-12 dmRespDesignCol required medium-12 large-12">
        <div class="optinwrapper">
            <div class="contact-checkable-container">
                <input type="checkbox" value="true" id="opt-in" class="checkable-input">
                <label for="opt-in" class="for-checkable">
                        <label for="opt-in" class="custom-contact-checkable"></label>
                <span class="service">By checking, I agree to share my form responses.</span>
                </label>
            </div>
        </div>
    </div>
    <div class="dmforminput small-12 dmRespDesignCol required medium-12 large-12">
        {{#custom_button "Generate My Site!" class="formButton"}} {{/custom_button}}
    </div>
</form>
```
{% endtab %}
{% endtabs %}

You'll notice the [Button Handlebars](../reference/handlebars-and-html.md#buttons) being used at the end of the HTML. This allows users to use Duda's standard classes and thus inherit all global styles for buttons on the website.

#### Javascript

In the Javascript section, place the following Javascript.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
let autocomplete;
dmAPI.loadScript('https://maps.googleapis.com/maps/api/js?key=GOOGLE_API_KEY&libraries=places', function() {
    var input = document.getElementById('address');
    autocomplete = new google.maps.places.Autocomplete(input);
})

$(document).on("click", ".days", function() {
    $(this).toggleClass('selected-day')
});

const thisForm = document.getElementById('myForm');
$(".formButton").click(function() {
    var formData = new FormData(thisForm)
    var formObject = createLibraryObject(formData)
    var businessHours = getHoursArry(formObject)
    var services = getServices(formObject)
    var address = formObject.address.split(', ')
    var body = {
        "site_data": {
            "location_data": {
                "phones": [{
                    "phoneNumber": formObject.tel.replace(/(\d{3})(\d{3})(\d{4})/, '($1) $2-$3'),
                    "label": "Office"
                }],
                "emails": [{
                    "emailAddress": formObject.email,
                    "label": "Office"
                }],
                "business_hours": businessHours,
                "address": {
                    "streetAddress": address[0],
                    "region": address[2],
                    "city": address[1],
                    "country": address[3]
                }
            },
            "site_texts": {
                "custom": [{
                    "label": "Services",
                    "text": services.join(', ')
                }]
            },
            "business_data": {
                "name": formObject.name
            }
        }
    }

    const response = fetch('API_ENDPOINT', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(body)
        }).then(response => response.json())
        .then(data => {
            console.log('Success:', data);
        })

});


function createLibraryObject(form) {
    var formInputs = {}
    for (var input of form.entries()) {
        formInputs[input[0]] = input[1]
    }
    return formInputs;
}

function getHoursArry(formData) {
    var selectedDays = $('.selected-day')
    var busHrsArry = [{
    	"days": [],
    	"open": '',
    	"close": ''
		}]

    for (i = 0; i < selectedDays.length; i++) {
        var day = selectedDays[i].attributes.title.value
        busHrsArry[0].days.push(day)
    }
        var openHrs = formData['open']
        var closingHrs = formData['close']
        busHrsArry[0].open = openHrs
        busHrsArry[0].close = closingHrs

    busHrsArry = busHrsArry.filter(function(element) {
        return element.days.length > 0;
    })
    return busHrsArry;
}

function getServices(formData) {
		var serviceArry = ['service1', 'service2', 'service3', 'service4', 'service5', 'service6']
    var selectedServices = []
    for (i = 0; i < serviceArry.length; i++) {
        var service = serviceArry[i]
        if (formData[service] === 'true') {
            selectedServices.push(service)
        }
    }
    return selectedServices;
}
```
{% endtab %}
{% endtabs %}

This form widget uses the [Autocomplete](https://developers.google.com/maps/documentation/javascript/places-autocomplete) feature of the Places library in the Google Maps JavaScript API. To use this feature, replace the `GOOGLE_API_KEY` placeholder on line 2 with your [Google API Key](https://developers.google.com/maps/documentation/javascript/places-autocomplete#get-started).

If you wish to exclude this functionality from your widget, remove lines 1-5.

This form collects business information from an end-user and makes an API call with the completed form data. To have this information passed over to your API, update the API endpoint placeholder on line 49 with the URL that will receive this data.

#### CSS

In the CSS section, place the following CSS. This will give the widget its structure and make sure everything fits in the correct place.

{% tabs %}
{% tab title="CSS" %}
```css
.day-border {
    display: flex !important;
    justify-content: center;
    align-items: center;
    width: 60px !important;
    height: 60px !important;
    margin-right: 24px !important;
}


.dmforminput > label{
    font-family: Nunito Sans !important;
    font-style: normal;
    font-weight: normal;
    font-size: 16px !important;
    line-height: 23px !important;
    color: #161D26 !important;
    margin-bottom: 10px !important;
}

.direction-text{
  margin-bottom: 20px !important;  
}

input[name="name"], input[name="tel"], input[name="email"], input[name="address"], select{
    border: 1px solid rgba(27, 35, 49, 0.304797) !important;
    border-radius: 3px !important;
    margin-bottom: 20px !important;
    font-family: Nunito Sans !important;
    font-style: normal;
    font-weight: normal;
    font-size: 16px !important;
    line-height: 23px !important;
    color: #161D26 !important;
    background: #FFFFFF !important;
    height: 55px !important;
}

.selected-day {
    border: 3px solid #1B2331 !important;
    border-radius: 28px;
}

.dayButtons{
    margin-bottom: 34px !important;
}

.section-title{
    margin-top: 24px;
    margin-bottom: 16px !important;
}

.day {
    display: flex !important;
    justify-content: center;
    align-items: center;
    width: 50px !important;
    height: 50px !important;
    border: 1px solid rgba(27, 35, 49, 0.304797);
    box-sizing: border-box;
    border-radius: 25px;
}

.day > span{
    font-family: Nunito Sans !important;
    font-style: normal;
    font-weight: 800 !important;
    font-size: 20px !important;
    line-height: 23px !important;
    text-align: center;
    color: #161D26 !important;
}

.optinwrapper > .contact-checkable-container, .optinwrapper > .contact-checkable-container input[type=checkbox].checkable-input+label .custom-contact-checkable::before{
    background: #FFFFFF !important;
}

.contact-checkable-container {
    background: #E5E5E5;
    height: 50px;
    margin: 15px 0 !important;
    padding: 20px 0px 20px 20px !important;
    height: 65px !important;
}

.service{
    font-family: Nunito Sans !important;
    font-style: normal;
    font-weight: normal !important;
    font-size: 16px !important;
    color: #161D26 !important;
    line-height: 25px !important;
}

.contact-checkable-container input[type=checkbox].checkable-input+label .custom-contact-checkable::before {
    width: 21px;
    height: 21px;
    border: 1px solid rgba(22, 29, 38, .4) !important;
    background: #E5E5E5 !important;
    border-radius: 3px;
    margin-right: 15px !important;
    margin: 0px;
    padding: 2px !important;
    box-shadow: none !important;
}

.contact-checkable-container input[type=checkbox].checkable-input:checked+label .custom-contact-checkable::before {
    content: '\2713' !important;
    font-family: system-ui !important;
    background: black !important;
    border: 1px solid black !important;
    color: white !important;
    box-shadow: none !important;
}

.optinwrapper > .contact-checkable-container {
    padding-left: 0px !important;
}
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

### 2. Create Design Options

For the last part of the widget, we need to set up the design input options. We'll have five total to allow design control over the widget. You'll notice familiar CSS classes that we assigned originally in the widget's HTML code.

#### Day Border Color

* **Type**: Color Picker
* **Descriptive Label**: Day Border Color
* **Toggle Selection**: Use CSS
* **CSS Property**: border-color
* **Selector**: `.day`

#### Selected Day Border Color

* **Type**: Color Picker
* **Descriptive Label**: Selected Day Border Color
* **Toggle Selection**: Use CSS
* **CSS Property**: border-color
* **Selector**: `.selected-day`

Since there are a large number of content options, we can use the [divider content input](../reference/content-editor.md#divider) here to help organize the content options.

#### Form Section Titles

* **Type**: Text Style
* **Descriptive Label**: Section Titles
* **Selector**: `.section-title`

#### Form SubSection Descriptions

* **Type**: Text Style
* **Descriptive Label**: SubSection Descriptions
* **Selector**: `.direction-text`

#### Submit Button Design

* **Type**: Button
* **Descriptive Label**: Submit Button
* **Selector**: `.formButton`

### Preview

If done correctly, you can now preview your widget and [publish](../concepts/widget-builder-overview.md#publishing) if you feel it's ready to go live.
