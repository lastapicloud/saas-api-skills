---
name: drip-marketing
description: Manage subscribers and campaigns via Drip. Use when the user mentions
  drip, email marketing, subscriber, campaign, automation, ecommerce marketing.
version: 1.0.0
skill_type: external
base_url_env: DRIP_BASE_URL
auth_env_var: DRIP_API_TOKEN
auth_type: bearer
triggers:
  - drip
  - email marketing
  - subscriber
  - campaign
  - automation
  - ecommerce marketing
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DRIP_BASE_URL and DRIP_API_TOKEN environment variables.
---

# Drip-Marketing

Manage subscribers and campaigns via Drip. Use when the user mentions drip, email marketing, subscriber, campaign, automation, ecommerce marketing.

## API Endpoints

- **GET** `/v2/{account_id}/subscribers` - List subscribers
- **POST** `/v2/{account_id}/subscribers` - Create or update a subscriber
- **GET** `/v2/{account_id}/subscribers/{subscriber_id}` - Get subscriber by ID
- **DELETE** `/v2/{account_id}/subscribers/{subscriber_id}` - Delete a subscriber
- **POST** `/v2/{account_id}/events` - Track an event
- **GET** `/v2/{account_id}/campaigns` - List campaigns
- **POST** `/v2/{account_id}/campaigns/{campaign_id}/activate` - Activate a campaign
- **GET** `/v2/{account_id}/workflows` - List workflows

## Actions

- list: List subscribers (GET /v2/{account_id}/subscribers)
- create: Create or update a subscriber (POST /v2/{account_id}/subscribers)
- get_by_id: Get subscriber by ID (GET /v2/{account_id}/subscribers/{subscriber_id})
- delete: Delete a subscriber (DELETE /v2/{account_id}/subscribers/{subscriber_id})
- create_events: Track an event (POST /v2/{account_id}/events)
- list_campaigns: List campaigns (GET /v2/{account_id}/campaigns)
- create_activate: Activate a campaign (POST /v2/{account_id}/campaigns/{campaign_id}/activate)
- list_workflows: List workflows (GET /v2/{account_id}/workflows)

## Fields

- `email`: string [REQUIRED for create]
- `action`: string [REQUIRED for track_event]
- `properties`: object [OPTIONAL]

## Example Request Bodies

**Create Subscriber:**
```json
{"subscribers": [{"email": "newuser@example.com", "tags": ["trial"], "custom_fields": {"plan": "starter"}}]}
```

**Track Event:**
```json
{"events": [{"email": "newuser@example.com", "action": "Completed onboarding", "properties": {"steps_completed": 5}}]}
```
