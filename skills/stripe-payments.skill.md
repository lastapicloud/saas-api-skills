---
name: stripe-payments
description: "Complete Stripe payment processing \u2014 customers, payment intents,\
  \ subscriptions, invoices, products, prices, refunds, disputes, payouts, checkout,\
  \ coupons, webhooks, and balance. Use when the user mentions stripe, payment, charge,\
  \ invoice, subscription, customer, refund, billing, checkout, payout, dispute, product,\
  \ price, coupon. (API 2022-11-15)"
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
compatibility: Requires STRIPE_BASE_URL and STRIPE_API_KEY environment variables.
---

# Stripe-Payments

Complete Stripe payment processing — customers, payment intents, subscriptions, invoices, products, prices, refunds, disputes, payouts, checkout, coupons, webhooks, and balance. Use when the user mentions stripe, payment, charge, invoice, subscription, customer, refund, billing, checkout, payout, dispute, product, price, coupon. (API 2022-11-15)

## API Endpoints

- **GET** `/v1/products/search` - <p>Search for products you’ve previously created using Stripe’s <a href="/docs/search#search-query-language">Search
- **POST** `/v1/products` - <p>Creates a new product object.</p>
- **DELETE** `/v1/products/{id}` - <p>Delete a product. Deleting a product is only possible if it has no prices associated with it. Additionally, deleting
- **GET** `/v1/coupons` - <p>Returns a list of your coupons.</p>
- **POST** `/v1/coupons` - <p>You can create coupons easily via the <a href="https://dashboard.stripe.com/coupons">coupon management</a> page of
- **DELETE** `/v1/coupons/{coupon}` - <p>You can delete coupons via the <a href="https://dashboard.stripe.com/coupons">coupon management</a> page of the
- **GET** `/v1/invoiceitems` - <p>Returns a list of your invoice items. Invoice items are returned sorted by creation date, with the most recently
- **POST** `/v1/invoiceitems` - <p>Creates an item to be added to a draft invoice (up to 250 items per invoice). If no invoice is specified, the item
- **DELETE** `/v1/invoiceitems/{invoiceitem}` - <p>Deletes an invoice item, removing it from an invoice. Deleting invoice items is only possible when they’re not
- **GET** `/v1/plans` - <p>Returns a list of your plans.</p>
- **POST** `/v1/plans` - <p>You can now model subscriptions more flexibly using the <a href="#prices">Prices API</a>. It replaces the Plans API
- **DELETE** `/v1/plans/{plan}` - <p>Deleting plans means new subscribers can’t be added. Existing subscribers aren’t affected.</p>
- **GET** `/v1/subscriptions/search` - <p>Search for subscriptions you’ve previously created using Stripe’s <a
- **POST** `/v1/subscriptions` - <p>Creates a new subscription on an existing customer. Each customer can have up to 500 active or scheduled
- **DELETE** `/v1/subscriptions/{subscription_exposed_id}` - <p>Cancels a customer’s subscription immediately. The customer will not be charged again for the

## Actions

- search: <p>Search for products you’ve previously created using Stripe’s <a href="/docs/s (GET /v1/products/search)
- create: <p>Creates a new product object.</p> (POST /v1/products)
- delete: <p>Delete a product. Deleting a product is only possible if it has no prices ass (DELETE /v1/products/{id})
- list: <p>Returns a list of your coupons.</p> (GET /v1/coupons)
- create_coupons: <p>You can create coupons easily via the <a href="https://dashboard.stripe.com/c (POST /v1/coupons)
- delete_coupons: <p>You can delete coupons via the <a href="https://dashboard.stripe.com/coupons" (DELETE /v1/coupons/{coupon})
- list_invoiceitems: <p>Returns a list of your invoice items. Invoice items are returned sorted by cr (GET /v1/invoiceitems)
- create_invoiceitems: <p>Creates an item to be added to a draft invoice (up to 250 items per invoice). (POST /v1/invoiceitems)
- delete_invoiceitems: <p>Deletes an invoice item, removing it from an invoice. Deleting invoice items (DELETE /v1/invoiceitems/{invoiceitem})
- list_plans: <p>Returns a list of your plans.</p> (GET /v1/plans)
- create_plans: <p>You can now model subscriptions more flexibly using the <a href="#prices">Pri (POST /v1/plans)
- delete_plans: <p>Deleting plans means new subscribers can’t be added. Existing subscribers are (DELETE /v1/plans/{plan})
- search_subscriptions: <p>Search for subscriptions you’ve previously created using Stripe’s <a (GET /v1/subscriptions/search)
- create_subscriptions: <p>Creates a new subscription on an existing customer. Each customer can have up (POST /v1/subscriptions)
- delete_subscriptions: <p>Cancels a customer’s subscription immediately. The customer will not be charg (DELETE /v1/subscriptions/{subscription_exposed_id})

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
