# Dynamic Pages

Dynamic pages is the capability of generating many pages of a website based on structured content that lives within a [collection](collections.md).

The high-level steps to create dynamic pages are as follows:

* [Create a collection](../../reference/partner-api-reference/collections.md). The collection should contain fields (similar to columns) of each dynamic piece of information you want to change on each version of the page that will be generated.
* Create & Design a dynamic page. Dynamic pages are always connected to a collection. As you design the dynamic page, you will connect widgets within that dynamic page to data elements
* Create a ‘list’ or ‘category’ page which deep links into each page of the dynamic pages. This is done by using either a list or gallery widget which displays all rows (items) within the collection and deep links to the specific pages.

<figure><img src="https://files.readme.io/f3bf3e5-image1.png" alt="1999"><figcaption><p>Flow of collection content into real pages</p></figcaption></figure>

**To use this guide successfully, you will need the following information:**

* Your Duda API User & Password
* A tool to make API calls (Postman, cURL via terminal, etc..)
* A location to host JSON files with data

For this guide, we will be creating pages for an artist that is currently on tour. For each concert or event, we want to create a specific page that contains all the details about that event, such as venue location, where tickets can be purchased, start time, etc..

### Creating a Collection

Follow this link to learn more about [creating a collection](../../reference/partner-api-reference/collections.md).

{% hint style="info" %}
**Good to know:** Dynamic Pages can be powered by internal and external collections. As well as collections pulling from Google Sheets and Airtable
{% endhint %}

### Provide Page Item URL

Because we want to turn the collection rows into pages within a site, we must provide a field in each row that specifies what the URL slug is for that page. This special field is called `page_item_url`.

For example a `page_item_url` of 'columbus' produces a web page that lives at `yoursite.com/<dynamic_folder_name>/columbus`. Note: \<dynamic\_folder\_name> is specified in the Duda editor. The `page_item_url` parameter must be formatted as a string and only supports lowercase characters, numbers, dashes and underscores.

Here’s example JSON that populates data related to events:

{% tabs %}
{% tab title="JSON" %}
```json
[
  {
    "page_item_url":"columbus",
    "data": {
      "details": "w/ Jess Glynne",
      "formatted-address": "Columbus, OH",
      "is-sold-out":"No",
      "link-text-1": "Tickets",
      "link-url-1": "https://link.seated.columbusom/198b2048-f3db-4c83-b2ee-5a0b8d76b380",
      "starts-at-short": "May 4, 2019",
      "venue-name": "EXPRESS LIVE! ",
      "event-image": "https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?ixlib=rb-1.2.1&auto=format&fit=crop&w=3150&q=80"
    }
  },
  {
    "page_item_url":"tokyo",
    "data": {
      "details": "Leon Bridges is going big in Japan!",
      "formatted-address": "Tokyo, Japan",
      "is-sold-out":"No",
      "link-text-1": "Tickets here",
      "link-url-1": "https://www.liquidroom.net/schedule/leonbridges20190524",
      "starts-at-short": "May 24, 2019",
      "venue-name": "Ebisu Liquidroom",
      "event-image": "https://images.unsplash.com/photo-1508700115892-45ecd05ae2ad?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80"
    }
  },
  {
    "page_item_url":"watkins-glen",
    "data": {
      "details": "Leon Bridges is going big in Japan!",
      "formatted-address": "Watkins Glen, NY",
      "is-sold-out":"No",
      "link-text-1": "Tickets here",
      "link-url-1": "https://www.woodstock.com/",
      "starts-at-short": "Aug 17, 2019",
      "venue-name": "Woodstock",
      "event-image": "https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?ixlib=rb-1.2.1&auto=format&fit=crop&w=1650&q=80"
    }
  },
  {
    "page_item_url":"franklin",
    "data": {
      "details": "Leon is heading to the volunteer state for the pilgrimage festival!",
      "formatted-address": "Franklin, TN",
      "is-sold-out":"No",
      "link-text-1": "Tickets here",
      "link-url-1": "https://pilgrimagefestival.com/",
      "starts-at-short": "Sep 21, 2019",
      "venue-name": "Pilgrimage Music & Cultural Festival",
      "event-image": "https://images.unsplash.com/photo-1444623151656-030273ddb785?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80"
    }
  }
]
```
{% endtab %}
{% endtabs %}

You can specify a static JSON file as our endpoint; however, you can also provide any URL as long as it returns JSON. The structure of the JSON file is an array of objects, where each object is a row of the collection.

{% hint style="info" %}
**Good to know:** If you’d like to use this example, we have uploaded for you to use: [https://dm-util.s3.amazonaws.com/russ/dynamic-pages/dynamic-pages-tour.json](https://dm-util.s3.amazonaws.com/russ/dynamic-pages/dynamic-pages-tour.json)
{% endhint %}

### Creating the Dynamic Page

Now that we have the data ready within Duda, it’s time to create a dynamic page to generate all the pages from data within the collection. The first step will be to add a new page to the website. When doing that, follow these steps:

* Add a new page to the site
* Choose the dynamic page option
* Choose a template, enter a page name (in our example, I use tour-2019). This means the subfolder in the URL becomes `tour-2019`.
* Choose the related collection that will be connected to the dynamic page

<figure><img src="https://files.readme.io/5d95dfb-add-new-page2.gif" alt="1000"><figcaption><p>Example of adding new dynamic page</p></figcaption></figure>

To convert an existing page to a Dynamic Page, open the pages panel, click the gear icon and select ‘Convert to Dynamic Page’.

<figure><img src="https://files.readme.io/39c7aa2-convert.gif" alt="1000"><figcaption><p>Example of converting regular page to dynamic</p></figcaption></figure>

After the page is created, you will want to add widgets to the page and use the [connected data feature to connect widgets](https://support.duda.co/hc/en-us/articles/360042934213-Connected-Data) of the page to fields within the dynamic page. You can also build custom widgets using the widget builder.

<figure><img src="https://files.readme.io/fe44b3a-doc-02.gif" alt="1000"><figcaption><p>Connecting widgets to the collection data</p></figcaption></figure>

After connecting all the widgets, you can view the different pages generated from the dynamic page. Go to the top bar and click the page item name to view the pages displaying the different content.

<figure><img src="https://files.readme.io/81f657e-page-items2.gif" alt="1000"><figcaption><p>In the top bar click the page item name to view the pages displaying different content</p></figcaption></figure>

### SEO Setup(optional)

Once you've finished connecting the widgets on your page and designing it, the last step (that's optional) is to make sure that you update the SEO fields of the page with connected data. To do this, navigate to the dynamic page settings (under the gear icon), choose ‘SEO’ and use connected data to connect the dynamic page title and page description to fields in your collection.

<figure><img src="https://files.readme.io/b8d4d5c-doc-03.gif" alt="1000"><figcaption><p>Making page title &#x26; description dynamic with the dynamic page content</p></figcaption></figure>

### Add List /category page

The final step in setting up dynamic pages is creating a list of links so users can navigate and find the right content within the website. This is often called a category or list page. This is can be done two different ways.

#### Native Duda Widget

Duda provides two widgets that displays data from a collection. These are the List and Photo Gallery widgets. You can try connecting the concert collection we created to the photo gallery widget as shown below. In the 'Connect Data' popup under 'Connect Link', make sure to select the dynamic page you created.

<figure><img src="https://files.readme.io/860647e-doc-04b.gif" alt="1000"><figcaption><p>Example of connecting a collection to a photo gallery to display the tour list</p></figcaption></figure>

#### Custom Widget

Often times you will want to build your own custom widget to connect to a collection and display each row. In order to do this you can use Duda's `getCollection` JS function. You can see it documented below.

{% hint style="info" %}
**Good to know:** In order to connect a custom widget to a collection you must [enable the widget to use Connected Data](../../custom-widgets/reference/content-editor.md#connected-data).
{% endhint %}

{% tabs %}
{% tab title="Javascript" %}
```javascript
function(element, data, api) {
	api.collections
		.getCollection({ collectionName: ‘tour’ })
		.then(results => {
  		console.log(results);
		})
		.catch(error => {
			console.log(error);
		});
}
```


{% endtab %}
{% endtabs %}

Additionally Duda's JS API offers a generic `getCollection` method that can be called from any page without the need to connect the custom widget. See the documentation for this method [here](../../javascript-api/live-site-js-reference.md#getcollection)

Now that you've set up each step, you've officially set up dynamic pages on your website.

### Supported Widgets

These are the and the data types they support. You can also build custom widgets using [the widget builder](../../custom-widgets/concepts/widget-builder-overview.md).

| Widget                                    | Data Type                                                             |
| ----------------------------------------- | --------------------------------------------------------------------- |
| <p>Text widgets<br>(title, paragraph)</p> | Text, Email, Phone, Location                                          |
| Image widget                              | Image                                                                 |
| Button                                    | Text, Link, Phone, Email                                              |
| Map                                       | Location                                                              |
| Business hours                            | Business hours                                                        |
| Video                                     | Video link - YouTube, Vimeo or Dailymotion                            |
| Photo Gallery                             | Images, texts (title and description), alt-texts and links link text. |
| Image Slider                              | Images, texts (title and description), alt-texts and links link text. |
| List Widget                               | Images, texts (title and description), alt-texts and links link text. |
| Background Row/Column                     | Image, Image Collection                                               |
