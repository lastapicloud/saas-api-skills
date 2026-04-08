---
name: gorgias-support
description: Manage tickets and customers via Gorgias. Use when the user mentions
  gorgias, support, ticket, customer, helpdesk, ecommerce support.
version: 1.0.0
skill_type: external
base_url_env: GORGIAS_BASE_URL
auth_env_var: GORGIAS_API_TOKEN
auth_type: bearer
triggers:
  - gorgias
  - support
  - ticket
  - customer
  - helpdesk
  - ecommerce support
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GORGIAS_BASE_URL and GORGIAS_API_TOKEN environment variables.
---

# Gorgias-Support

Manage tickets and customers via Gorgias. Use when the user mentions gorgias, support, ticket, customer, helpdesk, ecommerce support.

## API Endpoints

- **GET** `/api/tickets` - List tickets
- **POST** `/api/tickets` - Create ticket
- **GET** `/api/tickets/{id}` - Get ticket
- **PUT** `/api/tickets/{id}` - Update ticket
- **DELETE** `/api/tickets/{id}` - Delete ticket
- **GET** `/api/customers` - List customers
- **POST** `/api/customers` - Create customer
- **POST** `/api/tickets/{id}/messages` - Add message to ticket

## Actions

- list: List tickets (GET /api/tickets)
- create: Create ticket (POST /api/tickets)
- get_by_id: Get ticket (GET /api/tickets/{id})
- update: Update ticket (PUT /api/tickets/{id})
- delete: Delete ticket (DELETE /api/tickets/{id})
- list_customers: List customers (GET /api/customers)
- create_customers: Create customer (POST /api/customers)
- create_messages: Add message to ticket (POST /api/tickets/{id}/messages)

## Fields

- `subject`: string [OPTIONAL]
- `customer`: object [REQUIRED for create] (email)
- `channel`: string [REQUIRED for create]
- `body_text`: string [OPTIONAL]

## Example Request Bodies

**Create Ticket:**
```json
{"subject": "Order not delivered", "customer": {"email": "customer@example.com"}, "channel": "email", "body_text": "I have not received my order #12345."}
```

**Add Message to Ticket:**
```json
{"channel": "email", "body_text": "We are looking into your order and will update you shortly.", "via": "helpdesk"}
```
