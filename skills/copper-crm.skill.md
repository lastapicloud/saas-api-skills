---
name: copper-crm
description: 'Manage leads, people, opportunities, and companies in Copper CRM. Use
  when the user mentions copper, copper crm, copper lead, copper opportunity, copper
  people.

  '
version: 1.0.0
skill_type: external
base_url_env: COPPER_BASE_URL
auth_env_var: COPPER_API_TOKEN
auth_type: header
triggers:
  - copper
  - copper crm
  - copper lead
  - copper opportunity
  - copper people
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COPPER_BASE_URL and COPPER_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Copper-Crm

Manage leads, people, opportunities, and companies in Copper CRM. Use when the user mentions copper, copper crm, copper lead, copper opportunity, copper people.


## API Endpoints

- **POST** `/developer_api/v1/leads/search` - Search leads
- **POST** `/developer_api/v1/leads` - Create a lead
- **GET** `/developer_api/v1/leads/{id}` - Get a lead by ID
- **PUT** `/developer_api/v1/leads/{id}` - Update a lead
- **DELETE** `/developer_api/v1/leads/{id}` - Delete a lead
- **POST** `/developer_api/v1/people/search` - Search people
- **POST** `/developer_api/v1/people` - Create a person
- **POST** `/developer_api/v1/opportunities/search` - Search opportunities
- **POST** `/developer_api/v1/opportunities` - Create an opportunity
- **POST** `/developer_api/v1/companies/search` - Search companies

## Actions

- search: Search leads (POST /developer_api/v1/leads/search)
- create: Create a lead (POST /developer_api/v1/leads)
- get_by_id: Get a lead by ID (GET /developer_api/v1/leads/{id})
- update: Update a lead (PUT /developer_api/v1/leads/{id})
- delete: Delete a lead (DELETE /developer_api/v1/leads/{id})
- search_people: Search people (POST /developer_api/v1/people/search)
- create_person: Create a person (POST /developer_api/v1/people)
- search_opportunities: Search opportunities (POST /developer_api/v1/opportunities/search)
- create_opportunity: Create an opportunity (POST /developer_api/v1/opportunities)
- search_companies: Search companies (POST /developer_api/v1/companies/search)

## Fields

- `id`: integer [REQUIRED for get_lead, update_lead, delete_lead] (record ID) — Unique identifier
- `name`: string [REQUIRED for create_lead, create_person, create_opportunity] (name) — Display name
- `email`: object [OPTIONAL] (email with category and address fields) — Email address
- `phone_numbers`: array [OPTIONAL] (phone numbers) — List of phone numbers
- `company_name`: string [OPTIONAL] (company name) — Company display name
- `monetary_value`: number [OPTIONAL] (opportunity value) — Monetary Value
- `pipeline_id`: integer [OPTIONAL] (pipeline ID) — Pipeline unique identifier
- `page_size`: integer [OPTIONAL] (results per page, max 200) — Page Size value
- `page_number`: integer [OPTIONAL] (page number for pagination) — Page Number value

## Example Request Bodies

**Create Lead:**
```json
{"name": "Jane Doe", "email": {"email": "jane@example.com", "category": "work"}, "company_name": "Acme Corp"}
```

**Search Leads:**
```json
{"page_size": 25, "page_number": 1}
```

## Response

**Search object:**
- `id`: string — Unique search identifier
- `name`: string — Search name or title
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
