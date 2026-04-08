---
name: shopify-admin
description: "Complete Shopify REST Admin API \u2014 products, variants, images, metafields,\
  \ orders, fulfillments, refunds, transactions, customers, inventory, collections,\
  \ draft orders, webhooks, shop info, and locations. Use when the user mentions shopify,\
  \ product, order, customer, inventory, shop, e-commerce, ecommerce, fulfillment,\
  \ collection, variant, draft order, webhook, metafield."
version: 1.0.0
skill_type: external
base_url_env: SHOPIFY_BASE_URL
auth_env_var: SHOPIFY_ACCESS_TOKEN
auth_type: header
triggers:
  - shopify
  - product
  - order
  - customer
  - inventory
  - shop
  - e-commerce
  - ecommerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires SHOPIFY_BASE_URL and SHOPIFY_ACCESS_TOKEN environment variables.
---

# Shopify-Admin

Complete Shopify REST Admin API — products, variants, images, metafields, orders, fulfillments, refunds, transactions, customers, inventory, collections, draft orders, webhooks, shop info, and locations. Use when the user mentions shopify, product, order, customer, inventory, shop, e-commerce, ecommerce, fulfillment, collection, variant, draft order, webhook, metafield.

## API Endpoints

- **GET** `/products.json` - List all products
- **GET** `/products/{product_id}.json` - Get a single product
- **POST** `/products.json` - Create a product
- **PUT** `/products/{product_id}.json` - Update a product
- **DELETE** `/products/{product_id}.json` - Delete a product
- **GET** `/products/count.json` - Get product count
- **GET** `/products/{product_id}/variants.json` - List variants for a product
- **GET** `/variants/{variant_id}.json` - Get a single variant
- **POST** `/products/{product_id}/variants.json` - Create a variant
- **PUT** `/variants/{variant_id}.json` - Update a variant
- **DELETE** `/products/{product_id}/variants/{variant_id}.json` - Delete a variant
- **GET** `/products/{product_id}/images.json` - List product images
- **GET** `/products/{product_id}/images/{image_id}.json` - Get a single image
- **POST** `/products/{product_id}/images.json` - Create a product image
- **PUT** `/products/{product_id}/images/{image_id}.json` - Update a product image

## Actions

- list: List all products (GET /products.json)
- list_products: Get a single product (GET /products/{product_id}.json)
- create: Create a product (POST /products.json)
- update_products: Update a product (PUT /products/{product_id}.json)
- delete_products: Delete a product (DELETE /products/{product_id}.json)
- list_count_json: Get product count (GET /products/count.json)
- list_variants_json: List variants for a product (GET /products/{product_id}/variants.json)
- list_variants: Get a single variant (GET /variants/{variant_id}.json)
- create_variants_json: Create a variant (POST /products/{product_id}/variants.json)
- update_variants: Update a variant (PUT /variants/{variant_id}.json)
- delete_variants: Delete a variant (DELETE /products/{product_id}/variants/{variant_id}.json)
- list_images_json: List product images (GET /products/{product_id}/images.json)
- list_images: Get a single image (GET /products/{product_id}/images/{image_id}.json)
- create_images_json: Create a product image (POST /products/{product_id}/images.json)
- put_images: Update a product image (PUT /products/{product_id}/images/{image_id}.json)

## Fields

### Product
- `title`: string [REQUIRED for create] - Product title
- `body_html`: string [OPTIONAL] - Product description in HTML
- `vendor`: string [OPTIONAL] - Product vendor name
- `product_type`: string [OPTIONAL] - Product type/category
- `status`: string [OPTIONAL] - `active`, `archived`, or `draft` (default: `active`)
- `tags`: string [OPTIONAL] - Comma-separated tags (e.g., `"summer, sale, new"`)
- `template_suffix`: string [OPTIONAL] - Theme template suffix
- `published_scope`: string [OPTIONAL] - `web` (online store only) or `global` (all channels)
- `variants`: array [OPTIONAL] - Array of variant objects (see Variant fields below)
- `images`: array [OPTIONAL] - Array of image objects with `src` URLs
- `options`: array [OPTIONAL] - Array of up to 3 option objects: `{"name": "Size", "values": ["S", "M", "L"]}`
- `metafields`: array [OPTIONAL] - Array of metafield objects for creation

### Product Variant
- `option1`: string [REQUIRED if product has options] - First option value (e.g., `"Small"`)
- `option2`: string [OPTIONAL] - Second option value (e.g., `"Red"`)
- `option3`: string [OPTIONAL] - Third option value (e.g., `"Cotton"`)
- `price`: string [OPTIONAL] - Variant price (e.g., `"29.99"`)
- `compare_at_price`: string [OPTIONAL] - Original price for sale display
- `sku`: string [OPTIONAL] - Stock keeping unit
- `barcode`: string [OPTIONAL] - Barcode (ISBN, UPC, GTIN, etc.)
- `weight`: number [OPTIONAL] - Weight value
- `weight_unit`: string [OPTIONAL] - `g`, `kg`, `oz`, or `lb`
- `inventory_quantity`: integer [OPTIONAL] - Initial stock quantity (only on create)
- `inventory_management`: string [OPTIONAL] - `shopify` to enable inventory tracking, or `null`
- `inventory_policy`: string [OPTIONAL] - `deny` (stop selling at 0) or `continue`
- `requires_shipping`: boolean [OPTIONAL] - Whether variant requires shipping (default: true)
- `taxable`: boolean [OPTIONAL] - Whether variant is taxable (default: true)

### Product Image
- `src`: string [REQUIRED for create via URL] - Image source URL
- `attachment`: string [REQUIRED for create via base64] - Base64-encoded image data
- `filename`: string [OPTIONAL] - Image filename
- `position`: integer [OPTIONAL] - Image position (1-indexed, position 1 is the main image)
- `alt`: string [OPTIONAL] - Alt text for accessibility
- `variant_ids`: array [OPTIONAL] - Array of variant IDs to associate with the image

### Order
- `line_items`: array [REQUIRED for create] - Array of line item objects
- `line_items[].variant_id`: integer [REQUIRED per item] - Variant ID
- `line_items[].quantity`: integer [REQUIRED per item] - Quantity
- `line_items[].price`: string [OPTIONAL] - Override price
- `customer`: object [OPTIONAL] - Customer object with `id` field
- `email`: string [OPTIONAL] - Customer email
- `billing_address`: object [OPTIONAL] - Billing address object
- `shipping_address`: object [OPTIONAL] - Shipping address object
- `financial_status`: string [OPTIONAL] - `pending`, `authorized`, `partially_paid`, `paid`, `partially_refunded`, `refunded`, `voided`
- `fulfillment_status`: string [OPTIONAL] - `null` (unfulfilled), `partial`, `fulfilled`
- `note`: string [OPTIONAL] - Internal order note
- `tags`: string [OPTIONAL] - Comma-separated tags
- `shipping_lines`: array [OPTIONAL] - Array of shipping line objects
- `transactions`: array [OPTIONAL] - Array of transaction objects
- `send_receipt`: boolean [OPTIONAL] - Send order receipt to customer (default: false)
- `inventory_behaviour`: string [OPTIONAL] - `bypass`, `decrement_ignoring_policy`, `decrement_obeying_policy`
- `discount_codes`: array [OPTIONAL] - Array of discount code objects
- `tax_lines`: array [OPTIONAL] - Array of tax line objects
- `currency`: string [OPTIONAL] - Three-letter ISO 4217 currency code

### Customer
- `email`: string [REQUIRED for create] - Customer email address
- `first_name`: string [OPTIONAL] - First name
- `last_name`: string [OPTIONAL] - Last name
- `phone`: string [OPTIONAL] - Phone number in E.164 format (e.g., `"+14155551234"`)
- `verified_email`: boolean [OPTIONAL] - Whether email is verified (default: true for API-created)
- `send_email_invite`: boolean [OPTIONAL] - Send account invitation email
- `password`: string [OPTIONAL] - Customer password (only on create)
- `password_confirmation`: string [OPTIONAL] - Must match `password`
- `tags`: string [OPTIONAL] - Comma-separated tags
- `note`: string [OPTIONAL] - Internal note about customer
- `tax_exempt`: boolean [OPTIONAL] - Whether customer is tax exempt
- `addresses`: array [OPTIONAL] - Array of address objects
- `metafields`: array [OPTIONAL] - Array of metafield objects
- `state`: string [READ-ONLY] - `disabled`, `invited`, `enabled`, `declined`

### Customer Address
- `address1`: string [OPTIONAL] - Street address line 1
- `address2`: string [OPTIONAL] - Street address line 2
- `city`: string [OPTIONAL] - City
- `province`: string [OPTIONAL] - State/province
- `country`: string [OPTIONAL] - Country (full name or ISO code)
- `zip`: string [OPTIONAL] - Postal/ZIP code
- `phone`: string [OPTIONAL] - Phone number
- `name`: string [OPTIONAL] - Full name
- `company`: string [OPTIONAL] - Company name
- `first_name`: string [OPTIONAL] - First name
- `last_name`: string [OPTIONAL] - Last name
- `default`: boolean [OPTIONAL] - Set as default address

### Metafield (any resource)
- `namespace`: string [REQUIRED] - Grouping namespace (e.g., `"custom"`, `"my_app"`)
- `key`: string [REQUIRED] - Unique key within namespace
- `value`: string [REQUIRED] - Metafield value
- `type`: string [REQUIRED] - Value type: `single_line_text_field`, `multi_line_text_field`, `number_integer`, `number_decimal`, `json`, `boolean`, `date`, `date_time`, `url`, `color`, `weight`, `volume`, `dimension`, `rating`

### Inventory Level
- `inventory_item_id`: integer [REQUIRED] - Inventory item ID (from variant's `inventory_item_id`)
- `location_id`: integer [REQUIRED] - Location ID
- `available`: integer [REQUIRED for set] - Absolute inventory quantity
- `available_adjustment`: integer [REQUIRED for adjust] - Relative adjustment (+/-)

### Custom Collection
- `title`: string [REQUIRED for create] - Collection title
- `body_html`: string [OPTIONAL] - Collection description in HTML
- `published`: boolean [OPTIONAL] - Whether published (default: true)
- `image`: object [OPTIONAL] - Collection image object with `src` or `attachment`
- `sort_order`: string [OPTIONAL] - `alpha-asc`, `alpha-desc`, `best-selling`, `created`, `created-desc`, `manual`, `price-asc`, `price-desc`

### Smart Collection
- `title`: string [REQUIRED for create] - Collection title
- `rules`: array [REQUIRED for create] - Array of rule objects
- `rules[].column`: string [REQUIRED] - Rule column: `tag`, `title`, `type`, `vendor`, `variant_price`, `variant_compare_at_price`, `variant_weight`, `variant_inventory`, `variant_title`
- `rules[].relation`: string [REQUIRED] - `equals`, `not_equals`, `greater_than`, `less_than`, `starts_with`, `ends_with`, `contains`, `not_contains`
- `rules[].condition`: string [REQUIRED] - Value to match
- `disjunctive`: boolean [OPTIONAL] - `true` = OR logic, `false` = AND logic (default: false)
- `published`: boolean [OPTIONAL] - Whether published
- `body_html`: string [OPTIONAL] - Description in HTML
- `sort_order`: string [OPTIONAL] - Same options as custom collection

### Draft Order
- `line_items`: array [REQUIRED for create] - Array of line item objects
- `line_items[].variant_id`: integer [CONDITIONAL] - Variant ID (if existing product)
- `line_items[].title`: string [CONDITIONAL] - Title (if custom line item)
- `line_items[].price`: string [CONDITIONAL] - Price (required for custom items)
- `line_items[].quantity`: integer [REQUIRED] - Quantity
- `customer`: object [OPTIONAL] - Customer with `id` field
- `billing_address`: object [OPTIONAL] - Billing address object
- `shipping_address`: object [OPTIONAL] - Shipping address object
- `note`: string [OPTIONAL] - Note
- `tags`: string [OPTIONAL] - Comma-separated tags
- `applied_discount`: object [OPTIONAL] - Discount: `{"value": "10.0", "value_type": "percentage", "title": "10% OFF"}`
- `shipping_line`: object [OPTIONAL] - Shipping: `{"title": "Standard", "price": "5.99"}`
- `tax_exempt`: boolean [OPTIONAL] - Whether tax exempt
- `use_customer_default_address`: boolean [OPTIONAL] - Use customer's default address

### Fulfillment
- `line_items_by_fulfillment_order`: array [REQUIRED] - Array of fulfillment order references
- `line_items_by_fulfillment_order[].fulfillment_order_id`: integer [REQUIRED] - Fulfillment order ID
- `line_items_by_fulfillment_order[].fulfillment_order_line_items`: array [OPTIONAL] - Specific line items (omit for all)
- `tracking_info`: object [OPTIONAL] - Tracking: `{"number": "1234", "url": "https://...", "company": "UPS"}`
- `notify_customer`: boolean [OPTIONAL] - Send shipping notification (default: false)
- `message`: string [OPTIONAL] - Message included in notification

### Webhook
- `topic`: string [REQUIRED for create] - Event topic (e.g., `orders/create`, `products/update`, `customers/delete`, `app/uninstalled`)
- `address`: string [REQUIRED for create] - Callback URL (must be HTTPS)
- `format`: string [OPTIONAL] - `json` (default) or `xml`
- `fields`: array [OPTIONAL] - Specific fields to include in payload
- `metafield_namespaces`: array [OPTIONAL] - Metafield namespaces to include

### Refund
- `shipping`: object [OPTIONAL] - Shipping refund: `{"full_refund": true}` or `{"amount": "5.00"}`
- `refund_line_items`: array [OPTIONAL] - Array of line items to refund
- `refund_line_items[].line_item_id`: integer [REQUIRED per item] - Order line item ID
- `refund_line_items[].quantity`: integer [REQUIRED per item] - Quantity to refund
- `refund_line_items[].restock_type`: string [OPTIONAL] - `no_restock`, `cancel`, `return`, `legacy_restock`
- `notify`: boolean [OPTIONAL] - Send refund notification to customer
- `note`: string [OPTIONAL] - Refund note
- `transactions`: array [OPTIONAL] - Manual refund transactions

### Transaction
- `kind`: string [REQUIRED] - `authorization`, `capture`, `sale`, `void`, `refund`
- `amount`: string [OPTIONAL] - Transaction amount (e.g., `"29.99"`)
- `currency`: string [OPTIONAL] - ISO 4217 currency code
- `parent_id`: integer [OPTIONAL] - Parent transaction ID (for capture/void/refund)

## Example Request Bodies

**Create Product with Variants and Images:**
```json
{
  "product": {
    "title": "Classic T-Shirt",
    "body_html": "<p>Comfortable cotton t-shirt available in multiple sizes.</p>",
    "vendor": "MyBrand",
    "product_type": "Apparel",
    "status": "active",
    "tags": "clothing, summer, cotton",
    "options": [
      {"name": "Size", "values": ["S", "M", "L", "XL"]},
      {"name": "Color", "values": ["White", "Black", "Navy"]}
    ],
    "variants": [
      {"option1": "S", "option2": "White", "price": "24.99", "sku": "TSHIRT-S-WHT", "inventory_management": "shopify", "inventory_quantity": 100},
      {"option1": "M", "option2": "White", "price": "24.99", "sku": "TSHIRT-M-WHT", "inventory_management": "shopify", "inventory_quantity": 150},
      {"option1": "L", "option2": "Black", "price": "24.99", "sku": "TSHIRT-L-BLK", "inventory_management": "shopify", "inventory_quantity": 120}
    ],
    "images": [
      {"src": "https://example.com/images/tshirt-front.jpg", "alt": "Classic T-Shirt Front"},
      {"src": "https://example.com/images/tshirt-back.jpg", "alt": "Classic T-Shirt Back"}
    ]
  }
}
```

**Create Customer with Address:**
```json
{
  "customer": {
    "first_name": "Jane",
    "last_name": "Doe",
    "email": "jane.doe@example.com",
    "phone": "+14155551234",
    "verified_email": true,
    "tags": "vip, wholesale",
    "note": "Wholesale customer since 2023",
    "addresses": [
      {
        "address1": "123 Main St",
        "city": "San Francisco",
        "province": "CA",
        "country": "US",
        "zip": "94105",
        "default": true
      }
    ]
  }
}
```

**Create Order:**
```json
{
  "order": {
    "line_items": [
      {"variant_id": 447654321, "quantity": 2},
      {"variant_id": 447654322, "quantity": 1}
    ],
    "customer": {"id": 207119551},
    "email": "jane.doe@example.com",
    "financial_status": "pending",
    "shipping_address": {
      "first_name": "Jane",
      "last_name": "Doe",
      "address1": "123 Main St",
      "city": "San Francisco",
      "province": "CA",
      "country": "US",
      "zip": "94105"
    },
    "send_receipt": true,
    "inventory_behaviour": "decrement_obeying_policy"
  }
}
```

**Cancel an Order:**
```json
{
  "reason": "customer",
  "email": true,
  "restock": true
}
```

**Create Refund for an Order:**
```json
{
  "refund": {
    "notify": true,
    "note": "Customer returned damaged item",
    "shipping": {"full_refund": true},
    "refund_line_items": [
      {
        "line_item_id": 518995019,
        "quantity": 1,
        "restock_type": "return"
      }
    ]
  }
}
```

**Adjust Inventory Level:**
```json
{
  "location_id": 905684977,
  "inventory_item_id": 808950810,
  "available_adjustment": -5
}
```

**Set Inventory Level (absolute):**
```json
{
  "location_id": 905684977,
  "inventory_item_id": 808950810,
  "available": 42
}
```

**Create Smart Collection (auto-populated by rules):**
```json
{
  "smart_collection": {
    "title": "Summer Sale Items",
    "rules": [
      {"column": "tag", "relation": "equals", "condition": "summer"},
      {"column": "variant_compare_at_price", "relation": "greater_than", "condition": "0"}
    ],
    "disjunctive": false,
    "published": true,
    "sort_order": "best-selling"
  }
}
```

**Create Draft Order with Custom Line Item and Discount:**
```json
{
  "draft_order": {
    "line_items": [
      {"variant_id": 447654321, "quantity": 2},
      {"title": "Custom Engraving", "price": "15.00", "quantity": 1}
    ],
    "customer": {"id": 207119551},
    "applied_discount": {
      "value": "10.0",
      "value_type": "percentage",
      "title": "10% VIP Discount"
    },
    "shipping_line": {
      "title": "Standard Shipping",
      "price": "5.99"
    },
    "note": "Please gift wrap"
  }
}
```

**Create Fulfillment with Tracking:**
```json
{
  "fulfillment": {
    "line_items_by_fulfillment_order": [
      {
        "fulfillment_order_id": 1046000778,
        "fulfillment_order_line_items": [
          {"id": 1058737487, "quantity": 1}
        ]
      }
    ],
    "tracking_info": {
      "number": "1Z999AA10123456784",
      "url": "https://www.ups.com/track?tracknum=1Z999AA10123456784",
      "company": "UPS"
    },
    "notify_customer": true,
    "message": "Your order is on its way!"
  }
}
```

**Create Webhook:**
```json
{
  "webhook": {
    "topic": "orders/create",
    "address": "https://myapp.example.com/webhooks/orders",
    "format": "json"
  }
}
```

**Create Product Metafield:**
```json
{
  "metafield": {
    "namespace": "custom",
    "key": "care_instructions",
    "value": "Machine wash cold, tumble dry low",
    "type": "single_line_text_field"
  }
}
```

**List Orders with Filters (Query Params):**
Query parameters: `status=open&financial_status=paid&fulfillment_status=unfulfilled&limit=50&created_at_min=2024-01-01T00:00:00-05:00`

**Search Customers (Query Params):**
Query parameters: `query=email:jane@example.com&limit=10`
