# Creating and Using Collections in the Duda Editor

Collections allow site administrators to separate the maintenance of list-style content from the design of the site. They can be used to create a simple editing experience for less technical authors or to pull data from an external source for display on a published site.

### Objective and Outcomes

In this tutorial you will learn the value and purpose of collections when it comes to managing website content and you will understand the differences between internal and external collections. To do this, you will create and connect both external and internal collections to a website. The principles covered by this tutorial will help you when connecting any external data source to a Duda website.

### 1. Create a New Site

Log into your Duda account and create a new site. You may select any template as your starting point, but we recommend choosing a simple template such as the 'empty' template.

### 2. Create a New Internal Collection

Select **Content** from the editor sidebar then open the **Collections** tab. Click **New Collection** then click the **Internal Collection** icon. The editor creates a new collection named _Collection-01_. You can change the name of this collection by clicking anywhere in the title area. For now, delete the current name and name it _Internal Collection_.

Internal collections operate similarly to a spreadsheet. You can add columns (referred to as fields in Duda) of related data types. Rows of data can then be added to populate those types. A new internal collection starts with two fields, a mandatory **item** field, and an editable rich text field named **New Field**. Click the header of the New Field column. A modal appears that allows you to change the name and the data type of the field. Change the name to _Title_ and change the type to **Plain Text**. Once the changes are made, click **Save**.

Click the plus icon to the right of the column you just edited to create an additional field. Again you will be presented with a modal to change the name and type of the field. Edit the field as before, this time name the field _Description_ and change the type to **Rich Text**.

With the structure of your simple collection complete, you are ready to add data. Click **Add Row** and a form that matches the structure you just created appears. Edit the item field to have a value of _item-one_. Enter a title and then enter a sentence or two in the description field. Optionally, you can format the text of your description by using the toolbar above the rich text field. The data you enter is saved automatically. Click the **X** icon to close the form.

Add additional rows to your collection by following the same steps. The values for the title and description are arbitrary, but the item field must be unique for each row and only contain lowercase characters, numbers, dashes, and underscores.

### 3. Connect the Internal Collection to a Widget

Only certain widgets are able to be connected to a collection, these include the Accordion widget, List widget, Photo Gallery widget and Image Slider widget. Connecting these widgets to a collection is a two step process. First, select the collection to pull data into and then select the individual fields in your collection that will populate the content of the widget.

Select the **Widgets** tab from the editor sidebar and search for the **Accordion** widget. Drag and drop the widget onto the site to create a new instance of the widget. The **Accordion Content** panel will appear automatically (if you don't see the panel, click anywhere on the widget).Click the gear icon from the panel header and select **Connect to data** from the menu.

The **Connect Data** modal will display a dropdown populated with the list of collections you have created. Select **Internal Collection**. The widget is now connected to the internal collection you just created. The Accordion widget has two areas available to display content from your collection rows. **Description** is the area that is hidden in the accordion, which expands when the **Title** area is clicked. After selecting the collection, additional fields appear where you can choose which fields should be used as content for each of these areas. Select Title for the title area and **Description** for the description area. Click **Done** to complete the connection.

The values from the internal collection populate the widget. Open the collections UI and try editing your values or adding additional rows. You'll notice the widget will update itself with the new content. This is a great way to provide an easy-to-use UI for managing site content, without worrying about accidental editing of the site design.

### 4. Create a New External Collection

External collections allow you to connect a collection to an external data source and use that data as content for the site. The external data must be publicly accessible and in JSON format. The data is cached by Duda and rechecked for updates roughly every hour or two. Although, this can be revalidated manually via API.

You’ll create a new collection based on the [quotable API](https://github.com/lukePeavey/quotable), a free service that manages thousands of quotes, tagged by category. Creating an external collection is similar to creating internal collections, the paths only differ when comparing the source of data. Internal collections are managed via the collection UI within the editor, while external collections have their data managed elsewhere. Duda is simply connecting to a location that exposes the data.

While editing the same site that was used to create the internal collection, select the **Content** tab from the editor sidebar, then click **Collections**. Click **New Collection** above your existing internal collection and click the **External Database** icon.

As previously mentioned, you’re going to use a public endpoint for the quotable API. You are going to request the first fifty quotes tagged as 'technology'. Before you complete the collection details, let's have a look at the structure of the data returned by the API. Paste the following URL into a new tab in your browser:

[https://api.quotable.io/quotes?tags=technology\&limit=50](https://api.quotable.io/quotes?tags=technology\&limit=50)

The endpoint returns a JSON object that contains some metadata about the request, along with the results of the query.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "count":48,
  "totalCount":48,
  "page":1,
  "totalPages":1,
  "lastItemIndex":null,
  "results": [{
    "tags": ["technology"],
    "_id":"JxE5YMTDIK",
    "content": "Technology is a word that describes something that doesn’t work yet.",
    "author":"Douglas Adams",
    "authorSlug":"douglas-adams",
    "length":68,
    "dateAdded":"2021-03-28",
    "dateModified":"2021-03-28"
  }, {
    …
  }]
}
```
{% endtab %}
{% endtabs %}

Pay particular attention to the list of quotes. You will see that the array is nested within a **results** property of the JSON object. Now that you’re familiar with the structure of the JSON, you’re ready to complete the collection.

After selecting the external database option while creating the collection, a form appears where you enter the **Endpoint URL** for your data. Paste in the URL provided above to the quotable API.

Expand the **Define the collection path inside the endpoint** option by clicking the text or the disclosure arrow to the right. This is where you define a dot delimited path to the results within the JSON response. Your quotes can be found within the _results_ property. That will be the value of the text field.

Next, click **Fetch Collection**. The editor will attempt to fetch the data using the values provided and display the first result returned. Below the data, you'll see a dropdown to select the **Page item URL**. Select which property should act as your item key, similar to the item field in your internal collection. The value of this property must follow the same rules as your internal collection; each value should be unique and contain only lowercase letters, numbers, underscores, and dashes. For our purposes, the \_id field in the result set will work nicely as the value. After selecting the property, verify the data looks correct and then click the **Create Collection** link.

The second step in creating an external collection consists of choosing the correct data type for each property. For our simple example, you may choose **Rich Text** or **Plain Text** for all the properties. More complex setups will require you to match the data type to the value, such as number, image, or inner collection. Above the data types, you can also enter a new collection name by selecting the heading text. Delete the generic name and type _External Collection_ before clicking **Done**.

### 5. Connect the External Collection to a Widget

To connect a widget to the external collection, follow the same steps as connecting the internal collection in step 3. This time drag a **List** widget to the site. Click the gear icon at the top of the **List Content** panel (click anywhere on the list widget if you don't see the content panel) and select **Connect to data** from the menu.

Select **External Collection** from the collection dropdown. The List widget has more areas available to display content than the Accordion widget had, however you won't be able to select fields for all the areas. This is because you don't have any properties of type image or link in your collection. Because of this, the dropdowns for **Image** and **Link** will be disabled. Since you don't have a value for the link, you don’t need to select a value for the **Link Text** option. For the **Title** content, select **author** and then select **content** for the **Description** area. Click **Done** to complete the connection.

With the connection finished any new quotes added to the quotable API will automatically be reflected in the list widget. Duda will check the endpoint roughly every two hours and cache any updates that are found. Any changes will be immediately reflected on the **published** site, you do not need to manually republish to keep the data in sync.
