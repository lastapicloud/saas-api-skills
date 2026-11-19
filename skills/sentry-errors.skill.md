---
name: sentry-errors
description: 'Track errors, manage issues, and monitor releases via the Sentry API.
  Use when the user mentions sentry, error, issue, bug, crash, exception, release.

  '
version: 1.0.0
skill_type: external
base_url_env: SENTRY_BASE_URL
auth_env_var: SENTRY_AUTH_TOKEN
auth_type: bearer
triggers:
  - sentry
  - error
  - issue
  - bug
  - crash
  - exception
  - release
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SENTRY_BASE_URL and SENTRY_AUTH_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Sentry-Errors

Track errors, manage issues, and monitor releases via the Sentry API. Use when the user mentions sentry, error, issue, bug, crash, exception, release.


## API Endpoints

- **GET** `/projects/` - List all projects
- **GET** `/projects/{organization_slug}/{project_slug}/issues/` - List issues for a project
- **GET** `/issues/{issue_id}/` - Get issue details
- **PUT** `/issues/{issue_id}/` - Resolve or update an issue
- **POST** `/organizations/{organization_slug}/releases/` - Create a new release
- **GET** `/issues/{issue_id}/events/` - List events for an issue
- **GET** `/api/0/projects/{organization_id_or_slug}/{project_id_or_slug}/issues/`
- **GET** `/api/0/organizations/` - Return a list of organizations available to the authenticated session in a region.
- **PUT** `/api/0/organizations/{organization_id_or_slug}/` - Update various attributes and configurable settings for the given organization.
- **DELETE** `/api/0/organizations/{organization_id_or_slug}/detectors/` - ⚠️ This endpoint is currently in **beta** and may be subject to change. It is supported by [New Monitors and
- **POST** `/api/0/organizations/{organization_id_or_slug}/alert-rules/` - ## Deprecated
- **PATCH** `/api/0/organizations/{organization_id_or_slug}/scim/v2/Groups/{team_id_or_slug}` - Update a team's attributes with a SCIM Group PATCH Request.
- **GET** `/api/0/seer/models/` - Get list of actively used LLM model names from Seer.

## Actions

- list: List all projects (GET /projects/)
- list_issues_project: List issues for a project (GET /projects/{organization_slug}/{project_slug}/issues/)
- get_by_id: Get issue details (GET /issues/{issue_id}/)
- update: Resolve or update an issue (PUT /issues/{issue_id}/)
- create: Create a new release (POST /organizations/{organization_slug}/releases/)
- list_events_issue: List events for an issue (GET /issues/{issue_id}/events/)
- list_issues: GET /api/0/projects/{organization_id_or_slug}/{project_id_or_slug}/issues/ (GET /api/0/projects/{organization_id_or_slug}/{project_id_or_slug}/issues/)
- get_return_list_organizations_available: Return a list of organizations available to the authenticated session in a regio (GET /api/0/organizations/)
- update_various_attributes_configurable: Update various attributes and configurable settings for the given organization. (PUT /api/0/organizations/{organization_id_or_slug}/)
- delete_detectors: ⚠️ This endpoint is currently in **beta** and may be subject to change. It is su (DELETE /api/0/organizations/{organization_id_or_slug}/detectors/)
- create_deprecated: ## Deprecated (POST /api/0/organizations/{organization_id_or_slug}/alert-rules/)
- update_teams_attributes_scim: Update a team's attributes with a SCIM Group PATCH Request. (PATCH /api/0/organizations/{organization_id_or_slug}/scim/v2/Groups/{team_id_or_slug})
- get_list_actively_used: Get list of actively used LLM model names from Seer. (GET /api/0/seer/models/)

## Fields

- `organization_slug`: string [REQUIRED for list_issues, create_release] (organization slug) — Organization Slug
- `project_slug`: string [REQUIRED for list_issues] (project slug) — Project Slug
- `issue_id`: string [REQUIRED for get_issue, resolve_issue, list_events] (issue ID) — Issue unique identifier
- `status`: string [OPTIONAL for resolve_issue] (new status: resolved, unresolved, ignored) — Current status
- `version`: string [REQUIRED for create_release] (release version identifier) — Version
- `query`: string [OPTIONAL for list_issues] (search query) — Search or filter query

## Example Request Bodies

**Resolve Issue:**
```json
{"status": "resolved"}
```

**Create Release:**
```json
{"version": "1.0.0", "projects": ["my-project"]}
```

## Response

**Issue object:**
- `id`: string — Unique issue identifier
- `name`: string — Issue name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "organization_slug": "example_organization_slug",
  "project_slug": "example_project_slug",
  "issue_id": "example_issue_id"
}
```


**Required fields reference:**
```json
{
  "organization_slug": "example_organization_slug",
  "project_slug": "example_project_slug",
  "issue_id": "example_issue_id"
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
