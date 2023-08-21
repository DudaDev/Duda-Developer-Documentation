---
description: All webhooks related to Duda's Native store events are listed below.
---

# Native Ecommerce

### Order Created

A notification is sent when a new order is created within the store. Event type: `ECOMM_ORDER_CREATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "mode": "LIVE",
    "id": "9e36bca4-aea5-4e00-b78e-cf855bf82766",
    "status": "PROCESSED",
    "email": "john.doe@duda.co",
    "invoice_number": "ECOM-1065",
    "items": [
      {
        "id": "AkeDXLWQ_3knf3F7V",
        "product_id": "string",
        "variation_id": "string",
        "name": "Grey Ceramic plate",
        "image": "https://cdn.dwhitelabel.com/md/dmtmpl/8023052e-2693-4e9c-a8f1-f86c15ec13eb/dms3rep/multi/grey-ceramic-plate-view1.jpg",
        "options": [
          {
            "name": "Size",
            "value": "Small"
          }
        ],
        "quantity": 1,
        "unit_price": "45.00",
        "unit_weight": null,
        "unit_dimensions": null,
        "total": "45.00",
        "combined_weight": 0,
        "metadata": {}
      }
    ],
    "billing_address": {
      "name": "John Doe",
      "first_name": "John",
      "last_name": "Doe",
      "full_name": "John Doe",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "street_number": "1",
      "street_name": "Main St",
      "city": "Boulder",
      "sub_locality": null,
      "region": "CO",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_address": {
      "name": "John Doe",
      "first_name": "John",
      "last_name": "Doe",
      "full_name": "John Doe",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "street_number": "1",
      "street_name": "Main St",
      "city": "Boulder",
      "sub_locality": null,
      "region": "CO",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_method": {
      "name": "Zone 1",
      "cost": "14.00"
    },
    "shipping_instructions": "My instructions !",
    "discounts": [],
    "taxes": [
      {
        "name": "My tax",
        "amount": "8.85",
        "rate": 0.15
      }
    ],
    "subtotal": "45.00",
    "total": "67.85",
    "payment": {
      "transaction_id": "ch_3MPVHQHiZehw2KYT1r9REUbz",
      "status": "PAID",
      "currency": "CAD",
      "method": "CreditCard",
      "card_brand": "VISA",
      "card_last_4": "4242"
    },
    "refunds": [],
    "tracking_url": null,
    "tracking_number": null,
    "created": "2023-01-12T18:12:58Z",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "ip_address": "10.6.0.61",
    "metadata": {}
  },
  "source": null,
  "resource_data": {
    "site_name": "66f8c067f6ab411c9eaaac106a6948b5"
  },
  "event_timestamp": 1673547263361,
  "event_type": "ECOMM_ORDER_CREATED"
}
```
{% endtab %}
{% endtabs %}

| Name                       | Type     | Description                                                                                                                                   |
| -------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **data.mode**              | _string_ | Environment order was placed in. Possible values are `TEST` or `LIVE`                                                                         |
| **data.id**                | _string_ | A unique identifier for the order                                                                                                             |
| **data.status**            | _string_ | Status of the order. Possible values are `IN_PROGRESS`, `PROCESSED`, `DISPUTED`, `SHIPPED`, `DELIVERED`, `PENDING`, `CANCELLED`, `DISPATCHED` |
| **data.email**             | _string_ | Email associated with the order                                                                                                               |
| **data.invoice\_number**   | _string_ | Invoice number for the order                                                                                                                  |
| **data.items**             | _array_  | List of items selected as part of the order                                                                                                   |
| **data.billing\_address**  | _object_ | List of all fields from the submitted billing address                                                                                         |
| **data.shipping\_address** | _object_ | List of all fields from the submitted shipping address                                                                                        |

### Order Updated

A notification is sent when an order is updated within the store. Event type: `ECOMM_ORDER_UPDATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "mode": "LIVE",
    "id": "9e36bca4-aea5-4e00-b78e-cf855bf82766",
    "status": "PROCESSED",
    "email": "john.doe@duda.co",
    "invoice_number": "ECOM-1065",
    "items": [
      {
        "id": "AkeDXLWQ_3knf3F7V",
        "product_id": "string",
        "variation_id": "string",
        "name": "Grey Ceramic plate",
        "image": "https://cdn.dwhitelabel.com/md/dmtmpl/8023052e-2693-4e9c-a8f1-f86c15ec13eb/dms3rep/multi/grey-ceramic-plate-view1.jpg",
        "options": [
          {
            "name": "Size",
            "value": "Small"
          }
        ],
        "quantity": 1,
        "unit_price": "45.00",
        "unit_weight": null,
        "unit_dimensions": null,
        "total": "45.00",
        "combined_weight": 0,
        "metadata": {}
      }
    ],
    "billing_address": {
      "name": "John Doe",
      "first_name": "John",
      "last_name": "Doe",
      "full_name": "John Doe",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "street_number": "1",
      "street_name": "Main St",
      "city": "Boulder",
      "sub_locality": null,
      "region": "CO",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_address": {
      "name": "John Doe",
      "first_name": "John",
      "last_name": "Doe",
      "full_name": "John Doe",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "street_number": "1",
      "street_name": "Main St",
      "city": "Boulder",
      "sub_locality": null,
      "region": "CO",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_method": {
      "name": "Zone 1",
      "cost": "14.00"
    },
    "shipping_instructions": "My instructions !",
    "discounts": [],
    "taxes": [
      {
        "name": "My tax",
        "amount": "8.85",
        "rate": 0.15
      }
    ],
    "subtotal": "45.00",
    "total": "67.85",
    "payment": {
      "transaction_id": "ch_3MPVHQHiZehw2KYT1r9REUbz",
      "status": "PAID",
      "currency": "CAD",
      "method": "CreditCard",
      "card_brand": "VISA",
      "card_last_4": "4242"
    },
    "refunds": [],
    "tracking_url": null,
    "tracking_number": null,
    "created": "2023-01-12T18:12:58Z",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "ip_address": "10.6.0.61",
    "metadata": {}
  },
  "source": null,
  "resource_data": {
    "site_name": "66f8c067f6ab411c9eaaac106a6948b5"
  },
  "event_timestamp": 1673547263361,
  "event_type": "ECOMM_ORDER_UPDATED"
}
```
{% endtab %}
{% endtabs %}

| Name                       | Type     | Description                                                                                                                                   |
| -------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **data.mode**              | _string_ | Environment order was placed in. Possible values are `TEST` or `LIVE`                                                                         |
| **data.id**                | _string_ | A unique identifier for the order                                                                                                             |
| **data.status**            | _string_ | Status of the order. Possible values are `IN_PROGRESS`, `PROCESSED`, `DISPUTED`, `SHIPPED`, `DELIVERED`, `PENDING`, `CANCELLED`, `DISPATCHED` |
| **data.email**             | _string_ | Email associated with the order                                                                                                               |
| **data.invoice\_number**   | _string_ | Invoice number for the order                                                                                                                  |
| **data.items**             | _array_  | List of items selected as part of the order                                                                                                   |
| **data.billing\_address**  | _object_ | List of all fields from the submitted billing address                                                                                         |
| **data.shipping\_address** | _object_ | List of all fields from the submitted shipping address                                                                                        |

### Category Created

A notification is sent when a new category is created within the store. Event type: `CATEGORY_CREATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data":{
    "id":"aSmkM6Zp",
    "title":"Tops",
    "description":null,
    "parent_id": "hTPEQfON",
    "image":null,
    "seo":null,
    "subcategories":[],
    "products":[]
	},
  "source":null,
  "resource_data":{
      "site_name":"46e1a983"
   },
   "event_timestamp":1678901369468,
   "event_type":"CATEGORY_CREATED"
}
```
{% endtab %}
{% endtabs %}

| Name                   | Type     | Description                                                                                |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------ |
| **data.id**            | _string_ | A unique identifier for the category                                                       |
| **data.title**         | _string_ | Title of the category created                                                              |
| **data.parent\_id**    | _string_ | Unique identifier of parent category. Only has value if category created is a subcategory. |
| **data.image**         | _object_ | The alt-text and url of image                                                              |
| **data.subcategories** | _array_  | List of subcategory children                                                               |
| **data.products**      | _array_  |                                                                                            |

### Category Updated

A notification is sent when a category's details are updated. Event type: `CATEGORY_UPDATED`

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data":{
  "id":"hTPEQfON",
  "title":"Tops",
  "description":null,
  "parent_id":null,
  "image":{
    "alt":null,
    "url":"https://irp.cdn-website.com/md/pexels/dms3rep/multi/pexels-photo-13049673.jpeg"
	},
  "seo":null,
  "subcategories":[{
    "id":"Z6vnXMX1",
    "title":"Sweaters",
    "order":0
  }],
  "products":[{
    "id":"1nfqecTl",
    "name":"Hooded Sweater",
    "order":0
    },
    {
    "id":"C29ZkeIV",
    "name":"Knitted Sweater",
    "order":1
  }]
},
"source":null,
"resource_data":{
	"site_name":"46e1a983"
},
"event_timestamp":1678902273592,
"event_type":"CATEGORY_UPDATED"
}
```
{% endtab %}
{% endtabs %}

| Name                   | Type     | Description                                                                                |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------ |
| **data.id**            | _string_ | A unique identifier for the category                                                       |
| **data.title**         | _string_ | Title of the category                                                                      |
| **data.parent\_id**    | _string_ | Unique identifier of parent category. Only has value if category created is a subcategory. |
| **data.image**         | _object_ | The alt-text and url of image                                                              |
| **data.subcategories** | _array_  | List of subcategories assigned to category                                                 |
| **data.products**      | _array_  | List of products assigned to category                                                      |
