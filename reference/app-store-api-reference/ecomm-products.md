---
description: Native Store Only
---

# eComm Products

## Product Object

Get products page. Default page response size is 50, max requested page size is 100.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "description": "The most amazing t shirt ever sold",
  "external_id": "KTP9XGbSg2",
  "id": "IakdKbiUiK",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "options": [
    {
      "choices": [
        {
          "id": "db3je27rg7",
          "value": "45"
        }
      ],
      "id": "WMd1xylGrp",
      "name": "Shirt size"
    }
  ],
  "prices": [
    {
      "compare_at_price": "19.99",
      "currency": "USD",
      "price": "12.34"
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE",
  "variations": [
    {
      "external_id": "KTP9XGbSg2",
      "id": "KTP9XGbSg2",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "options": [
        {
          "choice_id": "db3je27rg7",
          "choice_value": "45",
          "option_id": "WMd1xylGrp",
          "option_name": "Shirt size"
        }
      ],
      "price_difference": "string",
      "quantity": 25,
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "stock_status": "IN_STOCK, OUT_OF_STOCK"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

#### product\_details

<table><thead><tr><th>Property</th><th>Type</th><th width="280">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>description</strong></td><td><em>string</em></td><td>A description of the product.</td><td>Yes</td></tr><tr><td><strong>external_id</strong></td><td><em>string</em></td><td>External product identifier for reference</td><td>No</td></tr><tr><td><strong>id</strong></td><td><em>string</em></td><td>A unique identifier for the product.</td><td>No</td></tr><tr><td><strong>images</strong></td><td><em>object[]</em></td><td>Contains images and image details for the product. Must pass all data when making any changes to this property. <a href="ecomm-products.md#images">See the section below for details.</a></td><td>Yes</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the product.</td><td>Yes</td></tr><tr><td><strong>options</strong></td><td><em>string</em></td><td>Options for the product. Will be used to generate product variations. <a href="ecomm-products.md#options">See the section below for details</a></td><td>Yes</td></tr><tr><td><strong>prices</strong></td><td><em>object[]</em></td><td>Contains the pricing details of the product. Must pass all data when making any changes to this property. <a href="ecomm-products.md#prices">See the section below for details.</a></td><td>Yes</td></tr><tr><td><strong>seo</strong></td><td>object</td><td>Contains the seo properties of the object. <a href="ecomm-products.md#seo">See the section below for details.</a></td><td>Yes</td></tr><tr><td><strong>sku</strong></td><td>string</td><td>The stock keeping unit of the product.</td><td>Yes</td></tr><tr><td><strong>status</strong></td><td>string</td><td>The status of the product. Can be either <strong>ACTIVE</strong> or <strong>INACTIVE</strong>.</td><td>Yes</td></tr></tbody></table>

#### images

<table><thead><tr><th>Property</th><th>Type</th><th width="237">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>alt</strong></td><td><em>string</em></td><td>Description of the image.</td><td>Yes</td></tr><tr><td><strong>url</strong></td><td><em>string</em></td><td>The url of the image.</td><td>Yes</td></tr></tbody></table>

#### prices

<table><thead><tr><th>Property</th><th>Type</th><th width="348">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>compare_at</strong></td><td><em>string</em></td><td>The comparative price of the product. The difference between the product's discounted price and original price.</td><td>Yes</td></tr><tr><td><strong>currency</strong></td><td><em>string</em></td><td>Specified currency of the product.</td><td>Yes</td></tr><tr><td><strong>price</strong></td><td><em>string</em></td><td>Actual price of the product.</td><td>Yes</td></tr></tbody></table>

#### seo

<table><thead><tr><th>Property</th><th>Type</th><th width="248">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>description</strong></td><td><em>string</em></td><td>The meta description of the product. Should be around 155 characters in length.</td><td>Yes</td></tr><tr><td><strong>product_url</strong></td><td><em>string</em></td><td>The path / URL to a product in the store.</td><td>Yes</td></tr><tr><td><strong>title</strong></td><td><em>string</em></td><td>Set the for this product. Should be less than 60 characters in length.</td><td>Yes</td></tr></tbody></table>

#### options

<table><thead><tr><th>Property</th><th>Type</th><th width="280">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>A unique identifier for the option.</td><td>Yes</td></tr><tr><td><strong>name</strong></td><td><em>string</em></td><td>The name of the option.</td><td>Yes</td></tr><tr><td><strong>choices</strong></td><td><em>array</em></td><td>An array of choices for the option. <a href="ecomm-products.md#choices">See the section below for details</a></td><td>Yes</td></tr></tbody></table>

#### choices

<table><thead><tr><th>Property</th><th>Type</th><th width="291">Description</th><th>Mutable</th></tr></thead><tbody><tr><td><strong>id</strong></td><td><em>string</em></td><td>A unique identifier for the choice.</td><td>No</td></tr><tr><td><strong>value</strong></td><td><em>string</em></td><td>The value of the choice.</td><td>Yes</td></tr></tbody></table>

## List Products

{% swagger method="get" baseUrl="https://api-sandbox.duda.co/api" expanded="false" fullWidth="false" summary="List Products" path="/integrationhub/application/site/{site_name}/ecommerce/products" %}
{% swagger-description %}
Get products page. Default page response size is 50, max requested page size is 100.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier of the target site.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="int32" %}
Zero-based offset for elements (0..N)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="int32" %}
The size of the page to be returned
{% endswagger-parameter %}

{% swagger-parameter in="query" name="sort" type="array of string" %}
Property on which to sort results
{% endswagger-parameter %}

{% swagger-parameter in="query" name="direction" type="string" %}
\[asc,desc] Order direction for the property specified in sort.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "limit": 0,
  "offset": 0,
  "results": [
    {
      "description": "The most amazing t shirt ever sold",
      "external_id": "KTP9XGbSg2",
      "id": "IakdKbiUiK",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "name": "Amazing T-shirt",
      "options": [
        {
          "choices": [
            {
              "id": "db3je27rg7",
              "value": "45"
            }
          ],
          "id": "WMd1xylGrp",
          "name": "Shirt size"
        }
      ],
      "prices": [
        {
          "compare_at_price": "19.99",
          "currency": "USD",
          "price": "12.34"
        }
      ],
      "seo": {
        "description": "Amazing T-shirt made with 100% biologic cotton",
        "product_url": "amazing-t-shirt",
        "title": "Amazing T-shirt"
      },
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "variations": [
        {
          "external_id": "KTP9XGbSg2",
          "id": "KTP9XGbSg2",
          "images": [
            {
              "alt": "Image of fancy shirt",
              "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
            }
          ],
          "options": [
            {
              "choice_id": "db3je27rg7",
              "choice_value": "45",
              "option_id": "WMd1xylGrp",
              "option_name": "Shirt size"
            }
          ],
          "price_difference": "string",
          "quantity": 25,
          "sku": "UGG-BB-PUR-06",
          "status": "ACTIVE",
          "stock_status": "IN_STOCK, OUT_OF_STOCK"
        }
      ]
    }
  ],
  "site_name": "string",
  "total_responses": 0
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url 'https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/products?offset=0' \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Get Product

{% swagger baseUrl="https://api-sandbox.duda.co/api" expanded="false" method="get" summary="Get Product" path="/integrationhub/application/site/{site_name}/ecommerce/products/{id}" %}
{% swagger-description %}
Get catalog product by id
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="product_id" type="string" required="true" %}
The unique identifier for the target Product.
{% endswagger-parameter %}

{% swagger-parameter in="header" type="string" name="x-duda-access-token" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "description": "The most amazing t shirt ever sold",
  "external_id": "KTP9XGbSg2",
  "id": "IakdKbiUiK",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "options": [
    {
      "choices": [
        {
          "id": "db3je27rg7",
          "value": "45"
        }
      ],
      "id": "WMd1xylGrp",
      "name": "Shirt size"
    }
  ],
  "prices": [
    {
      "compare_at_price": "19.99",
      "currency": "USD",
      "price": "12.34"
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE",
  "variations": [
    {
      "external_id": "KTP9XGbSg2",
      "id": "KTP9XGbSg2",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "options": [
        {
          "choice_id": "db3je27rg7",
          "choice_value": "45",
          "option_id": "WMd1xylGrp",
          "option_name": "Shirt size"
        }
      ],
      "price_difference": "string",
      "quantity": 25,
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "stock_status": "IN_STOCK, OUT_OF_STOCK"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url 'https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/products/id?offset=0' \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Create Product

{% swagger method="post" path="/integrationhub/application/site/{site_name}/ecommerce/products" baseUrl="https://api-sandbox.duda.co/api" summary="Create Product" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
Product name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}
Product description
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sku" type="string" %}
Stock keeping unit of given product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="status" type="string" %}
\[ACTIVE, HIDDEN] Only entities in published state will be available to store front
{% endswagger-parameter %}

{% swagger-parameter in="body" name="images" type="array of objects" %}
image list fro given product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="array of objects" %}
Price for given product in different currencies
{% endswagger-parameter %}

{% swagger-parameter in="body" name="seo" type="object" %}
description, product_ur, and title of product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="options" type="array of objects" %}
List of options and values to chose from, will be used to create the product variations
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "description": "The most amazing t shirt ever sold",
  "external_id": "KTP9XGbSg2",
  "id": "IakdKbiUiK",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "options": [
    {
      "choices": [
        {
          "id": "db3je27rg7",
          "value": "45"
        }
      ],
      "id": "WMd1xylGrp",
      "name": "Shirt size"
    }
  ],
  "prices": [
    {
      "compare_at_price": "19.99",
      "currency": "USD",
      "price": "12.34"
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE",
  "variations": [
    {
      "external_id": "KTP9XGbSg2",
      "id": "KTP9XGbSg2",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "options": [
        {
          "choice_id": "db3je27rg7",
          "choice_value": "45",
          "option_id": "WMd1xylGrp",
          "option_name": "Shirt size"
        }
      ],
      "price_difference": "string",
      "quantity": 25,
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "stock_status": "IN_STOCK, OUT_OF_STOCK"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/products \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Update Product

{% swagger method="patch" path="/integrationhub/application/site/{site_name}/ecommerce/products/{id}" baseUrl="https://api-sandbox.duda.co/api" summary="Update Product" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
Product name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" %}
Product description
{% endswagger-parameter %}

{% swagger-parameter in="path" name="product_id" type="string" required="true" %}
The unique identifier for the target Product.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sku" type="string" %}
Stock keeping unit of given product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="status" type="string" %}
\[ACTIVE, HIDDEN] Only entities in published state will be available to store front
{% endswagger-parameter %}

{% swagger-parameter in="body" name="images" type="array of objects" %}
image list fro given product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="array of objects" %}
Price for given product in different currencies
{% endswagger-parameter %}

{% swagger-parameter in="body" name="seo" type="object" %}
description, product_ur, and title of product
{% endswagger-parameter %}

{% swagger-parameter in="body" name="options" type="array of objects" %}
List of options and values to chose from, will be used to create the product variations
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "description": "The most amazing t shirt ever sold",
  "external_id": "KTP9XGbSg2",
  "id": "IakdKbiUiK",
  "images": [
    {
      "alt": "Image of fancy shirt",
      "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
    }
  ],
  "name": "Amazing T-shirt",
  "options": [
    {
      "choices": [
        {
          "id": "db3je27rg7",
          "value": "45"
        }
      ],
      "id": "WMd1xylGrp",
      "name": "Shirt size"
    }
  ],
  "prices": [
    {
      "compare_at_price": "19.99",
      "currency": "USD",
      "price": "12.34"
    }
  ],
  "seo": {
    "description": "Amazing T-shirt made with 100% biologic cotton",
    "product_url": "amazing-t-shirt",
    "title": "Amazing T-shirt"
  },
  "sku": "UGG-BB-PUR-06",
  "status": "ACTIVE",
  "variations": [
    {
      "external_id": "KTP9XGbSg2",
      "id": "KTP9XGbSg2",
      "images": [
        {
          "alt": "Image of fancy shirt",
          "url": "https://images.pexels.com/photos/1020585/pexels-photo-1020585.jpeg"
        }
      ],
      "options": [
        {
          "choice_id": "db3je27rg7",
          "choice_value": "45",
          "option_id": "WMd1xylGrp",
          "option_name": "Shirt size"
        }
      ],
      "price_difference": "string",
      "quantity": 25,
      "sku": "UGG-BB-PUR-06",
      "status": "ACTIVE",
      "stock_status": "IN_STOCK, OUT_OF_STOCK"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request PATCH \
     --url https://api-sandbox.duda.co/api/integrationhub/application/site/site_name/ecommerce/products/id \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'content-type: application/json' \
     --header 'x-access-token: {access_token}' \
     --header 'x-duda-access-token: Bearer tefDCCAKciewk6FLmMjfC0cg1d4'
```
{% endtab %}
{% endtabs %}

## Delete Product

{% swagger method="delete" path="/integrationhub/application/site/{site_name}/ecommerce/products/{id}" baseUrl="https://api-sandbox.duda.co/api" summary="Delete Product" expanded="false" %}
{% swagger-description %}
Delete catalog product
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
The unique identifier for the target site
{% endswagger-parameter %}

{% swagger-parameter in="path" name="product_id" type="string" required="true" %}
The unique identifier of the target Product.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-duda-access-token" type="string" %}
The specific access token to access this site API.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}
Your App Account's username and password, base64'd.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api.duda.co/api/sites/multiscreen/site_name/ecommerce/products/product_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
