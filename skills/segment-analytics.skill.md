---
name: segment-analytics
description: Track events, identify users, and manage sources in Segment. Use when
  the user mentions segment, analytics, track, identify, CDP, customer data, event.
version: 1.0.0
skill_type: external
base_url_env: SEGMENT_BASE_URL
auth_env_var: SEGMENT_WRITE_KEY
auth_type: basic
triggers:
  - segment
  - analytics
  - track
  - identify
  - CDP
  - customer data
  - event
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SEGMENT_BASE_URL and SEGMENT_WRITE_KEY environment variables.
---

# Segment-Analytics

Track events, identify users, and manage sources in Segment. Use when the user mentions segment, analytics, track, identify, CDP, customer data, event.

## API Endpoints

- **POST** `/identify` - Identify a user (Tracking API)
- **POST** `/track` - Track an event (Tracking API)
- **POST** `/page` - Record a page view (Tracking API)
- **POST** `/group` - Associate user with a group (Tracking API)
- **POST** `/alias` - Alias two user identities (Tracking API)
- **POST** `/batch` - Send multiple messages in a batch (Tracking API)
- **GET** `/sources` - List all sources (Public API)
- **POST** `/sources` - Create a source (Public API)
- **GET** `/sources/{sourceId}` - Get a source (Public API)
- **PATCH** `/sources/{sourceId}` - Update a source (Public API)
- **DELETE** `/sources/{sourceId}` - Delete a source (Public API)
- **GET** `/catalog/sources` - List source catalog (Public API)
- **GET** `/destinations` - List destinations (Public API)
- **GET** `/warehouses` - List warehouses (Public API)

## Actions

- create: Identify a user (POST /identify)
- create_track: Track an event (POST /track)
- create_page: Record a page view (POST /page)
- create_group: Associate user with a group (POST /group)
- create_alias: Alias two user identities (POST /alias)
- create_batch: Send multiple messages in a batch (POST /batch)
- list_sources: List all sources (GET /sources)
- create_source: Create a source (POST /sources)
- get_by_id_source: Get a source (GET /sources/{sourceId})
- update_source: Update a source (PATCH /sources/{sourceId})
- delete_source: Delete a source (DELETE /sources/{sourceId})
- list_catalog: List source catalog (GET /catalog/sources)
- list_destinations: List destinations (GET /destinations)
- list_warehouses: List warehouses (GET /warehouses)

## Fields

- `userId`: string [REQUIRED for identify, track, page, group] (user identifier)
- `anonymousId`: string [OPTIONAL, alternative to userId] (anonymous user identifier)
- `event`: string [REQUIRED for track_event] (event name)
- `properties`: object [OPTIONAL for track_event, record_page] (event/page properties)
- `traits`: object [OPTIONAL for identify_user] (user traits like name, email)
- `groupId`: string [REQUIRED for group_user] (group identifier)
- `name`: string [OPTIONAL for record_page] (page name)
- `previousId`: string [REQUIRED for alias_user] (previous user ID)
- `context`: object [OPTIONAL] (context with library, device, OS info)
- `timestamp`: string [OPTIONAL] (ISO 8601 datetime)
- `batch`: array [REQUIRED for batch_send] (array of message objects)

## Example Request Bodies

**Track Event:**
```json
{"userId": "user_123", "event": "Order Completed", "properties": {"revenue": 49.99, "currency": "USD", "orderId": "order_456"}}
```

**Identify User:**
```json
{"userId": "user_123", "traits": {"name": "Jane Doe", "email": "jane@example.com", "plan": "premium"}}
```

**Batch Send:**
```json
{"batch": [{"type": "identify", "userId": "user_123", "traits": {"name": "Jane"}}, {"type": "track", "userId": "user_123", "event": "Login"}]}
```
