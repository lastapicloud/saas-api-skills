---
name: iterable-marketing
description: 'Manage Iterable users, campaigns, and events. Use when the user mentions
  iterable, email marketing, campaign, user, event, workflow.

  '
version: 1.0.0
skill_type: external
base_url_env: ITERABLE_BASE_URL
auth_env_var: ITERABLE_API_KEY
auth_type: header
triggers:
  - iterable
  - email marketing
  - campaign
  - user
  - event
  - workflow
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ITERABLE_BASE_URL and ITERABLE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Iterable-Marketing

Manage Iterable users, campaigns, and events. Use when the user mentions iterable, email marketing, campaign, user, event, workflow.


## API Endpoints

- **POST** `/api/users/update` - Create/update a user
- **GET** `/api/users/{email}` - Get a user
- **DELETE** `/api/users/{email}` - Delete a user
- **POST** `/api/events/track` - Track an event
- **GET** `/api/campaigns` - List campaigns
- **POST** `/api/email/target` - Send a targeted email
- **GET** `/api/lists` - List all lists
- **POST** `/api/lists/subscribe` - Subscribe users to list
- **GET** `/api/workflows` - List workflows
- **GET** `/api/channels` - List channels

## Actions

- create: Create/update a user (POST /api/users/update)
- get_by_id: Get a user (GET /api/users/{email})
- delete: Delete a user (DELETE /api/users/{email})
- create_track_event: Track an event (POST /api/events/track)
- list: List campaigns (GET /api/campaigns)
- send_targeted_email: Send a targeted email (POST /api/email/target)
- lists: List all lists (GET /api/lists)
- create_subscribe_users_list: Subscribe users to list (POST /api/lists/subscribe)
- list_workflows: List workflows (GET /api/workflows)
- list_channels: List channels (GET /api/channels)

## Fields

- `email`: string [REQUIRED] — Email address
- `dataFields`: object [OPTIONAL for user] — Datafields configuration
- `eventName`: string [REQUIRED for track] — Event display name
- `campaignId`: integer [REQUIRED for send] — Campaign unique identifier
- `recipientEmail`: string [REQUIRED for send] — Recipient email address
- `listId`: integer [REQUIRED for subscribe] — List unique identifier

## Example Request Bodies

**Create/Update User:**
```json
{"email": "user@example.com", "dataFields": {"firstName": "Jane", "signupDate": "2024-01-15"}}
```

**Track Event:**
```json
{"email": "user@example.com", "eventName": "purchase_completed", "dataFields": {"amount": 49.99}}
```

## Response

**User object:**
- `id`: string — Unique user identifier
- `name`: string — User name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "campaignId": 1,
  "recipientEmail": "example_recipientEmail",
  "listId": 1
}
```


**Required fields reference:**
```json
{
  "campaignId": 1,
  "recipientEmail": "example_recipientEmail",
  "listId": 1
}
```

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
