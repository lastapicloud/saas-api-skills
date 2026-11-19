---
name: segment-analytics
description: 'Track events, identify users, and manage sources in Segment. Use when
  the user mentions segment, analytics, track, identify, CDP, customer data, event.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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

## Actions

- create: Identify a user (Tracking API) (POST /identify)
- create_track_event_tracking_api: Track an event (Tracking API) (POST /track)
- create_record_page_view_tracking: Record a page view (Tracking API) (POST /page)
- create_associate_user_group_tracking: Associate user with a group (Tracking API) (POST /group)
- create_alias_two_user_identities: Alias two user identities (Tracking API) (POST /alias)
- send_multiple_messages_batch: Send multiple messages in a batch (Tracking API) (POST /batch)

## Fields

- `userId`: string [REQUIRED for identify, track, page, group] (user identifier) — User unique identifier
- `anonymousId`: string [OPTIONAL, alternative to userId] (anonymous user identifier) — Anonymous unique identifier
- `event`: string [REQUIRED for track_event] (event name) — Event
- `properties`: object [OPTIONAL for track_event, record_page] (event/page properties) — Properties configuration
- `traits`: object [OPTIONAL for identify_user] (user traits like name, email) — Traits configuration
- `groupId`: string [REQUIRED for group_user] (group identifier) — Group unique identifier
- `name`: string [OPTIONAL for record_page] (page name) — Display name
- `previousId`: string [REQUIRED for alias_user] (previous user ID) — Previous unique identifier
- `context`: object [OPTIONAL] (context with library, device, OS info) — Con text content
- `timestamp`: string [OPTIONAL] (ISO 8601 datetime) — Timestamp
- `batch`: array [REQUIRED for batch_send] (array of message objects) — List of batch

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

## Response

**Identify object:**
- `id`: string — Unique identify identifier
- `name`: string — Identify name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "groupId": "example_groupId",
  "previousId": "example_previousId"
}
```


**Required fields reference:**
```json
{
  "groupId": "example_groupId",
  "previousId": "example_previousId"
}
```

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
