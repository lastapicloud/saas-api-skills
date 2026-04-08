---
name: heap-analytics
description: Track events, manage users, and query analytics data via Heap. Use when
  the user mentions heap, analytics, event, user, track, session.
version: 1.0.0
skill_type: external
base_url_env: HEAP_BASE_URL
auth_env_var: HEAP_API_KEY
auth_type: header
triggers:
  - heap
  - analytics
  - event
  - user
  - track
  - session
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HEAP_BASE_URL and HEAP_API_KEY environment variables.
---

# Heap-Analytics

Track events, manage users, and query analytics data via Heap. Use when the user mentions heap, analytics, event, user, track, session.

## API Endpoints

- **POST** `/api/track` - Track a custom event for a user
- **POST** `/api/add_user_properties` - Add or update properties on a user
- **POST** `/api/identify` - Associate an anonymous user with an identity
- **POST** `/api/delete_user` - Delete a user and their data
- **GET** `/api/v1/event_definitions` - List all tracked event definitions
- **GET** `/api/v1/user_properties` - List all user property definitions
- **POST** `/api/integrations/webhooks` - Create a webhook integration
- **GET** `/api/integrations/webhooks` - List webhook integrations
- **GET** `/v1/shopping/flight-dates` - Find the cheapest flight dates from an origin to a destination.

## Actions

- create: Track a custom event for a user (POST /api/track)
- create_add_user_properties: Add or update properties on a user (POST /api/add_user_properties)
- create_identify: Associate an anonymous user with an identity (POST /api/identify)
- create_delete_user: Delete a user and their data (POST /api/delete_user)
- list: List all tracked event definitions (GET /api/v1/event_definitions)
- list_user_properties: List all user property definitions (GET /api/v1/user_properties)
- create_webhooks: Create a webhook integration (POST /api/integrations/webhooks)
- list_webhooks: List webhook integrations (GET /api/integrations/webhooks)
- list_flight_dates: Find the cheapest flight dates from an origin to a destination. (GET /v1/shopping/flight-dates)

## Fields

- `app_id`: string [REQUIRED for track] (Heap app ID)
- `identity`: string [REQUIRED for track, identify] (user identity/email)
- `event`: string [REQUIRED for track] (event name)
- `properties`: object [OPTIONAL for track] (key-value event properties)
- `user_id`: string [REQUIRED for delete_user] (user ID to delete)

## Example Request Bodies

**Track Event:**
```json
{"app_id": "1234567890", "identity": "user@example.com", "event": "Purchase Completed", "properties": {"amount": 49.99, "currency": "USD"}}
```

**Identify User:**
```json
{"app_id": "1234567890", "identity": "user@example.com", "properties": {"plan": "premium", "signup_date": "2024-01-15"}}
```
