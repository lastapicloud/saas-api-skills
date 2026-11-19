---
name: bloomreach-engagement
description: 'Manage customers, campaigns, and catalogs via Bloomreach. Use when the
  user mentions bloomreach, engagement, campaign, customer, catalog, recommendation.

  '
version: 1.0.0
skill_type: external
base_url_env: BLOOMREACH_BASE_URL
auth_env_var: BLOOMREACH_API_KEY
auth_type: bearer
triggers:
  - bloomreach
  - engagement
  - campaign
  - customer
  - catalog
  - recommendation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BLOOMREACH_BASE_URL and BLOOMREACH_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Bloomreach-Engagement

Manage customers, campaigns, and catalogs via Bloomreach. Use when the user mentions bloomreach, engagement, campaign, customer, catalog, recommendation.


## API Endpoints

- **POST** `/track/v2/projects/{projectId}/customers/events` - Track customer event
- **POST** `/track/v2/projects/{projectId}/customers` - Update customer properties
- **GET** `/data/v2/projects/{projectId}/customers/export` - Export customers
- **POST** `/email/v2/projects/{projectId}/campaigns` - Create email campaign
- **GET** `/data/v2/projects/{projectId}/catalogs` - List catalogs
- **POST** `/data/v2/projects/{projectId}/catalogs/{catalogId}/items` - Create catalog item
- **GET** `/analytics/v2/projects/{projectId}/funnels` - Get funnel analytics
- **GET** `/recommendations/v2/projects/{projectId}/models` - List recommendation models

## Actions

- create: Track customer event (POST /track/v2/projects/{projectId}/customers/events)
- update_customer_properties: Update customer properties (POST /track/v2/projects/{projectId}/customers)
- list: Export customers (GET /data/v2/projects/{projectId}/customers/export)
- create_email_campaign: Create email campaign (POST /email/v2/projects/{projectId}/campaigns)
- list_catalogs: List catalogs (GET /data/v2/projects/{projectId}/catalogs)
- create_catalog_item: Create catalog item (POST /data/v2/projects/{projectId}/catalogs/{catalogId}/items)
- get_funnel_analytics: Get funnel analytics (GET /analytics/v2/projects/{projectId}/funnels)
- list_recommendation_models: List recommendation models (GET /recommendations/v2/projects/{projectId}/models)

## Fields

- `customer_ids`: object [REQUIRED] (customer identifiers) — Customer Ids configuration
- `event_type`: string [REQUIRED for track_event] — Event resource type
- `properties`: object [OPTIONAL] — Properties configuration

## Example Request Bodies

**Track Customer Event:**
```json
{"customer_ids": {"registered": "user-12345"}, "event_type": "purchase", "properties": {"item_id": "SKU-9876", "amount": 49.99}}
```

**Create Email Campaign:**
```json
{"name": "Summer Sale 2026", "subject": "Save 30% this weekend!", "sender_email": "marketing@example.com"}
```

## Response

**Event object:**
- `id`: string — Unique event identifier
- `name`: string — Event name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
