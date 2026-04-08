---
name: iterable-marketing
description: Manage Iterable users, campaigns, and events. Use when the user mentions
  iterable, email marketing, campaign, user, event, workflow.
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
- create_track: Track an event (POST /api/events/track)
- list: List campaigns (GET /api/campaigns)
- create_target: Send a targeted email (POST /api/email/target)
- list_lists: List all lists (GET /api/lists)
- create_subscribe: Subscribe users to list (POST /api/lists/subscribe)
- list_workflows: List workflows (GET /api/workflows)
- list_channels: List channels (GET /api/channels)

## Fields

- `email`: string [REQUIRED]
- `dataFields`: object [OPTIONAL for user]
- `eventName`: string [REQUIRED for track]
- `campaignId`: integer [REQUIRED for send]
- `recipientEmail`: string [REQUIRED for send]
- `listId`: integer [REQUIRED for subscribe]

## Example Request Bodies

**Create/Update User:**
```json
{"email": "user@example.com", "dataFields": {"firstName": "Jane", "signupDate": "2024-01-15"}}
```

**Track Event:**
```json
{"email": "user@example.com", "eventName": "purchase_completed", "dataFields": {"amount": 49.99}}
```
