---
description: >-
  Understanding the benefits of white-labeling your application and how you do
  it.
---

# White Labeling Apps

## The benefit of following white label

Many of Duda’s existing customers choose Duda because we have fully white labeled our platform and allow agencies to present the website builder tool as their own solution. This allows many of Duda customers to build their own set of technology services and present them under a single, unified brand.

Apps that conform to white labeling will likely see wider adoption, as it allows our agencies to offer an entire online marketing solution to their customers, under a single unified brand with a single message.

Duda recommends that Apps white label whenever possible, but it is not a requirement.

## Understanding White Labeling when building Apps

The Duda platform is available under two different branding scenarios in which App developers can confirm their Apps to follow. These types follow the different user types that might be controlling the application at that time. These are: (a) Staff and (2) Customers. Let’s cover the profile of each quickly and if they see the Duda brand or not.

### Staff & Agency

Agency and Staff members always see the Duda brand and thus should see the brand of your application. The agency account (sometimes referred to as account owner) is the direct customer of Duda and is the one that will ultimately purchase your App.

Staff members are team members (think designers, QA, copy writers, etc..) of the team under the agency account. They see the Duda brand along with the agency and are considered (roughly) the same customer profile within Duda.

Agencies can also [control the branding of their account](https://help.duda.co/hc/en-us/articles/219057568-DudaPro-Custom-Branding) from their dashboard inside of Duda.

### Customers

The customer of an agency will never see the Duda brand (side note, your app should never mention Duda). When customers are logged into the platform, they will see the logo and colors that the agency has configured for their account and the tool will be represented as though the agency own’s it.

Customers will never give payments or see pricing for your application -- the app must be purchased by the agency before customers can access it.

## Conforming to white label

The default view for applications will be to show the brand of your app to both Staff & Customer accounts. If you want to enable white labeling for customer accounts, you will need to fill in the white label section of your manifest file. See the flow chart below for how this will be handled inside of the Duda platform if you choose to white label the application.

<figure><img src="https://files.readme.io/5b347a7-wl-app-profile-explainer.jpg" alt="901"><figcaption><p>What different user types will see in the App Store.</p></figcaption></figure>

When building the white label profile, you will need to fill in all relevant details, but omit any references to your brand. You should come up with a generic term to describe the integration. For example, Ecwid eCommerce is called Online Store.

You will also need to make sure any UI you present to the user does not display your brand, mention your company name or link to any branded URL, anywhere within your product. Your UI does not need to inherit the styles of the agency account, but if your app is to be considered white-label enabled, you must not allow standard users to easily find out who built your product.

## Branding your App

When Duda performs SSO, we add a URL parameter into the SSO URL called `is_white_label`. This indicates if the current user who is opening your application is a white-label user or not. This should tell you whether to present a white-labeled experience or not.

Many applications choose to brand their interface with a generic logo and brand that is presented to all users, rather than needing to make the branding dynamic for different customer types. This approach is 100% supported.

## Using the Duda-reseller branding in your app

Some of Duda's accounts set up their own [custom-branding](https://support.duda.co/hc/en-us/articles/360042933793-Custom-Branding) within the Duda platform. You can use the [GET Branding](../../reference/app-store-api-reference/get-account-brand.md#undefined-1) API to get the custom branding and use it in your app's UI.
