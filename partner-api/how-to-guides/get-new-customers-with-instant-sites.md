---
description: A step-by-step guide on how to build Instant Sites for a PPC campaign.
---

# Get New Customers With Instant Sites

This guide explains how to create a high converting, pay-per-click ad campaign using Instant Sites.

In this example, we are focusing on a specific use case where you promote your website building service using an ad campaign that targets a specific business type, such as a vet clinic or nail salon. Your ad will ask prospects to fill out a form with their business information in order to receive a preview of what their website could look like. After the prospect fills out the form, an automated email is sent to them with a link to preview their site and your contact information. If the prospect likes what they see, they can call you to take their site live.

The benefit to using our Instant Sites feature for a campaign like this is that it creates a demand generation channel and it can help you scale your business. It also drives higher conversion by allowing you to show a beautiful website instead of just telling prospects about how you can build them a website.

To create your campaign, you will follow these general steps:

1. Create a connected template that connects widgets to the Content Library.
2. Build a form for prospects to fill out and host it on a landing page that you can link to from your ad.
3. Use the API to create a new site from the template you built previously.
4. Collect data from the form you created.
5. Push data from the form to the Content Library, which will then populate a new site using your template.
6. Use your preferred mail provider to send prospects an email with a link to preview their site.
7. Create and launch your ad campaign. Once that is complete, all you have to do is sit back and wait for calls from prospects to start coming in.

{% hint style="warning" %}
**Heads up: API Access Required**

You need API access to use this guide. To upgrade your plan to get API access, [schedule time with our team](https://calendar.google.com/calendar/u/0?cid=Y2FtZXJvbkBkdWRhLmNv).
{% endhint %}

### 1. Build Connected Template

A connected template is a custom site template that connects widgets to the Content Library. The benefit to using a connected template for this use case is that you only need to build a template once. Then as prospects fill out your form, their website will be generated within minutes.

To build a connected template you first have to create a site template, populate the Content Library with placeholder data, and then connect widgets to the Content Library. To learn more about connected templates, see [Connected Data](https://support.duda.co/hc/en-us/articles/1500001598102).

#### Create Site Template

To create a site template:

1. Log in to your account to access the Dashboard.
2. Click **Create a Responsive Site**.
3. At the top of the page, click **Create Template**.
4. Select one of the existing templates to customize. This template serves as a starting point for your design.
5. Type a Template name in the field.
6. Customize your site in the editor as usual. When you are finished making changes, click **Done**.

The new template will appear in the “Team Templates” section.

#### Populate Content Library

You need to populate the Content Library with placeholder data before you can connect widgets to the Content Library. For information on what types of data you can connect to the widgets on your site, see the Connect Data section of [Connected Data](https://support.duda.co/hc/en-us/articles/1500001598102).

Use the [Update Content Library](../../reference/partner-api-reference/site-content.md#update-content-library-1) call to push placeholder data to the Content Library.

#### Connect Widgets to Content Library

To connect widgets to the Content Library:

1. Right-click the widget you want to connect to a data field.
2. From the context menu, click **Connect to data**.
3. In the Connect Data dialog, select the data field that you want to connect this widget to.
4. When a widget has successfully connected to data in the Content Library, it is marked with a blue Connected Data icon.

{% hint style="info" %}
**Good to know: Connected Data & Text Styles**

If you are connecting text data, the text inherits Global Text styles. In order to change the text style, go to the widget’s design editor. The inline text editing menu is not available for text widgets that are connected.
{% endhint %}

#### Retrieve Template ID

Now that you have built your connected template, you can retrieve the `template_id` from the [List Templates API endpoint](../../reference/partner-api-reference/templates.md#list-templates-1). This is important for step 3.

### 2. Create Custom Form and Landing Page

#### Create Custom Form Widget

You will need a form to collect your prospect's information. The data collected in the form can be pushed to the Content Library and used to create a new site. Follow our [Building a Custom Form Widget](../../custom-widgets/how-to-guides/build-a-custom-form-widget.md) guide to learn how to make a great form.

#### Create Landing Page for Widget

Create a landing page to host the form created in the previous step. This can be hosted on Duda or an external website.

To create a site from the Duda dashboard:

1. From the dashboard, click **Create a Responsive Site**.
2. Point to a template in the list, and click **Start Building**. Alternatively, to use an existing template to create your own template, click **Create Template**.
3. _(Optional)_ Type a name for the site.
4. Click **Start Building**.
5. Add the form to your site and customize the site design as needed.
6. Publish your site. For more information on taking your site live, see [Go Live, Publish, and Setup Your Domain](https://support.duda.co/hc/en-us/articles/360060106454-Go-Live-Publish-and-Set-Up-Your-Domain).

When you create your ad campaign, this is the page you will link to for prospects to fill out your form.

### 3. Create Site

Now that the connected template is built, you are ready to create your first site using the template. When creating a site using the Duda API you can pass a parameter of `template_id`. This creates a brand new Duda site that has the same connections to the Content Library as the template. Use the `template_id` from the template created in [Step 1](get-new-customers-with-instant-sites.md#1.-build-connected-template).

If you need help learning how to use our API to create a site, then check out the first three steps of our [Do It Yourself](do-it-yourself.md) guide.

### 4. Collect Data

Enter fictional data in your form so that in the next step you can verify if the content is being pushed to the correct places in your template. Once your campaign is live, this is when data from prospects filling out your form will be collected.

### 5. Push Data

Use the [Update Content Library](../../reference/partner-api-reference/site-content.md#update-content-library-1) API call to update the Content Library with content that is entered into your form.

Here is an example of how to update the Content Library using the API:

{% tabs %}
{% tab title="curl" %}
```shell
curl -X POST -k 'https://api.duda.co/api/sites/multiscreen/{site_name}/content' 
-u 'xxxx:xxxxxx' \
-d '"location_data": {"phones": [ "phoneNumber": "800-123-4567", "label": "Main Phone Number"] }'
```
{% endtab %}
{% endtabs %}

This call will update the main phone number to `800-123-4567`. Once this call is executed, any widget on the website that is connected to the main phone number in the Content Library will update automatically. Any widget connected to the Content Library can be updated this way. This includes phone numbers, email addresses, contact address, social accounts, business hours, company logo, gallery images, and so on.

### 6. Set Up Mail Provider

You need to set up a mail provider so you can automate the process of sending prospects emails with links to their website previews. Additionally, you can collect and store email addresses from prospects for future campaigns.

For this guide we used Mailchimp, but you can use any mail provider you like. For information on how to use the Mailchimp API to add a contact, see [Members](https://mailchimp.com/developer/marketing/api/list-members/). For information on how to use the Mailchimp API to send an email, see [Send using message template](https://mailchimp.com/developer/transactional/api/messages/send-using-message-template/).

{% hint style="warning" %}
**Heads up: Hosting API Calls**

The Duda API and Mailchimp API calls mentioned in this guide need to be made from the server-side.

Once you have finished setting up your flow, push it up to your preferred server service, such as AWS, Google, or Digital Ocean.
{% endhint %}

### 7. Create Ad Campaign

For this guide we used Facebook to create and run our ad campaign, however you can use other ad services such as Google. If you are using Facebook to create your campaign, see [Create a Campaign in Ad Manager](https://www.facebook.com/business/help/621956575422138?id=649869995454285). If you are using Google, see [Create a Campaign](https://support.google.com/google-ads/answer/6324971?hl=en).

Once your campaign is live, you can sit back and wait for calls from prospects to come in!
