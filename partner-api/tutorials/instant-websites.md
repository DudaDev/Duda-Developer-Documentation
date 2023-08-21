# Instant Websites

This guide will walk you through how to work with instant websites on the Duda platform via the API. If Instant Websites are unfamiliar to you, then check out our [Resource Center article](https://support.duda.co/hc/en-us/articles/360042934213-Connected-Data). We will cover creating instant websites through the API as well as how to push content to an individual site.

### Requirements

To work with this guide, you’ll need to make sure you have the following items ready:

* Your Duda API key and password. Learn how to gain API access [here](../../#api-credentials).
* Using the Duda API to create a website. If you aren't familiar with this you can learn more in the [Do It Yourself](../how-to-guides/do-it-yourself.md).

### 1. Build Connected Template

A connected template is a custom site template that connects pieces of the website to the content library. An example is a text element holding the phone number. To learn more about creating a connected template read our [resource center article](https://support.duda.co/hc/en-us/articles/360042934213-Connected-Data#Connected%20Templates).

Once the connected template is built you can retrieve the `template_id` from the [GET /sites/multiscreen/templates](../../reference/partner-api-reference/templates.md#list-templates-1) API endpoint. This is important for the next step.

### 2. Create Site

Now that the connected template is built you are ready to create your first site using this template. When creating a site via the Duda API you can pass an optional parameter of `template_id`. Use the template id found in step 1. This will create a brand new Duda site that has the same connections as the template.

If you need a refresher on how to use our API to create a site and grant a customer access, then check out the first three steps of our [Do It Yourself](../how-to-guides/do-it-yourself.md) guide.

### 3. Collecting Data

The good news is many Duda partners already have information on their prospects and customers. This data might be stored in a database or CRM. Using what we learned in Steps 1-3, you can automatically create a site and push existing content to that site.

Optionally you can create a custom form to have a sales representative or customer fill out a form. The data collected in the form can be pushed to the content library of the newly created site. An example form is pictured below:

<figure><img src="https://files.readme.io/a1d64bc-ScreenShot2018-10-30at5.08.44PM.png" alt=""><figcaption></figcaption></figure>

### 4. Push Data

The advantage of an Instant Website is the ability to automatically populate the website with content via the API. This is possible through the Site's Content Library. Using the Content API you can retrieve and update the content library. Here is an example how to retrieve the content of an existing site.



{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \ 
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/sites/multiscreen/{site_name}/content
```


{% endtab %}

{% tab title="JSON - Response" %}
```json
{
   "location_data": {
        "phones": [
            {
                "phoneNumber": "xxx-xxx-xxxx",
                "label": "Main Phone Number"
            }
        ],
        "emails": [
            {
                "emailAddress": "sales@duda.co",
                "label": "Sales Email"
            },
            {
                "emailAddress": "support@duda.co",
                "label": "Support Email"
            }
        ],
        "label": "Duda HQ",
        "social_accounts": {
            "facebook": "duda",
            "linkedin": "duda",
            "vimeo": "dudamobile",
            "reddit": "duda"
        },
        "address": {
            "streetAddress": "577 College Ave",
            "postalCode": "94306",
            "region":"CA",
            "city": "Palo Alto",
            "country": "US"
        },
        "geo": {
            "longitude": "-122.4757527166",
            "latitude": "37.502439189002"
        },
        "logo_url": "",
        "business_hours": []
    },
    "additional_locations": [],
    "site_texts": {
        "overview": "Oh, Duda? Duda is a variation of \"Dude\", who just happens to be the main character in one of our favorite movies of all time: The Big Lebowski. You should watch it some time. Look out for that ferret!",
        "services": "- Responsive Website Builder",
        "custom": [
            {
                "label": "Example CTA 1",
                "text": "THE WEB DESIGN PLATFORM FOR Scaling Your Agency"
            },
            {
                "label": "Example CTA 2",
                "text": "THE WEB DESIGN PLATFORM FOR\nBuilding Websites Faster"
            }
        ],
        "about_us": "Duda is a leading website builder for web professionals and agencies of all sizes."
    },
    "business_data": {
        "name": "Duda",
        "logo_url": "https://www.duda.co/developers/REST-API-Reference/images/duda.svg"
    },
    "site_images": []
}
```
{% endtab %}
{% endtabs %}

Here's an example of how to update the content library via the API

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST -k 'https://api.duda.co/api/sites/multiscreen/{site_name}/content' 
-u 'xxxx:xxxxxx' \
-d '"location_data": {"phones": [ "phoneNumber": "800-123-4567", "label": "Main Phone Number"] }'
```
{% endtab %}
{% endtabs %}

This call will update the Main Phone Number to 800-123-4567. Once this call is executed any element of the website connected to the Main Phone Number in the content library will update automatically. The screenshot below shows how a connected element displays in the editor.

<figure><img src="https://files.readme.io/67ec588-ScreenShot2018-10-30at5.00.30PM.png" alt=""><figcaption></figcaption></figure>

Any component of the content library can be updated this way. This includes phone numbers, email addresses, contact address, social accounts, business hours, company logo, gallery images, etc...

{% hint style="info" %}
**Good to know: Content Only Site Publish**

When updating the content library for a published site use the [POST /api/sites/multiscreen/{site\_name}/content/publish](../../reference/partner-api-reference/site-content.md#publish-content-library-3) API call to only push the content library changes to the published site.\

{% endhint %}
