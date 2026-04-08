---
name: splunk-observability
description: Search Splunk logs, manage saved searches and indexes. Use when the user
  mentions splunk, log, search, index, SIEM, observability.
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
- search_searches: List saved searches (GET /services/saved/searches)
- search_searches_2: Create a saved search (POST /services/saved/searches)
- delete: Delete a saved search (DELETE /services/saved/searches/{name})
- list_indexes: List indexes (GET /services/data/indexes)
- create_simple: Submit events (POST /services/receivers/simple)
- list_info: Get server info (GET /services/server/info)
- list_current_context: Get current user (GET /services/authentication/current-context)

## Fields

- `search`: string [REQUIRED for search] (SPL query)
- `earliest_time`: string [OPTIONAL] (e.g., "-24h")
- `latest_time`: string [OPTIONAL] (e.g., "now")
- `name`: string [REQUIRED for create saved search]

## Example Request Bodies

**Create Search Job:**
```json
{"search": "index=main error | stats count by host", "earliest_time": "-24h", "latest_time": "now"}
```

**Create Saved Search:**
```json
{"name": "Critical Errors Last Hour", "search": "index=main level=ERROR | top 10 source"}
