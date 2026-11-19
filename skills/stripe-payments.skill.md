---
name: stripe-payments
description: "Complete Stripe payment processing \u2014 customers, payment intents, subscriptions, invoices, products, prices, refunds, disputes, payouts, checkout, coupons, webhooks, and balance. Use when the user mentions stripe, payment, charge, invoice, subscription, customer, refund, billing, checkout, payout, dispute, product, price, coupon. (API 2022-11-15). Native /stripe/* routes are available when STRIPE_SECRET_KEY is set (preferred). Falls back to STRIPE_API_KEY for backward compatibility."
version: 1.0.0
skill_type: external
base_url_env: STRIPE_BASE_URL
auth_env_var: STRIPE_API_KEY
auth_type: bearer
triggers:
  - stripe
  - payment
  - charge
  - invoice
  - subscription
  - customer
  - refund
  - billing
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: 'External skill: Requires STRIPE_BASE_URL and STRIPE_API_KEY environment
  variables. Native routes: Set STRIPE_SECRET_KEY (and optionally STRIPE_PUBLISHABLE_KEY,
  STRIPE_WEBHOOK_SECRET) to enable /stripe/* endpoints directly in this API.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Stripe-Payments

Complete Stripe payment processing — customers, payment intents, subscriptions, invoices, products, prices, refunds, disputes, payouts, checkout, coupons, webhooks, and balance. Use when the user mentions stripe, payment, charge, invoice, subscription, customer, refund, billing, checkout, payout, dispute, product, price, coupon. (API 2022-11-15). Native /stripe/* routes are available when STRIPE_SECRET_KEY is set (preferred). Falls back to STRIPE_API_KEY for backward compatibility.


## API Endpoints

- **GET** `/v1/products/search` - Search for products you’ve previously created using Stripe’s Search
- **POST** `/v1/products` - Creates a new product object.
- **DELETE** `/v1/products/{id}` - Delete a product. Deleting a product is only possible if it has no prices associated with it. Additionally, deleting
- **GET** `/v1/coupons` - Returns a list of your coupons.
- **POST** `/v1/coupons` - You can create coupons easily via the coupon management page of
- **DELETE** `/v1/coupons/{coupon}` - You can delete coupons via the coupon management page of the
- **GET** `/v1/invoiceitems` - Returns a list of your invoice items. Invoice items are returned sorted by creation date, with the most recently
- **POST** `/v1/invoiceitems` - Creates an item to be added to a draft invoice (up to 250 items per invoice). If no invoice is specified, the item
- **DELETE** `/v1/invoiceitems/{invoiceitem}` - Deletes an invoice item, removing it from an invoice. Deleting invoice items is only possible when they’re not
- **GET** `/v1/plans` - Returns a list of your plans.
- **POST** `/v1/plans` - You can now model subscriptions more flexibly using the Prices API. It replaces the Plans API
- **DELETE** `/v1/plans/{plan}` - Deleting plans means new subscribers can’t be added. Existing subscribers aren’t affected.
- **GET** `/v1/subscriptions/search` - Search for subscriptions you’ve previously created using Stripe’s Pri (POST /v1/plans)
- **GET** `/v1/webhook_endpoints` - List all webhook endpoints
- **POST** `/v1/webhook_endpoints` - Create a webhook endpoint

## Actions

- search: Search for products you’ve previously created using Stripe’s Search (GET /v1/products/search)
- create: Creates a new product object. (POST /v1/products)
- delete: Delete a product. Deleting a product is only possible if it has no prices associ (DELETE /v1/products/{id})
- list: Returns a list of your coupons. (GET /v1/coupons)
- create_coupons: You can create coupons easily via the coupon management page of (POST /v1/coupons)
- delete_coupons: You can delete coupons via the coupon management page of the (DELETE /v1/coupons/{coupon})
- list_invoiceitems: Returns a list of your invoice items. Invoice items are returned sorted by creat (GET /v1/invoiceitems)
- create_invoiceitems: Creates an item to be added to a draft invoice (up to 250 items per invoice). If (POST /v1/invoiceitems)
- delete_invoiceitems: Deletes an invoice item, removing it from an invoice. Deleting invoice items is (DELETE /v1/invoiceitems/{invoiceitem})
- list_plans: Returns a list of your plans. (GET /v1/plans)
- create_plans: You can now model subscriptions more flexibly using the Prices API. It replaces (POST /v1/plans)
- delete_plans: Deleting plans means new subscribers can’t be added. Existing subscribers aren’t (DELETE /v1/plans/{plan})
- search_subscriptions: Search for subscriptions you’ve previously created using Stripe’s Pri (POST /v1/ (GET /v1/subscriptions/search)
- list_webhook_endpoints: List all webhook endpoints (GET /v1/webhook_endpoints)
- create_webhook_endpoints: Create a webhook endpoint (POST /v1/webhook_endpoints)

## Fields

### Customer
- `email`: string [OPTIONAL] - Customer email address
- `name`: string [OPTIONAL] - Full name
- `phone`: string [OPTIONAL] - Phone number
- `description`: string [OPTIONAL] - Description
- `metadata`: object [OPTIONAL] - Key-value pairs (max 50 keys)
- `payment_method`: string [OPTIONAL] - Default payment method ID (pm_)
- `address`: object [OPTIONAL] - {line1, line2, city, state, postal_code, country}

### Payment Intent
- `amount`: integer [REQUIRED] - Amount in cents (e.g., 5000 = $50.00)
- `currency`: string [REQUIRED] - Three-letter ISO code (usd, eur, gbp, brl, etc.)
- `customer`: string [OPTIONAL] - Customer ID (cus_)
- `payment_method`: string [OPTIONAL] - Payment method ID (pm_)
- `description`: string [OPTIONAL] - Description shown on statement
- `metadata`: object [OPTIONAL] - Key-value pairs
- `confirm`: boolean [OPTIONAL] - Confirm immediately (default false)
- `automatic_payment_methods[enabled]`: boolean [OPTIONAL] - Enable auto payment methods
- `receipt_email`: string [OPTIONAL] - Email for receipt
- `statement_descriptor`: string [OPTIONAL] - Statement descriptor (max 22 chars)

### Subscription
- `customer`: string [REQUIRED] - Customer ID (cus_)
- `items[0][price]`: string [REQUIRED] - Price ID (price_)
- `items[0][quantity]`: integer [OPTIONAL] - Quantity (default 1)
- `default_payment_method`: string [OPTIONAL] - Payment method ID
- `trial_period_days`: integer [OPTIONAL] - Free trial days
- `cancel_at_period_end`: boolean [OPTIONAL] - Cancel at period end
- `proration_behavior`: string [OPTIONAL] - create_prorations, none, always_invoice
- `metadata`: object [OPTIONAL] - Key-value pairs

### Invoice
- `customer`: string [REQUIRED] - Customer ID
- `auto_advance`: boolean [OPTIONAL] - Auto-finalize (default true)
- `collection_method`: string [OPTIONAL] - charge_automatically or send_invoice
- `days_until_due`: integer [OPTIONAL] - Days until due (for send_invoice)
- `description`: string [OPTIONAL] - Description
- `metadata`: object [OPTIONAL] - Key-value pairs

### Product
- `name`: string [REQUIRED] - Product name
- `description`: string [OPTIONAL] - Description
- `active`: boolean [OPTIONAL] - Whether active (default true)
- `metadata`: object [OPTIONAL] - Key-value pairs
- `images`: array [OPTIONAL] - Up to 8 image URLs

### Price
- `product`: string [REQUIRED] - Product ID (prod_) or inline product data
- `unit_amount`: integer [REQUIRED for one-time] - Amount in cents
- `currency`: string [REQUIRED] - Three-letter ISO code
- `recurring[interval]`: string [REQUIRED for recurring] - day, week, month, year
- `recurring[interval_count]`: integer [OPTIONAL] - Interval multiplier (default 1)
- `nickname`: string [OPTIONAL] - Nickname for internal use

### Checkout Session
- `mode`: string [REQUIRED] - payment, setup, or subscription
- `success_url`: string [REQUIRED] - Redirect URL on success
- `cancel_url`: string [OPTIONAL] - Redirect URL on cancel
- `line_items[0][price]`: string [REQUIRED] - Price ID
- `line_items[0][quantity]`: integer [REQUIRED] - Quantity
- `customer`: string [OPTIONAL] - Existing customer ID
- `customer_email`: string [OPTIONAL] - Pre-fill email

### Refund
- `charge`: string [CONDITIONAL] - Charge ID (ch_) — required if no payment_intent
- `payment_intent`: string [CONDITIONAL] - Payment intent ID (pi_) — required if no charge
- `amount`: integer [OPTIONAL] - Partial refund amount in cents (default: full refund)
- `reason`: string [OPTIONAL] - duplicate, fraudulent, requested_by_customer
- `metadata`: object [OPTIONAL] - Key-value pairs

### Coupon
- `percent_off`: number [CONDITIONAL] - Percentage discount (1-100)
- `amount_off`: integer [CONDITIONAL] - Fixed amount discount in cents
- `currency`: string [REQUIRED with amount_off] - Currency
- `duration`: string [REQUIRED] - forever, once, repeating
- `duration_in_months`: integer [REQUIRED if repeating] - Number of months
- `name`: string [OPTIONAL] - Display name
- `max_redemptions`: integer [OPTIONAL] - Max times coupon can be redeemed

### Payout
- `amount`: integer [REQUIRED] - Amount in cents
- `currency`: string [REQUIRED] - Three-letter ISO code
- `description`: string [OPTIONAL] - Description
- `destination`: string [OPTIONAL] - Bank account or card ID
- `method`: string [OPTIONAL] - standard or instant

### Webhook Endpoint
- `url`: string [REQUIRED] - Endpoint URL (must be HTTPS)
- `enabled_events`: array [REQUIRED] - Events to listen for (e.g., ["payment_intent.succeeded", "customer.created"])
- `description`: string [OPTIONAL] - Description

## Example Requests

**Create Customer:**
```
email=jane@example.com&name=Jane+Doe&metadata[company]=Acme+Inc
```

**Create Payment Intent ($50 USD):**
```
amount=5000&currency=usd&customer=cus_abc123&automatic_payment_methods[enabled]=true
```

**Create Subscription (monthly):**
```
customer=cus_abc123&items[0][price]=price_xyz789&trial_period_days=14
```

**Create Product + Price:**
```
# Product
name=Pro+Plan&description=Professional+tier+access

# Price (recurring monthly $29)
product=prod_abc123&unit_amount=2900&currency=usd&recurring[interval]=month
```

**Create Checkout Session:**
```
mode=payment&success_url=https://example.com/success&line_items[0][price]=price_xyz789&line_items[0][quantity]=1
```

**Issue Partial Refund ($25 of a $50 charge):**
```
payment_intent=pi_abc123&amount=2500&reason=requested_by_customer
```

**Create Coupon (20% off forever):**
```
percent_off=20&duration=forever&name=LAUNCH20
```

**Create Payout:**
```
amount=10000&currency=usd&method=standard
```

**Create Webhook Endpoint:**
```
url=https://myapp.com/stripe-webhooks&enabled_events[]=payment_intent.succeeded&enabled_events[]=customer.created&enabled_events[]=invoice.paid
```

## Response

**get_webhook_endpoints response:**
- `data`: array
- `has_more`: boolean — True if this list has another page of items after this one that can be fetched.
- `object`: string — String representing the object's type. Objects of the same type share the same value. Always has the
- `url`: string — The URL where this list can be accessed.

## Error Responses

Stripe returns errors as JSON with `type`, `code`, and `message` fields inside an `error` object.

| Status | Error Type | Meaning |
|--------|-----------|---------|
| 400 | `invalid_request_error` | Missing required parameter, invalid value, or malformed request |
| 401 | `authentication_error` | Invalid API key or expired token |
| 402 | `card_error` | Card declined, insufficient funds, or card-specific failure (code: `card_declined`, `insufficient_funds`, `expired_card`) |
| 403 | `invalid_request_error` | Restricted API key lacks permission for this endpoint |
| 404 | `invalid_request_error` | Resource not found (invalid ID format or deleted object) |
| 409 | `idempotency_error` | Idempotency key reused with different parameters |
| 429 | `rate_limit_error` | Too many requests — retry with exponential backoff |
| 500 | `api_error` | Stripe server error — retry is safe |
