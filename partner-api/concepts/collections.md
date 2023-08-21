# Collections

Complex data structures can be integrated into Duda websites via collections. A collection is a list of like items (e.g. staff members, products, events, news articles, etc.), with each object in the list consisting of the same set of properties called fields. For staff members, this might be a name, bio and profile picture. For events it could be a date, time, description and a URL from which to purchase tickets.

Collections are similar to databases or a spreadsheet in that they are made up of fields (similar to columns) that are assigned a data type, and individual items consisting of the values corresponding to each field (similar to rows).

### Collection Types

Duda provides two types of collections, internal and external, with the source of the data/values providing the distinction between the two. In internal collections the data is stored directly within Duda. Users are able to edit data either manually within the editor, or programmatically via our collection API endpoints. External collections receive their data from an outside source, via a JSON endpoint. This data is temporarily stored within Duda, but will be revalidated periodically or immediately via an API call. External collections are a great way to ensure outside systems stay the source-of-truth for content displayed on a website.

### Field and Data Types

Similar to columns within a relational database, collection fields must be assigned a name and a data type. In Duda, data types are used to associate a field value with the type of widgets that can display that value, in addition to allowing the editor to know what types of formatting are available to the value. For example, a column with URLs as values may be set to be either an image data type or a link data type. Knowing the specific data type lets the Duda editor narrow down the types of widgets that are allowed to use that value.

Collection data can be connected to widgets in the same way it's possible to [connect business-level data](https://blog.duda.co/integrating-duda-into-a-saas-platform-1). However, because collection data is a list of items instead of a single piece of discrete data, only certain widgets are capable of displaying that data on a page. These types of widgets include:

* list widget
* photo gallery widget
* image slider widget
* accordion widget

Once a collection has been connected, you'll be able to connect the individual properties of the items to display within the widget's layout.

### Caching

By default, Duda caches the data for an external collection to help with performance. By default, we cache a collection up to 2hrs. If you want to update the data in the site immediately, you can use one of the [revalidate](../../reference/partner-api-reference/collections.md#clear-cache-1) [calls](../../reference/partner-api-reference/collections.md#clear-cache-by-external-id-1).

### Limitations

The following limitations exist for Internal and External Collections.

|                                 | Internal                          | External                          |
| ------------------------------- | --------------------------------- | --------------------------------- |
| Number of collections per site  | 100 (including image collections) | 100 (including image collections) |
| Rows                            | 500                               |                                   |
| Fields                          | 30                                | 100                               |
| Inner collection rows           | 30                                |                                   |
| Inner collection fields         | 10                                | 15                                |
| Text field character limit      | 2000                              |                                   |
| Collection name character limit | 50                                | 50                                |
| Field name character limit      | 50                                | 50                                |
| Page item URL character limit   | 100                               |                                   |
| Update data                     | Publish site/content library      | Automatic                         |
