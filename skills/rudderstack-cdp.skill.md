---
name: rudderstack-cdp
description: Customer data platform via RudderStack. Use when the user mentions rudderstack, CDP, customer data, event tracking, data pipeline, segment alternative.
version: 1.0.0
skill_type: external
base_url_env: RUDDERSTACK_BASE_URL
auth_env_var: RUDDERSTACK_WRITE_KEY
auth_type: bearer
triggers:
  - rudderstack
  - CDP
  - customer data
  - event tracking
  - data pipeline
  - segment alternative
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://www.rudderstack.com/docs/api/
---

# Rudderstack-CDP

Customer data platform via RudderStack. Use when the user mentions rudderstack, CDP, customer data, event tracking, data pipeline, segment alternative.

## API Endpoints

- **POST** `/v1/track` - Track an event
- **POST** `/v1/identify` - Identify a user
- **POST** `/v1/page` - Record a page view
- **POST** `/v1/screen` - Record screen view
- **POST** `/v1/alias` - Alias user identity
- **POST** `/v1/group` - Group users
- **GET** `/v1/users` - List users
- **GET** `/v1/events` - List events
- **GET** `/v1/connections` - List destinations
- **GET** `/v1/sources` - List sources

## Actions

- track: Track an event (POST /v1/track)
- identify: Identify a user (POST /v1/identify)
- page: Record page view (POST /v1/page)
- screen: Record screen view (POST /v1/screen)
- alias: Alias user identity (POST /v1/alias)
- group: Group users (POST /v1/group)
- list_users: List users (GET /v1/users)
- list_events: List events (GET /v1/events)
- list_connections: List destinations (GET /v1/connections)
- list_sources: List sources (GET /v1/sources)

## Fields

- `event`: string [REQUIRED for track] - Event name
- `userId`: string [REQUIRED for track] - User ID
- `properties`: object [OPTIONAL] - Event properties
- `traits`: object [OPTIONAL for identify] - User traits
- `name`: string [REQUIRED for page] - Page name
- `category`: string [OPTIONAL] - Page category

## Example Request Bodies

**Track Event:**
```json
{"event": "Product Clicked", "userId": "user123", "properties": {"productId": "prod_123", "price": 29.99}}
```

**Identify User:**
```json
{"userId": "user123", "traits": {"email": "user@example.com", "name": "John Doe"}}
```

**Page View:**
```json
{"userId": "user123", "name": "Home", "category": "Navigation"}
```
