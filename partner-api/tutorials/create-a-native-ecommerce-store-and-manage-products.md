# Create a Native eCommerce Store and Manage Products

### Objectives and Outcomes

In this tutorial you will learn how to set up a native eCommerce store on your Duda site, as well as managing products for your native store using the API.

### Requirements

To work with this guide, you’ll need to make sure you have the following items ready:

* Your Duda API key and password. Learn how to gain API access [here](../../).

### 1. Add a Native Store to a Site

First you need to add a native store to your site. In the side panel of the editor, click **eCommerce**. Next, click **Add store to your site**, then select **Add native store**.

Once your store is created, you can set up different aspects of your store, including [Business Information](https://support.duda.co/hc/en-us/articles/5411161045015-Business-Information), [Payment Gateways](https://support.duda.co/hc/en-us/articles/5411132421015-Payment), [Shipping Zones](https://support.duda.co/hc/en-us/articles/5411132453655-Shipping-Zones), [Tax Zones and Rates](https://support.duda.co/hc/en-us/articles/5411172039831-Tax-Zones-and-Rates), and [Create Discounts](https://support.duda.co/hc/en-us/articles/5411171786647-Create-Discount).

### 2. Add Products to Your Store

Now that you have your store set up, it's time to start adding products. With the use of the Product APIs, you can add products to your store without having to manually add individual products directly from the Duda editor. For example, you can add a t-shirt product directly to the store using the Create Product API. To do this, use the [POST /sites/multiscreen/{site\_name}/products](../../reference/partner-api-reference/ecomm-products.md#create-product-1) API endpoint.

{% tabs %}
{% tab title="Create Product for a Site" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X POST \
-k https://api.duda.co/api/sites/multiscreen/146856ab/products \
-d '{
	"description": "The most amazing t shirt ever sold",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "prices": [
    {
      "compare_at_price": 19.99,
      "currency": "USD",
      "price": 12.34
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE"
}'
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

This call creates a t-shirt product with a description as well as a price, image, SEO properties, and SKU. The image below shows this product in the store after the command has been executed.

<figure><img src="https://files.readme.io/d615147-product_pic.png" alt=""><figcaption></figcaption></figure>

### 3. Update Products in Your Store

The Product APIs allow you to update and delete existing products in your store, as well as get information on individual or all products within your store. More information on those specific commands can be found in the API Reference Documentation for the [Product APIs](../../reference/partner-api-reference/ecomm-products.md).
