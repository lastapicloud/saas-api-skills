---
name: klaviyo-marketing-campaigns
description: Manage campaigns and flows via Klaviyo Marketing. Use when the user mentions
  klaviyo marketing, campaign, flow, template, email marketing.
version: 1.0.0
skill_type: external
base_url_env: KLAVIYO_BASE_URL
auth_env_var: KLAVIYO_API_KEY
auth_type: header
triggers:
  - klaviyo marketing
  - campaign
  - flow
  - template
  - email marketing
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KLAVIYO_BASE_URL and KLAVIYO_API_KEY environment variables.
---

# Klaviyo-Marketing-Campaigns

Manage campaigns and flows via Klaviyo Marketing. Use when the user mentions klaviyo marketing, campaign, flow, template, email marketing.

## API Endpoints

- **GET** `/api/campaigns/` - List campaigns
- **POST** `/api/campaigns/` - Create campaign
- **GET** `/api/campaigns/{id}/` - Get campaign
- **PATCH** `/api/campaigns/{id}/` - Update campaign
- **DELETE** `/api/campaigns/{id}/` - Delete campaign
- **GET** `/api/flows/` - List flows
- **GET** `/api/templates/` - List templates
- **POST** `/api/campaign-send-jobs/` - Send campaign

## Actions

- list: List campaigns (GET /api/campaigns/)
- create: Create campaign (POST /api/campaigns/)
- get_by_id: Get campaign (GET /api/campaigns/{id}/)
- update: Update campaign (PATCH /api/campaigns/{id}/)
- delete: Delete campaign (DELETE /api/campaigns/{id}/)
- list_flows: List flows (GET /api/flows/)
- list_templates: List templates (GET /api/templates/)
- create_campaign_send_jobs: Send campaign (POST /api/campaign-send-jobs/)

## Fields

- `type`: string [REQUIRED] (campaign)
- `attributes`: object [REQUIRED for create]

## Example Request Bodies

**Create Campaign:**
```json
{"data": {"type": "campaign", "attributes": {"name": "Spring Sale 2024", "channel": "email", "audiences": {"included": ["list-abc123"]}}}}
```

**Send Campaign:**
```json
{"data": {"type": "campaign-send-job", "attributes": {"campaign_id": "camp-xyz789"}}}
```
