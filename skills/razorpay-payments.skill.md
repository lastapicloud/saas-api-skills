---
name: razorpay-payments
description: Manage Razorpay payments, orders, and customers. Use when the user mentions
  razorpay, payment, order, refund, customer.
version: 1.0.0
skill_type: external
base_url_env: RAZORPAY_BASE_URL
auth_env_var: RAZORPAY_KEY_SECRET
auth_user_env: RAZORPAY_KEY_ID
auth_type: basic
triggers:
  - razorpay
  - payment
  - order
  - refund
  - customer
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RAZORPAY_BASE_URL and RAZORPAY_KEY_SECRET environment variables.
---

# Razorpay-Payments

Manage Razorpay payments, orders, and customers. Use when the user mentions razorpay, payment, order, refund, customer.

## API Endpoints

- **GET** `/v1/payments` - List payments
- **GET** `/v1/payments/{paymentId}` - Get a payment
- **POST** `/v1/payments/{paymentId}/capture` - Capture a payment
- **POST** `/v1/payments/{paymentId}/refund` - Refund a payment
- **POST** `/v1/orders` - Create an order
- **GET** `/v1/orders` - List orders
- **GET** `/v1/orders/{orderId}` - Get an order
- **POST** `/v1/customers` - Create a customer
- **GET** `/v1/customers` - List customers
- **GET** `/v1/refunds` - List refunds

## Actions

- list: List payments (GET /v1/payments)
- get_by_id: Get a payment (GET /v1/payments/{paymentId})
- create: Capture a payment (POST /v1/payments/{paymentId}/capture)
- create_refund: Refund a payment (POST /v1/payments/{paymentId}/refund)
- create_orders: Create an order (POST /v1/orders)
- list_orders: List orders (GET /v1/orders)
- get_by_id_orders: Get an order (GET /v1/orders/{orderId})
- create_customers: Create a customer (POST /v1/customers)
- list_customers: List customers (GET /v1/customers)
- list_refunds: List refunds (GET /v1/refunds)

## Fields

- `amount`: integer [REQUIRED] (paise for INR)
- `currency`: string [REQUIRED]
- `receipt`: string [OPTIONAL]
- `name`: string [OPTIONAL for customer]
- `email`: string [OPTIONAL for customer]
- `contact`: string [OPTIONAL for customer]

## Example Request Bodies

**Create Order:**
```json
{"amount": 50000, "currency": "INR", "receipt": "order_rcpt_1"}
```

**Create Customer:**
```json
{"name": "Rahul Sharma", "email": "rahul@example.com", "contact": "+919876543210"}
```
