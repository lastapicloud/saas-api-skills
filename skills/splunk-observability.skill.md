---
name: splunk-observability
description: 'Search Splunk logs, manage saved searches and indexes. Use when the
  user mentions splunk, log, search, index, SIEM, observability.

  '
version: 1.0.0
skill_type: external
base_url_env: SPLUNK_BASE_URL
auth_env_var: SPLUNK_API_TOKEN
auth_type: bearer
triggers:
  - splunk
  - log
  - search
  - index
  - SIEM
  - observability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SPLUNK_BASE_URL and SPLUNK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Splunk-Observability

Search Splunk logs, manage saved searches and indexes. Use when the user mentions splunk, log, search, index, SIEM, observability.


## API Endpoints

- **POST** `/services/search/jobs` - Create a search job
- **GET** `/services/search/jobs/{searchId}` - Get search job status
- **GET** `/services/search/jobs/{searchId}/results` - Get search results
- **GET** `/services/saved/searches` - List saved searches
- **POST** `/services/saved/searches` - Create a saved search
- **DELETE** `/services/saved/searches/{name}` - Delete a saved search
- **GET** `/services/data/indexes` - List indexes
- **POST** `/services/receivers/simple` - Submit events
- **GET** `/services/server/info` - Get server info
- **GET** `/services/authentication/current-context` - Get current user

## Actions

- create: Create a search job (POST /services/search/jobs)
- search: Get search job status (GET /services/search/jobs/{searchId})
- list: Get search results (GET /services/search/jobs/{searchId}/results)
- list_saved_searches: List saved searches (GET /services/saved/searches)
- create_saved_search: Create a saved search (POST /services/saved/searches)
- delete: Delete a saved search (DELETE /services/saved/searches/{name})
- list_indexes: List indexes (GET /services/data/indexes)
- create_submit_events: Submit events (POST /services/receivers/simple)
- get_server_info: Get server info (GET /services/server/info)
- get_current_user: Get current user (GET /services/authentication/current-context)

## Fields

- `search`: string [REQUIRED for search] (SPL query) — Search
- `earliest_time`: string [OPTIONAL] (e.g., "-24h") — Earliest Time
- `latest_time`: string [OPTIONAL] (e.g., "now") — Latest Time
- `name`: string [REQUIRED for create saved search] — Display name

## Example Request Bodies

**Create Search Job:**
```json
{"search": "index=main error | stats count by host", "earliest_time": "-24h", "latest_time": "now"}
```

**Create Saved Search:**
```json
{"name": "Critical Errors Last Hour", "search": "index=main level=ERROR | top 10 source"}

## Response

**Searche object:**
- `id`: string — Unique searche identifier
- `name`: string — Searche name or title
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
