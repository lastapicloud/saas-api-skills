---
name: marketo-marketing
description: 'Manage Marketo leads, campaigns, and programs. Use when the user mentions
  marketo, lead, campaign, program, marketing automation.

  '
version: 1.0.0
skill_type: external
base_url_env: MARKETO_BASE_URL
auth_env_var: MARKETO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - marketo
  - lead
  - campaign
  - program
  - marketing automation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MARKETO_BASE_URL and MARKETO_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Marketo-Marketing

Manage Marketo leads, campaigns, and programs. Use when the user mentions marketo, lead, campaign, program, marketing automation.


## API Endpoints

- **GET** `/rest/v1/leads.json` - List leads
- **GET** `/rest/v1/lead/{leadId}.json` - Get a lead
- **POST** `/rest/v1/leads.json` - Create/update leads
- **POST** `/rest/v1/leads/delete.json` - Delete leads
- **GET** `/rest/v1/campaigns.json` - List campaigns
- **POST** `/rest/v1/campaigns/{campaignId}/trigger.json` - Trigger a campaign
- **GET** `/rest/asset/v1/programs.json` - List programs
- **GET** `/rest/v1/lists.json` - List static lists
- **POST** `/rest/v1/lists/{listId}/leads.json` - Add leads to list
- **GET** `/rest/v1/activities/types.json` - List activity types

## Actions

- list: List leads (GET /rest/v1/leads.json)
- get_lead: Get a lead (GET /rest/v1/lead/{leadId}.json)
- create: Create/update leads (POST /rest/v1/leads.json)
- delete_leads: Delete leads (POST /rest/v1/leads/delete.json)
- list_campaigns: List campaigns (GET /rest/v1/campaigns.json)
- trigger_campaign: Trigger a campaign (POST /rest/v1/campaigns/{campaignId}/trigger.json)
- list_programs: List programs (GET /rest/asset/v1/programs.json)
- list_static_lists: List static lists (GET /rest/v1/lists.json)
- add_leads_list: Add leads to list (POST /rest/v1/lists/{listId}/leads.json)
- list_activity_types: List activity types (GET /rest/v1/activities/types.json)

## Fields

- `input`: array [REQUIRED for create/delete] with lead objects — List of input
- `action`: string [OPTIONAL] ("createOnly", "updateOnly", "createOrUpdate") — Action
- `lookupField`: string [OPTIONAL] ("email" or field name) — Lookupfield
- `id`: integer [REQUIRED in lead objects for update] — Unique identifier
- `email`: string [REQUIRED for create] — Email address

## Example Request Bodies

**Create/Update Leads:**
```json
{"action": "createOrUpdate", "lookupField": "email", "input": [{"email": "lead@example.com", "firstName": "Jane", "lastName": "Smith"}]}
```

**Trigger Campaign:**
```json
{"input": [{"leadId": 12345}]}
```

## Response

**Leads.Json object:**
- `id`: string — Unique leads.json identifier
- `name`: string — Leads.Json name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

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
