---
name: marketo-marketing
description: Manage Marketo leads, campaigns, and programs. Use when the user mentions
  marketo, lead, campaign, program, marketing automation.
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
- list_lead: Get a lead (GET /rest/v1/lead/{leadId}.json)
- create: Create/update leads (POST /rest/v1/leads.json)
- create_delete_json: Delete leads (POST /rest/v1/leads/delete.json)
- list_campaigns_json: List campaigns (GET /rest/v1/campaigns.json)
- create_trigger_json: Trigger a campaign (POST /rest/v1/campaigns/{campaignId}/trigger.json)
- list_programs_json: List programs (GET /rest/asset/v1/programs.json)
- list_lists_json: List static lists (GET /rest/v1/lists.json)
- create_leads_json: Add leads to list (POST /rest/v1/lists/{listId}/leads.json)
- list_types_json: List activity types (GET /rest/v1/activities/types.json)

## Fields

- `input`: array [REQUIRED for create/delete] with lead objects
- `action`: string [OPTIONAL] ("createOnly", "updateOnly", "createOrUpdate")
- `lookupField`: string [OPTIONAL] ("email" or field name)
- `id`: integer [REQUIRED in lead objects for update]
- `email`: string [REQUIRED for create]

## Example Request Bodies

**Create/Update Leads:**
```json
{"action": "createOrUpdate", "lookupField": "email", "input": [{"email": "lead@example.com", "firstName": "Jane", "lastName": "Smith"}]}
```

**Trigger Campaign:**
```json
{"input": [{"leadId": 12345}]}
```
