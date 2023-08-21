# Domain Management

### Overview

This guide will walk you through the different types of domains that are customizable on the Duda platform. These domains are either configuration of the white label settings of your portal or the domains where websites will be visible online.

### Requirements

To work with this guide, you’ll need to make sure you have the following items ready:

* A white label enabled account. This typically is reserved for agencies and resellers.

### How it Works

Inside the Duda dashboard you’ll notice a tab called White Label. Under that tab is a link named Custom Domain. Under this link you’ll find the ability to customize all possible domains under Duda.

![](https://files.readme.io/89044a9-white\_label\_tab.png)

​

### Dashboard Domain

The Dashboard domain manages what domain serves the Duda editor, dashboard, preview and login portal. By default this domain is a subdomain of our default editor domain. The subdomain can be changed to any subdomain currently not in use.

![](https://files.readme.io/115d87e-Screen\_Shot\_2022-07-22\_at\_11.29.18\_AM.png)

In the above example using a subdomain of mycompany creates the following urls:

* mycompany.\[default editor domain]/login (login portal for your team and clients)
* mycompany.\[default editor domain]/home (serves the duda dashboard)
* mycompany.\[default editor domain]/preview (preview links for site builds are served from this path. For example, mycompany.\[default editor domain]/preview/a1dewsf?device=all)

Optionally you can use your own domain in place of a subdomain.

For example, selecting the radio button next to Custom Domain and entering mycompany.com will enable the following urls:

* mycompany.com/login (login portal for your team and clients)
* mycompany.com/home (serves the duda dashboard)
* mycompany.com/preview (preview links for site builds are served from this path. For example, mycompany.com/preview/a1dewsf?device=all)

Using your own domain requires you to update the DNS record pointing the domain to Duda. For detailed instructions how to set this up, look [here](https://support.duda.co/hc/en-us/articles/360060106454-Go-Live-Publish-and-Set-Up-Your-Domain).

{% hint style="info" %}
**Good to know: SSL Certificates**

SSL certificates are automatically created for your domain to ensure all traffic is served over https.
{% endhint %}

### Sites Domain

The Sites Domain manages the default domain for all published sites. This default domain is a way for sites to publish without requiring a custom domain. This is a great way to build a site for a customer who doesn’t own a domain or has a domain already in use.

By default a site without a custom domain is published using the following pattern:

`https://<SiteName>.[default sites domain]`

Optionally you can provide your own domain as a default publishing domain.

![](https://files.readme.io/066f7dd-Screen\_Shot\_2022-07-22\_at\_11.30.37\_AM.png)

In the above example the default domain for published sites is:

`https://<SiteName>.mycompany-sites.com`

Using your own domain requires you to update the DNS record pointing the domain to Duda. For detailed instructions how to set this up, look [here](https://support.duda.co/hc/en-us/articles/360060106454-Go-Live-Publish-and-Set-Up-Your-Domain).

{% hint style="info" %}
**Good to know: Domain Change**

The domain of a site can be changed at anytime in the Duda editor or via the API. A common pattern is building a site under a subdomain initially before moving it to it’s own domain. Learn more about using a custom domain for a site here.
{% endhint %}
