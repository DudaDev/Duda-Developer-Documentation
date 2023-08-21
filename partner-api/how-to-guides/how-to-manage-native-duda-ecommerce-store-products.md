# How to Manage Native Duda eCommerce Store Products

This guide explains how to create and manage products for native eCommerce stores on Duda sites using the API. If using native eCommerce on the Duda platform is unfamiliar to you, then check out our [Native eCommerce Overview article](https://support.duda.co/hc/en-us/articles/5131910530071-Native-eCommerce-Overview).

### Requirements

To work with this guide, you’ll need to make sure you have the following items ready:

* Your Duda API key and password. Learn how to gain API access [here](../../#api-credentials).
* A native store added to a site. If you aren't sure how to do this, you can learn more by checking out our Tutorial on [Creating a Native eCommerce Store](../tutorials/create-a-native-ecommerce-store-and-manage-products.md).

### 1. Add Products to Your Store

Now that you have your store set up, it's time to start adding products. To create a new product, use the [POST /sites/multiscreen/{site\_name}/products](../../reference/partner-api-reference/ecomm-products.md#create-product-1) API endpoint. When adding a product to a store, you are required to pass a 'site\_name' parameter, this way Duda knows which site store you want to add a product to. In the body, we pass through product details such as a description, associated images, name, price details, specific SEO details, SKU, and whether the item is actively listed within your store. In the example below, we are creating a new product listing for a t-shirt.

{% tabs %}
{% tab title="curl" %}
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
{% endtabs %}

### 2. Get Products From Your Store

You can retrieve a list of all products in your store by using the [GET /sites/multiscreen/{site\_name}/products](../../reference/partner-api-reference/ecomm-products.md#list-products-1) API endpoint.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/sites/multiscreen/146856ab/products
```
{% endtab %}
{% endtabs %}

Similarly, you can get a single product by filtering by product id in the path using the [GET /sites/multiscreen/{site\_name}/products/{product\_id}](../../reference/partner-api-reference/ecomm-products.md#get-product-1) API endpoint.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X GET \
-k https://api.duda.co/api/sites/multiscreen/146856ab/products/IakdKbiUiK
```
{% endtab %}
{% endtabs %}

### 3. Update Products in Your Store

You can update individual products by specifying the product id using the [PATCH /sites/multiscreen/{site\_name}/products/{product\_id}](../../reference/partner-api-reference/ecomm-products.md#update-product-1) API endpoint.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X PATCH \
-k https://api.duda.co/api/sites/multiscreen/146856ab/products/IakdKbiUiK \
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
{% endtabs %}

### 4. Delete Products From Your Store

You can remove individual products from the store by using the [DELETE /sites/multiscreen/{site\_name}/products/{product\_id}](../../reference/partner-api-reference/ecomm-products.md#delete-product-1) API endpoint.

{% tabs %}
{% tab title="curl" %}
```bash
curl -S -u 'APIusername:APIpassword' \
-H 'Content-Type: application/json' \
-X DELETE \
-k https://api.duda.co/api/sites/multiscreen/146856ab/products/IakdKbiUiK
```
{% endtab %}
{% endtabs %}
