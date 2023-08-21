# Libraries/SDKs

Currently, we have libraries for the following languages:

### Node

* [NPM](https://www.npmjs.com/package/@dudadev/partner-api)
* [Repo](https://github.com/DudaDev/partner-api)

{% tabs %}
{% tab title="Installation" %}
```javascript
npm install @dudadev/partner-api --save
// or
yarn add @dudadev/partner-api
```
{% endtab %}

{% tab title="Example" %}
```javascript
const { Duda } = require('@dudadev/partner-api');

const duda = new Duda({
  user: process.env.DUDA_API_USER,
  pass: process.env.DUDA_API_PASS,
});

duda.sites.get({ site_name: "a-site-name" })
  .then((site) => console.log(site))
  .catch((error) => console.error(error));
```
{% endtab %}
{% endtabs %}

**Don't see your favorite language?**\
[Let us know](https://about/cdn-cgi/l/email-protection#9ae9efeaeaf5e8eedafeeffefbb4f9f5) if you want (or are interested in writing) a library for a language not represented here!
