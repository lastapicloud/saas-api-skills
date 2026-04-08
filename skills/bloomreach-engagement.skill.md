---
name: bloomreach-engagement
description: Manage customers, campaigns, and catalogs via Bloomreach. Use when the
  user mentions bloomreach, engagement, campaign, customer, catalog, recommendation.
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
- create_customers: Update customer properties (POST /track/v2/projects/{projectId}/customers)
- list: Export customers (GET /data/v2/projects/{projectId}/customers/export)
- create_campaigns: Create email campaign (POST /email/v2/projects/{projectId}/campaigns)
- list_catalogs: List catalogs (GET /data/v2/projects/{projectId}/catalogs)
- create_items: Create catalog item (POST /data/v2/projects/{projectId}/catalogs/{catalogId}/items)
- list_funnels: Get funnel analytics (GET /analytics/v2/projects/{projectId}/funnels)
- list_models: List recommendation models (GET /recommendations/v2/projects/{projectId}/models)

## Fields

- `customer_ids`: object [REQUIRED] (customer identifiers)
- `event_type`: string [REQUIRED for track_event]
- `properties`: object [OPTIONAL]

## Example Request Bodies

**Track Customer Event:**
```json
{"customer_ids": {"registered": "user-12345"}, "event_type": "purchase", "properties": {"item_id": "SKU-9876", "amount": 49.99}}
```

**Create Email Campaign:**
```json
{"name": "Summer Sale 2026", "subject": "Save 30% this weekend!", "sender_email": "marketing@example.com"}
```
