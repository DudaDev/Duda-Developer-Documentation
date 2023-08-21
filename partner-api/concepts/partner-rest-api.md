# Partner REST API

### Partner Rest API

When a developer hears Duda has a website management API, many times they assume some version of design-by-API functionality, where a highly-polished website can be constructed from a completely blank slate. While there are hints of this functionality available within the Partner API, most of the endpoints are instead focused on the task of publishing similar websites at scale.

The allure of pure-API website design fades once you consider the complexity of design and the limitations of the browser's document object model (DOM). For example, consider the relatively simple concept of adding an image to a page. The API call would need to not only specify a public URL or binary data representing the image, it would need to know the style data associated with that image. Does it have a border? What are the margins? Should it be displayed inline or as a block element? The list goes on-and-on.

Once your design choices are made, there's the issue of actually inserting the element into the DOM. Very rarely can elements be placed without the help of other DOM scaffolding. A tree structure of anchor tags, lists, divs and other elements are used as a layout mechanism to maintain the position of the inserted element. Construction of this object tree via API becomes impractically difficult without immediate visual feedback.

### Managing Websites at Scale <a href="#managing-websites-at-scale" id="managing-websites-at-scale"></a>

Duda takes the position that design is best done in the visual drag-and-drop editor. While access, lifecycle management, and content injection are functions that can be accomplished via API. Designing site templates or sections within the editor allows visual complexity to be solved within a visual environment. Those templates can then be easily used to create multiple websites based on the underlying design.

With the design decisions made, we can use the API to manage all the other aspects of the website lifecycle:

* [Creating a website](../../reference/partner-api-reference/sites.md#create-site-1) from a template
* [Updating content](../../reference/partner-api-reference/site-content.md#update-content-library-1) on the website
* [Publishing](../../reference/partner-api-reference/sites.md#publish-site-1) and [unpublishing](../../reference/partner-api-reference/sites.md#unpublish-site-1) the website
* [Deleting](../../reference/partner-api-reference/sites.md#delete-site-1) a website when it's no longer needed

Using the API to manage the lifecycle of a website means you can easily manage the state of dozens or hundreds of sites programmatically. If you allow customers the ability to edit their own sites, there are additional endpoints to help automate access to sites:

* [Creating](../../reference/partner-api-reference/accounts.md#create-account-1) and [deleting](../../reference/partner-api-reference/accounts.md#delete-account-1) users
* [Granting](../../reference/partner-api-reference/client-permissions.md#grant-site-access-1) and [revoking](../../reference/partner-api-reference/client-permissions.md#remove-site-access-1) access to sites
* [Authenticating](../../reference/partner-api-reference/authentication.md#get-sso-link-1) users into the editor

### Other API Capabilities

Managing site lifecycle and access allows companies to easily create a DIY or instant website flow for their business. Along with this common functionality, other features are available via API including creating site backups, managing URL rules, and retrieving site analytics. The common theme of these endpoints is they operate on high-level objects and concepts outside of the design of the site. Think of the API as a way to capitalize on the work you've already done within the editor. Once your templates and designs are finalized, the API allows you to quickly scale that work across multiple customers with minimal effort and no manual intervention. For more information on all available endpoints, see the API reference.
