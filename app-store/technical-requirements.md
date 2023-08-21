# Technical Requirements

Below is a list of requirements that Duda enforces on apps in its App Store. The goal of these requirements are to maintain a solid and consistent user experience that is inline with existing apps. If you have questions or need clarification -- please reach out -- we're happy to guide and help!

### Login

* All apps in Duda’s App Store must allow users to login via the ‘Open App’ feature within the editor. This means you must use our SSO method to log users into your app.
* You may allow users to log in to your app outside of Duda, however, asking for a password to onboard is forbidden.
* If you do allow users to log in outside of Duda, it must not interfere with their logins directly via the Duda platform in any way.
* Your app must be allowed to load in an iframe.
* When users add your app, you must create a new unique account for that website and/or client. If a user already has an account with you, the sign-up via Duda must work and not return an error.
* Users must be able to add the app on multiple websites. (The `site_name` is the unique identifier, not the `owner_account_name`)

### Technical

* You must respect the `api_endpoint` parameter passed in the install callback. This should be used as the `host` or `domain` you call for the API of a specific website.

### User Experience

* Apps should never require copy-pasting of code, IDs, API keys, or content to or from the App.
* Apps should use clear and understandable language and avoid jargon.
* Settings that users change must be made visible immediately. Avoid relying on save buttons if possible.
* There should be no disruptive and intrusive pop-ups. There will be no use of native JavaScript alerts or confirmation boxes.
* **White labeling:** No part of your app or the profile should show or reference Duda. Your app might be opened in a white label context, so, you should not reference Duda anywhere.
* Show premium or locked features even if they’re not available on the current plan. Any feature that is not available on the currently installed plan or tier should still be shown. The feature should be blocked or locked from access, but still clearly show that it exists.

### App Dashboard Design

* Your App should have a unified and standardized design with consistent layout and element spacing. These need to be the same across all pages/screens/settings.
* **Clear CTAs:** Your app must have clear calls to action that have been prioritized and clearly guide the user through important actions.
* Your app must fit nicely within the frame in which it loads. The max and default sizing of this frame is 1300px wide by 650px high. There are some cases where the width can shrink down to 800px on smaller screens. The UI must work in all scenarios and fill the entire content of the screen while not being overly crowded.

### Security

* Your app must accurately list the API permissions it uses. It should use no more permissions than absolutely necessary.
* You should aim to secure against all the OSWAP Top 10 Security Risks.
* All connections to your app must be served over HTTPS.

### Frontend / Widgets

* If your app adds anything to the website such as a widget, code embed, or floating buttons, it must conform with these requirements:

### Speed

* It is preferred to load all content server-side via widgets if possible. We understand that often it is not.
* If you load content from a 3rd party server via JavaScript, the following rules apply:
  * Your Time-To-First-Byte for connecting to your server must be 300ms or less.
  * The content downloaded to display or render your website embed must be less than 100kb (over the wire) in total download size, for the first view. This means that if users interact with your content/feature, it can load content that goes above 100kb, but only if it’s based on user interaction.
  * You must load JavaScript asynchronously/deferred.
  * If the content you’re loading is inline or within the body of the page, you must set a specific minimum height for your content that is set in static CSS. This is to avoid CLS.
  * You must minify JavaScript and CSS files.
  * Enable gzip (ideally also Brotli, too) compression on the server hosting your content.
  * Set appropriate caching headers.

#### We recommend the following as well:

* Using the site-wide HTML API, add a rel=”preconnect” tags to the header for all domains to which your App will make client-side network requests.

### SEO

If the content you add to websites affects the overall web presence, as such, you need to implement best practices related to SEO. Here’s what that means:

* Avoid usage of `<h1>` tags. If you need a heading, allow the user to select what type of heading tag (h2 through h6).
* If you include images, make sure to provide alt text.
* Avoid including content that can’t be edited by the website owner. Small banners/labels are okay, but anything longer should be customizable.
* No iframes for critical content. If the content helps the web presence and might assist in discoverability, then it needs to be discoverable by search engines, this means we do not allow content to be embedded within iframes.

### Pricing / Payments

* You are not permitted to collect payment for services outside of Duda’s App Store payment system.
  * There are some cases where we might allow it for highly specific or custom payment setups, but even in these scenarios, the primary service must be charged through Duda’s App Store. Contact us to learn more.
* The pricing you sell your app for within Duda must be the same as, or preferably lower than the price you offer publicly. In addition, the plans/feature sets must be comparable as well.
* If your App includes a trial, the status of the trial must be clearly displayed within your App. This means showing that there is X amount of time left and displaying a banner offering a path to upgrade when the trial has ended.

### GDPR / Privacy

* Your App must be GDPR compliant and allow users to (a) export all their data on demand and (b) manage the data that the App collects

### Market / Commercial

The goal of all apps is that they aim to enhancement to web presence in some way. Duda will not accept Apps that do not have a direct relationship with building a successful online presence. Here are four broad categories of Apps that constitute being related to a website:

1. Getting more traffic or customers: platforms, products and services that help the business and/or website get more traffic, visitors, and customers.
2. Expand the feature set of the website: tools that expand, extend or make existing features better and help Duda’s web professionals do more with their website.
3. Help convert customers: tools that help businesses turn leads into paying customers through follow-ups, smart optimizations, etc.
4. Help retain customers, give feedback or turn into repeat customers: Services like this communicate with existing customers and re-engage them in some way.

Duda’s goal here is to make sure that apps in the App Store are aligned with what our customers need and to not have apps or services that do not help make their websites better. Other types of apps will be considered, but our goal is to empower Duda customers to do more with their websites.

### Competition

Apps must not present or upsell to services competitive with the core website. E.g. you cannot promote your own website tool or site-building service inside of an App. You can’t reference other website products/platforms, etc.

### Localization

Your app must be localized for a minimum of English. This is the primary language of Duda’s customer base. We strongly also recommend localizing for most other languages that Duda supports.
