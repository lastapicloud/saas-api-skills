---
name: customerio-engagement
description: Manage Customer.io customers, segments, and campaigns. Use when the user
  mentions customer.io, customerio, customer, segment, campaign, engagement.
version: 1.0.0
skill_type: external
base_url_env: CUSTOMERIO_BASE_URL
auth_env_var: CUSTOMERIO_API_KEY
auth_type: bearer
triggers:
  - customer.io
  - customerio
  - customer
  - segment
  - campaign
  - engagement
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CUSTOMERIO_BASE_URL and CUSTOMERIO_API_KEY environment variables.
---

# Customerio-Engagement

Manage Customer.io customers, segments, and campaigns. Use when the user mentions customer.io, customerio, customer, segment, campaign, engagement.

## API Endpoints

- **PUT** `/api/v1/customers/{customerId}` - Create/update a customer
- **DELETE** `/api/v1/customers/{customerId}` - Delete a customer
- **POST** `/api/v1/customers/{customerId}/events` - Track an event
- **GET** `/v1/customers/{customerId}/attributes` - Get customer attributes
- **GET** `/v1/segments` - List segments
- **GET** `/v1/segments/{segmentId}/membership` - Get segment membership
- **GET** `/v1/campaigns` - List campaigns
- **GET** `/v1/campaigns/{campaignId}` - Get a campaign
- **GET** `/v1/newsletters` - List newsletters
- **POST** `/api/v1/send/email` - Send a transactional email

## Actions

- update: Create/update a customer (PUT /api/v1/customers/{customerId})
- delete: Delete a customer (DELETE /api/v1/customers/{customerId})
- create: Track an event (POST /api/v1/customers/{customerId}/events)
- list: Get customer attributes (GET /v1/customers/{customerId}/attributes)
- list_segments: List segments (GET /v1/segments)
- list_membership: Get segment membership (GET /v1/segments/{segmentId}/membership)
- list_campaigns: List campaigns (GET /v1/campaigns)
- get_by_id: Get a campaign (GET /v1/campaigns/{campaignId})
- list_newsletters: List newsletters (GET /v1/newsletters)
- create_email: Send a transactional email (POST /api/v1/send/email)

## Fields

- `email`: string [REQUIRED for create customer]
- `name`: string [REQUIRED for track event]
- `data`: object [OPTIONAL for events]
- `to`: string [REQUIRED for send email]
- `transactional_message_id`: string [REQUIRED for send email]
- `message_data`: object [OPTIONAL for send email]

## Example Request Bodies

**Track Event:**
```json
{"name": "purchase_completed", "data": {"product": "Pro Plan", "amount": 99.00}}
```

**Send Transactional Email:**
```json
{"to": "user@example.com", "transactional_message_id": "tmpl_abc123", "message_data": {"first_name": "Jane"}}
