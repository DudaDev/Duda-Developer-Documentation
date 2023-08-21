# How to Set Multi-Language Dynamic Pages

Duda allows you to serve multi-language content from a single external collection. When a user visits your site, Duda will automatically map the external collection language to the selected site language.

### Prerequisites

An external collection endpoint must be created and identified by a 'lang' path or query parameter. The value of the parameter must correspond to a supported language.

| en    | es    | ja    | pt    |
| ----- | ----- | ----- | ----- |
| fr    | de    | tr    | en-gb |
| it    | nl    | ar    | be    |
| bg    | bs-ba | ca    | cs    |
| da    | el    | en-au | en-ca |
| es-ar | es-cl | es-co | es-cr |
| es-mx | et    | fa    | fi    |
| fr-ca | he    | hi    | lv    |
| hu    | hy    | id    | is    |
| nb    | ar    | pa    | pl    |
| pt-br | ro    | ru    | sk    |
| sl    | sq    | sv    | sw    |
| ta    | th    | uk    | vi    |
| zh    | cy    | tl    | zh-tw |
| ka    | mr    | sr-rs | gl    |
| eu    | az    | ps    | mi    |
| ko    | mn    |       |       |

### 1. Configure External Endpoint in Editor

Specify the location of the lang parameter by using a placeholder in the Endpoint URL field of the collection settings.

<figure><img src="https://files.readme.io/3bf43fd-collection_settings.png" alt="2918"><figcaption><p>Example usage of the {lang} placeholder in the Endpoint URL of a collection.</p></figcaption></figure>

The endpoint URL of [https://example.org/collections/{lang}/collection.json](https://example.org/collections/%7Blang%7D/collection.json) could refer to any of the following actual URLs.

* [https://example.org/collections/en/collection.json](https://example.org/collections/en/collection.json)
* [https://example.org/collections/es/collection.json](https://example.org/collections/es/collection.json)
* [https://example.org/collections/de/collection.json](https://example.org/collections/de/collection.json)

Alternatively, you could use the query parameter format. An endpoint URL such as [https://example.org/collections/collection.json?lang={lang}](https://example.org/collections/collection.json?lang=%7Blang%7D) could refer to the following:

* [https://example.org/collections/collection.json?lang=en](https://example.org/collections/collection.json?lang=en)
* [https://example.org/collections/collection.json?lang=es](https://example.org/collections/collection.json?lang=es)
* [https://example.org/collections/collection.json?lang=de](https://example.org/collections/collection.json?lang=de)

### 2. Create Multi-Language Dynamic Pages

To create a multi-language dynamic page follow the same process as [creating a single-language dynamic page](../concepts/dynamic-pages.md#creating-the-dynamic-page).

{% hint style="info" %}
**Good to know:** Creating a dynamic page or converting a regular page to a dynamic will be available only from the primary language.
{% endhint %}

Once all your widgets have been connected within the dynamic page, add that page to the other languages by clicking 'translate' in the cog menu next to the dynamic page, or by switching to another language and clicking 'translate another page at the top of the pages menu

<figure><img src="https://files.readme.io/a0c8032-translate.png" alt="1458"><figcaption><p>Translating a dynamic page from the page's cog menu</p></figcaption></figure>

<figure><img src="https://files.readme.io/edcb55c-translate_menu.png" alt="1458"><figcaption><p>Translating a dynamic page by selecting the page from the 'Translate another page' menu.</p></figcaption></figure>

There is no need to edit the data connections on the widgets within the translated dynamic pages. Duda will automatically map the language to the correct endpoint URL by substituting the language code of the selected language with the {lang} placeholder in the endpoint URL setting of the external collection.

{% hint style="warning" %}
**Heads up: Converting a dynamic page back to a regular page**

* When converting a dynamic page to a regular page from the primary language, it will be converted to a regular page in all languages.
* When converting a dynamic page to a regular page from a language other than the primary one, it will affect only this specific language.
{% endhint %}
