---
name: snyk-security
description: "Scan for vulnerabilities, manage projects, and track security issues\
  \ via the Snyk API. Use when the user mentions snyk, vulnerability scan, dependency\
  \ vulnerability, snyk project, snyk issue, software composition analysis, open source\
  \ security.\n (API 1.0.0)"
version: 1.0.0
skill_type: external
base_url_env: SNYK_BASE_URL
auth_env_var: SNYK_API_TOKEN
auth_type: bearer
triggers:
  - snyk
  - vulnerability scan
  - dependency vulnerability
  - snyk project
  - snyk issue
  - software composition analysis
  - open source security
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SNYK_BASE_URL and SNYK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Snyk-Security

Scan for vulnerabilities, manage projects, and track security issues via the Snyk API. Use when the user mentions snyk, vulnerability scan, dependency vulnerability, snyk project, snyk issue, software composition analysis, open source security.
 (API 1.0.0)

## API Endpoints

- **POST** `/org` - Create a new organization
- **GET** `/org/{orgId}/entitlements` - List all entitlements
- **PUT** `/org/{orgId}/notification-settings` - Set notification settings
- **DELETE** `/org/{orgId}` - Remove organization
- **GET** `/group/{groupId}/members` - List all members in a group
- **PUT** `/group/{groupId}/settings` - Update group settings
- **POST** `/group/{groupId}/audit` - Get group level audit logs
- **POST** `/test/composer` - Test composer.json & composer.lock file
- **GET** `/test/gradle/{group}/{name}/{version}` - Test for issues in a public package by group, name and version
- **GET** `/user/me` - Get My Details
- **PUT** `/user/me/notification-settings/org/{orgId}` - Modify organization notification settings
- **POST** `/reporting/counts/issues` - Get issue counts
- **GET** `/orgs` - List all the organizations a user belongs to
- **POST** `/monitor/dep-graph` - Monitor Dep Graph

## Actions

- create: Create a new organization (POST /org)
- list: List all entitlements (GET /org/{orgId}/entitlements)
- put_notification_settings: Set notification settings (PUT /org/{orgId}/notification-settings)
- delete: Remove organization (DELETE /org/{orgId})
- list_members_group: List all members in a group (GET /group/{groupId}/members)
- put_settings: Update group settings (PUT /group/{groupId}/settings)
- get_group_level_audit: Get group level audit logs (POST /group/{groupId}/audit)
- create_composer: Test composer.json & composer.lock file (POST /test/composer)
- get_by_id: Test for issues in a public package by group, name and version (GET /test/gradle/{group}/{name}/{version})
- get_my_details: Get My Details (GET /user/me)
- update: Modify organization notification settings (PUT /user/me/notification-settings/org/{orgId})
- get_issue_counts: Get issue counts (POST /reporting/counts/issues)
- list_organizations_user_belongs: List all the organizations a user belongs to (GET /orgs)
- create_monitor_dep_graph: Monitor Dep Graph (POST /monitor/dep-graph)

## Fields

### Org (Create a new organization)
- `groupId`: string [OPTIONAL] — The group ID. The `API_KEY` must have access to this group.
- `name`: string [REQUIRED] — The name of the new organization
- `sourceOrgId`: string [OPTIONAL] — The id of an organization to copy settings from.

If provided, this organization must be associated with the same group.

### Notification Settings (Set notification settings)
- `new-issues-remediations`: object [OPTIONAL] ({enabled [REQUIRED], issueSeverity [REQUIRED], issueType [REQUIRED]}) — New Issues Remediations configuration
- `project-imported`: object [OPTIONAL] ({enabled [REQUIRED]}) — Project Imported configuration
- `test-limit`: object [OPTIONAL] ({enabled [REQUIRED]}) — Test- maximum number of results
- `weekly-report`: object [OPTIONAL] ({enabled [REQUIRED]}) — Weekly Report configuration

### Audit (Get group level audit logs)
- `filters`: object [OPTIONAL] ({email , event , excludeEvent , projectId , userId }) — Filters configuration

## Example Request Bodies

**Update Project:**
```json
{"data": {"attributes": {"name": "my-project"}, "type": "project"}}
```

## Response

**Org object:**
- `id`: string — Unique org identifier
- `name`: string — Org name or title
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
