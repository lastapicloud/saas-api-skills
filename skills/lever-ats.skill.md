---
name: lever-ats
description: Manage opportunities, candidates, and postings in Lever ATS. Use when
  the user mentions lever, lever candidate, lever opportunity, lever posting, lever
  hiring.
version: 1.0.0
skill_type: external
base_url_env: LEVER_BASE_URL
auth_env_var: LEVER_API_KEY
auth_type: basic
triggers:
  - lever
  - lever candidate
  - lever opportunity
  - lever posting
  - lever hiring
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LEVER_BASE_URL and LEVER_API_KEY environment variables.
---

# Lever-Ats

Manage opportunities, candidates, and postings in Lever ATS. Use when the user mentions lever, lever candidate, lever opportunity, lever posting, lever hiring.

## API Endpoints

- **GET** `/v1/opportunities` - List opportunities
- **POST** `/v1/opportunities` - Create an opportunity
- **GET** `/v1/opportunities/{id}` - Get an opportunity by ID
- **PUT** `/v1/opportunities/{id}` - Update an opportunity
- **DELETE** `/v1/opportunities/{id}` - Delete an opportunity
- **GET** `/v1/postings` - List postings
- **GET** `/v1/postings/{id}` - Get a posting by ID
- **GET** `/v1/opportunities/{id}/applications` - List applications for opportunity
- **GET** `/v1/archive_reasons` - List archive reasons
- **GET** `/v1/stages` - List pipeline stages
- **GET** `/opportunities/:opportunity/applications/:application`
- **GET** `/opportunities/:opportunity/applications`
- **GET** `/archive_reasons/:archive_reason`
- **GET** `/archive_reasons`
- **GET** `/audit_events`

## Actions

- list: List opportunities (GET /v1/opportunities)
- create: Create an opportunity (POST /v1/opportunities)
- get_by_id: Get an opportunity by ID (GET /v1/opportunities/{id})
- update: Update an opportunity (PUT /v1/opportunities/{id})
- delete: Delete an opportunity (DELETE /v1/opportunities/{id})
- list_postings: List postings (GET /v1/postings)
- get_by_id_postings: Get a posting by ID (GET /v1/postings/{id})
- list_applications: List applications for opportunity (GET /v1/opportunities/{id}/applications)
- list_archive_reasons: List archive reasons (GET /v1/archive_reasons)
- list_stages: List pipeline stages (GET /v1/stages)
- list_application: GET /opportunities/:opportunity/applications/:application (GET /opportunities/:opportunity/applications/:application)
- list_applications_2: GET /opportunities/:opportunity/applications (GET /opportunities/:opportunity/applications)
- list_archive_reason: GET /archive_reasons/:archive_reason (GET /archive_reasons/:archive_reason)
- list_archive_reasons_2: GET /archive_reasons (GET /archive_reasons)
- list_audit_events: GET /audit_events (GET /audit_events)

## Fields

- `id`: string [REQUIRED for get_opportunity, update_opportunity, delete_opportunity, get_posting, list_applications] (record ID)
- `name`: string [REQUIRED for create_opportunity] (candidate name)
- `headline`: string [OPTIONAL] (candidate headline/title)
- `emails`: array [OPTIONAL] (email addresses)
- `phones`: array [OPTIONAL] (phone numbers)
- `location`: string [OPTIONAL] (candidate location)
- `origin`: string [OPTIONAL] (sourced, applied, referred, agency)
- `stage`: string [OPTIONAL] (stage ID to move candidate to)
- `postings`: array [OPTIONAL] (posting IDs to associate)
- `tags`: array [OPTIONAL] (tags for candidate)

## Example Request Bodies

**Create Opportunity:**
```json
{"name": "Jane Doe", "headline": "Senior Engineer", "emails": ["jane@example.com"], "origin": "sourced", "postings": ["posting_abc123"]}
```

**Update Opportunity:**
```json
{"stage": "stage_abc123", "tags": ["senior", "engineering"]}
```
