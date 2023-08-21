# Connected Data

Connected data offers a way to connect individual pieces of content to the design of a website. This enables a single change in data to propagate to multiple places throughout a site. For example, an edit to a business phone number in a site's Content Library, can automatically update the contact info in the footer, a click to call widget in the header, and individual page content where the number is being displayed.

### Content Library

Duda’s Content Library acts as a central location where you can store all of a client’s business information, such as their name, address, business hours, about us statements, and so on. It also allows you to save other pieces of data you might use as website content like long-form text and images. You can think of the Content Library as a key-value store, where some keys are predefined and others are created by you.

The Content Library is accessed from the **Content** tab in the side panel of the editor. There are four sections in the Library that come into play when working with Connected Data. They are:

| Content Library Sections | Description                                                                                                                                                                                        |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Business Info            | Contains all standard information for a business. For example, address, phone number, email, and social accounts. A site can contain multiple addresses, phone numbers, and email addresses.       |
| Business Text            | Text blocks related to the site. By default each site comes with 3 text blocks (About Us, Company Overview + Business Services). An unlimited number of custom text blocks can be added to a site. |
| Business Images          | All images related to the site. An unlimited number of custom images can be added to a site. Note: the business logo can be uploaded to the Business Info screen.                                  |
| Collections              | Collections can contain multiple items of some similar type of data. A collection is useful when working with a widget that accepts multiple pieces of data (ex. Image gallery)                    |

### Connected Elements

Many widgets in Duda can be connected to the data that resides in the Content Library. Any changes to the info in the Content Library will update the content of the widgets connected to the field. This connection is shown in the editor with a blue icon on hover of the connected element. Keep in mind that multiple widgets can be connected to the same field in the Content Library.

Assuming content has been added to the Library, a **Connect to Data** option will appear in the menu when right-clicking a widget. After selecting the option, a popup will display all the relevant pieces of content from the Content Library. Selecting the data you'd like to use as content will connect the widget.

<figure><img src="https://files.readme.io/8f68eb6-connected.gif" alt=""><figcaption></figcaption></figure>

### Connected Templates

The same connection options are available when creating templates as well as sites. By connecting widgets in a template and providing placeholder data to the Content Library, it's very easy to generate new sites. When creating a new site from a template, not only is the design copied, but also the Content Library and data connections to widgets. To personalize a site for a customer, simply select your connected template as the base for the new site and update the content in the Content Library.

This is a key concept in creating and managing a large number of sites. The Duda Partner API provides the ability to update the content library through an API endpoint. This content endpoint, when combined with other API endpoints allows the programmatic generation of websites at scale.
