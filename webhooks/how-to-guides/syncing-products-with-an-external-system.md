# Syncing Products With an External System

This guide covers how to use Duda's Native eCommerce Webhooks to sync products in an external system when an order is created, updated, or deleted. This allows you to accurately catalog changes in your native store and reflect those changes in your own system.

### Requirements

To work with this guide, you’ll need to have your Duda Webhooks configured. To learn how, see [Configuring Webhooks](../tutorials/configuring-webhooks.md).

### Order is Created

For this example, the customer purchased one grey ceramic plate. Whenever a new order is created within the store a notification is sent, like in the example below.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "mode": "LIVE",
    "currency": "USD",
    "external_id": "my-custom-id-123",
    "status": "PROCESSED",
    "invoice_number": "ECOMM-1001",
    "email": "john.smith@duda.co",
    "invoice_number": "ECOM-1065",
    "items": [
      {
        "product_id": "string",
        "variation_id": "string",
        "external_product_id": "string",
      	"external_variation_id": "string",
        "name": "Grey Ceramic plate",
        "image": "https://cdn.dwhitelabel.com/md/dmtmpl/8023052e-2693-4e9c-a8f1-f86c15ec13eb/dms3rep/multi/grey-ceramic-plate-view1.jpg",
        "options": [
          {
            "name": "Size",
            "value": "Small"
          }
        ],
        "quantity": 1,
        "shippable": true,
        "unit_price": 45.00,
        "unit_weight": 0,
        "unit_dimensions": {
        	"height": 0,
        	"width": 0,
        	"length": 0
      	},
      	"total": 0,
      	"combined_weight": 0,
      	"metadata": "string"
      }
    ],
		"billing_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_method": {
      "name": "Zone 1",
      "cost": 14.00
    },
    "shipping_instructions": "My instructions !",
    "discounts": [
    	{
      	"id": "string",
      	"savings": 5,
      	"name": "My discount",
      	"type": "string"
    	}
  	],
  	"taxes": [
      {
        "name": "My tax",
        "amount": 8.85,
        "rate": 0.15
      }
    ],
    	"subtotal": 45.00,
    	"total": 62.85,
    	"payment": {
      	"transaction_id": "ch_3MPVHQHiZehw2KYT1r9REUbz",
      	"status": "PAID",
      	"currency": "CAD",
      	"method": "CreditCard",
      	"card_brand": "VISA",
      	"card_last_4": "4242"
    	},
    "refunds": [
      {}
    ],
    "tracking_url": "string",
    "tracking_number": "string",
    "created": "2023-01-12T18:12:58Z",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "ip_address": "10.6.0.61",
    "metadata": "string"
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

The most important information is the items object array, specifically the `id` and `quantity`. You can update your external system to reflect that the grey ceramic plate with the unique item `id` is decremented in total amount by the `quantity` from this webhook event.

### Order is Updated

Next, the customer updates their order to purchase 3 ceramic plates instead of just 1. Similar to creating an order, you can update the order and send a notification via a webhook event. The example below shows the updated item object array.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "mode": "LIVE",
    "currency": "USD",
    "external_id": "my-custom-id-123",
    "status": "PROCESSED",
    "invoice_number": "ECOMM-1001",
    "email": "john.smith@duda.co",
    "invoice_number": "ECOM-1065",
    "items": [
      {
        "product_id": "string",
        "variation_id": "string",
        "external_product_id": "string",
      	"external_variation_id": "string",
        "name": "Grey Ceramic plate",
        "image": "https://cdn.dwhitelabel.com/md/dmtmpl/8023052e-2693-4e9c-a8f1-f86c15ec13eb/dms3rep/multi/grey-ceramic-plate-view1.jpg",
        "options": [
          {
            "name": "Size",
            "value": "Small"
          }
        ],
        "quantity": 3,
        "shippable": true,
        "unit_price": 45.00,
        "unit_weight": 0,
        "unit_dimensions": {
        	"height": 0,
        	"width": 0,
        	"length": 0
      	},
      	"total": 0,
      	"combined_weight": 0,
      	"metadata": "string"
      }
    ],
		"billing_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_method": {
      "name": "Zone 1",
      "cost": 14.00
    },
    "shipping_instructions": "My instructions !",
    "discounts": [
    	{
      	"id": "string",
      	"savings": 15,
      	"name": "My discount",
      	"type": "string"
    	}
  	],
  	"taxes": [
      {
        "name": "My tax",
        "amount": 22.35,
        "rate": 0.15
      }
    ],
    	"subtotal": 152.35,
    	"total": 62.85,
    	"payment": {
      	"transaction_id": "ch_3MPVHQHiZehw2KYT1r9REUbz",
      	"status": "PAID",
      	"currency": "CAD",
      	"method": "CreditCard",
      	"card_brand": "VISA",
      	"card_last_4": "4242"
    	},
    "refunds": [
      {}
    ],
    "tracking_url": "string",
    "tracking_number": "string",
    "created": "2023-01-12T18:12:58Z",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "ip_address": "10.6.0.61",
    "metadata": "string"
  },
  "source": null,
  "resource_data": {
    "site_name": "66f8c067f6ab411c9eaaac106a6948b5"
  },
  "event_timestamp": 1673547263361,
  "event_type": "ECOMM_ORDER_STATUS_UPDATED"
}
```
{% endtab %}
{% endtabs %}

You can again take the `id` and `quantity` fields from the items object array to update your external system to decrement the total number of ceramic plates in inventory by 3 instead of just 1.

### Order is Deleted

If the customer decides that they no longer want to order these ceramic plates and wants to cancel their entire order, you need to update the inventory of ceramic plates in your external system. You can send a notification from a webhook notifying that this order has been deleted, like in the example below.

{% tabs %}
{% tab title="JSON" %}
```json
{
  "data": {
    "mode": "LIVE",
    "currency": "USD",
    "external_id": "my-custom-id-123",
    "status": "PROCESSED",
    "invoice_number": "ECOMM-1001",
    "email": "john.smith@duda.co",
    "invoice_number": "ECOM-1065",
    "items": [
      {
        "product_id": "string",
        "variation_id": "string",
        "external_product_id": "string",
      	"external_variation_id": "string",
        "name": "Grey Ceramic plate",
        "image": "https://cdn.dwhitelabel.com/md/dmtmpl/8023052e-2693-4e9c-a8f1-f86c15ec13eb/dms3rep/multi/grey-ceramic-plate-view1.jpg",
        "options": [
          {
            "name": "Size",
            "value": "Small"
          }
        ],
        "quantity": 3,
        "shippable": true,
        "unit_price": 45.00,
        "unit_weight": 0,
        "unit_dimensions": {
        	"height": 0,
        	"width": 0,
        	"length": 0
      	},
      	"total": 0,
      	"combined_weight": 0,
      	"metadata": "string"
      }
    ],
		"billing_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_address": {
      "name": "John Smith",
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "address_1": "1 Main St",
      "address_2": "Apt C",
      "city": "Boulder",
      "region": "CO",
      "sub_locality": null,
      "street_number": "1",
      "street_name": "Main St",
      "country": "US",
      "postal_code": "12345",
      "phone": "555-5555"
    },
    "shipping_method": {
      "name": "Zone 1",
      "cost": 14.00
    },
    "shipping_instructions": "My instructions !",
    "discounts": [
    	{
      	"id": "string",
      	"savings": 15,
      	"name": "My discount",
      	"type": "string"
    	}
  	],
  	"taxes": [
      {
        "name": "My tax",
        "amount": 22.35,
        "rate": 0.15
      }
    ],
    	"subtotal": 152.35,
    	"total": 62.85,
    	"payment": {
      	"transaction_id": "ch_3MPVHQHiZehw2KYT1r9REUbz",
      	"status": "PAID",
      	"currency": "CAD",
      	"method": "CreditCard",
      	"card_brand": "VISA",
      	"card_last_4": "4242"
    	},
    "refunds": [
      {}
    ],
    "tracking_url": "string",
    "tracking_number": "string",
    "created": "2023-01-12T18:12:58Z",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "ip_address": "10.6.0.61",
    "metadata": "string"
  },
  "source": null,
  "resource_data": {
    "site_name": "66f8c067f6ab411c9eaaac106a6948b5"
  },
  "event_timestamp": 1673547263361,
  "event_type": "ECOMM_ORDER_DELETED"
}
```
{% endtab %}
{% endtabs %}

You can then take that same `id` and `quantity` parameters from the items object array to update your external system with the 3 ceramic plates that were a part of this order.
