---
name: pendo-analytics
description: Track usage and manage guides via Pendo. Use when the user mentions pendo,
  analytics, guide, feature, visitor, usage.
version: 1.0.0
skill_type: external
base_url_env: PENDO_BASE_URL
auth_env_var: PENDO_API_KEY
auth_type: header
triggers:
  - pendo
  - analytics
  - guide
  - feature
  - visitor
  - usage
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PENDO_BASE_URL and PENDO_API_KEY environment variables.
---

# Pendo-Analytics

Track usage and manage guides via Pendo. Use when the user mentions pendo, analytics, guide, feature, visitor, usage.

## API Endpoints

- **POST** `/api/v1/aggregation` - Run aggregation query
- **GET** `/api/v1/feature` - List features
- **GET** `/api/v1/feature/{featureId}` - Get feature
- **GET** `/api/v1/guide` - List guides
- **GET** `/api/v1/guide/{guideId}` - Get guide
- **GET** `/api/v1/visitor/{visitorId}` - Get visitor
- **POST** `/api/v1/metadata/visitor/agent/value` - Update visitor metadata
- **GET** `/api/v1/page` - List pages
- **GET** `/users/search` - Find a User with a query
- **POST** `/users` - Ping to create or update an EndUser and Account in one call
- **PUT** `/users/{id}` - Update a User
- **DELETE** `/users/{id}` - Delete a User
- **GET** `/accounts` - Query accounts
- **PUT** `/accounts/{id}` - Update an Account
- **DELETE** `/accounts/{id}` - Delete an Account

## Actions

- create: Run aggregation query (POST /api/v1/aggregation)
- list: List features (GET /api/v1/feature)
- get_by_id: Get feature (GET /api/v1/feature/{featureId})
- list_guide: List guides (GET /api/v1/guide)
- get_by_id_guide: Get guide (GET /api/v1/guide/{guideId})
- get_by_id_visitor: Get visitor (GET /api/v1/visitor/{visitorId})
- create_value: Update visitor metadata (POST /api/v1/metadata/visitor/agent/value)
- list_page: List pages (GET /api/v1/page)
- search: Find a User with a query (GET /users/search)
- create_users: Ping to create or update an EndUser and Account in one call (POST /users)
- update: Update a User (PUT /users/{id})
- delete: Delete a User (DELETE /users/{id})
- list_accounts: Query accounts (GET /accounts)
- update_accounts: Update an Account (PUT /accounts/{id})
- delete_accounts: Delete an Account (DELETE /accounts/{id})

## Fields

- `pipeline`: array [REQUIRED for aggregate]
- `source`: object [REQUIRED for aggregate]
- `visitorId`: string [REQUIRED for get_visitor]

## Example Request Bodies

**Run Aggregation Query:**
```json
{"response": {"mimeType": "application/json"}, "request": {"pipeline": [{"source": {"events": null}}, {"identified": "visitorId"}, {"dateRange": {"first": "2024-01-01", "last": "2024-03-31"}}], "requestId": "agg-001"}}
```

**Update Visitor Metadata:**
```json
{"visitorId": "visitor-abc123", "values": {"plan": "enterprise", "company": "Acme Corp"}}
```
