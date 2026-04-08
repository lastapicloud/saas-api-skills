---
name: yext-listings
description: Manage business listings and reviews via Yext. Use when the user mentions
  yext, listing, review, location, knowledge graph, local seo.
version: 1.0.0
skill_type: external
base_url_env: YEXT_BASE_URL
auth_env_var: YEXT_API_KEY
auth_type: header
triggers:
  - yext
  - listing
  - review
  - location
  - knowledge graph
  - local seo
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires YEXT_BASE_URL and YEXT_API_KEY environment variables.
---

# Yext-Listings

Manage business listings and reviews via Yext. Use when the user mentions yext, listing, review, location, knowledge graph, local seo.

## API Endpoints

- **GET** `/v2/accounts/{accountId}/locations` - List locations
- **POST** `/v2/accounts/{accountId}/locations` - Create location
- **GET** `/v2/accounts/{accountId}/locations/{locationId}` - Get location
- **PUT** `/v2/accounts/{accountId}/locations/{locationId}` - Update location
- **GET** `/v2/accounts/{accountId}/reviews` - List reviews
- **GET** `/v2/accounts/{accountId}/listings` - List listings
- **GET** `/v2/accounts/{accountId}/analytics/reports` - Get analytics

## Actions

- list: List locations (GET /v2/accounts/{accountId}/locations)
- create: Create location (POST /v2/accounts/{accountId}/locations)
- get_by_id: Get location (GET /v2/accounts/{accountId}/locations/{locationId})
- update: Update location (PUT /v2/accounts/{accountId}/locations/{locationId})
- list_reviews: List reviews (GET /v2/accounts/{accountId}/reviews)
- list_listings: List listings (GET /v2/accounts/{accountId}/listings)
- list_reports: Get analytics (GET /v2/accounts/{accountId}/analytics/reports)

## Fields

- `locationName`: string [REQUIRED for create]
- `address`: object [REQUIRED for create]
- `categoryIds`: array [OPTIONAL]

## Example Request Bodies

**Create Location:**
```json
{"locationName": "Downtown Coffee Shop", "address": {"line1": "123 Main St", "city": "Seattle", "region": "WA", "postalCode": "98101"}, "categoryIds": ["restaurant"]}
```

**Update Location:**
```json
{"locationName": "Downtown Coffee & Tea", "address": {"line1": "123 Main St", "city": "Seattle", "region": "WA", "postalCode": "98101"}}
