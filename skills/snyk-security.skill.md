---
name: snyk-security
description: Scan for vulnerabilities, manage projects, and track security issues
  via the Snyk API. Use when the user mentions snyk, vulnerability scan, dependency
  vulnerability, snyk project, snyk issue, software composition analysis, open source
  security.
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
---

# Snyk-Security

Scan for vulnerabilities, manage projects, and track security issues via the Snyk API. Use when the user mentions snyk, vulnerability scan, dependency vulnerability, snyk project, snyk issue, software composition analysis, open source security.

## API Endpoints

- **GET** `/rest/orgs` - List all accessible organizations
- **GET** `/rest/orgs/{org_id}/projects` - List all projects for an organization
- **GET** `/rest/orgs/{org_id}/projects/{project_id}` - Get project details
- **PATCH** `/rest/orgs/{org_id}/projects/{project_id}` - Update a project
- **DELETE** `/rest/orgs/{org_id}/projects/{project_id}` - Delete a project
- **GET** `/rest/orgs/{org_id}/issues` - List issues for an organization
- **GET** `/rest/orgs/{org_id}/issues/{issue_id}` - Get issue details
- **GET** `/rest/orgs/{org_id}/packages/{purl}/issues` - List issues for a specific package
- **POST** `/org` - Create a new organization
- **GET** `/org/{orgId}/entitlements` - List all entitlements
- **PUT** `/org/{orgId}/notification-settings` - Set notification settings
- **DELETE** `/org/{orgId}` - Remove organization
- **GET** `/group/{groupId}/members` - List all members in a group
- **PUT** `/group/{groupId}/settings` - Update group settings
- **POST** `/group/{groupId}/audit` - Get group level audit logs

## Actions

- list: List all accessible organizations (GET /rest/orgs)
- list_projects: List all projects for an organization (GET /rest/orgs/{org_id}/projects)
- get_by_id: Get project details (GET /rest/orgs/{org_id}/projects/{project_id})
- update: Update a project (PATCH /rest/orgs/{org_id}/projects/{project_id})
- delete: Delete a project (DELETE /rest/orgs/{org_id}/projects/{project_id})
- list_issues: List issues for an organization (GET /rest/orgs/{org_id}/issues)
- get_by_id_issues: Get issue details (GET /rest/orgs/{org_id}/issues/{issue_id})
- list_issues_2: List issues for a specific package (GET /rest/orgs/{org_id}/packages/{purl}/issues)
- create: Create a new organization (POST /org)
- list_entitlements: List all entitlements (GET /org/{orgId}/entitlements)
- put_notification_settings: Set notification settings (PUT /org/{orgId}/notification-settings)
- delete_org: Remove organization (DELETE /org/{orgId})
- list_members: List all members in a group (GET /group/{groupId}/members)
- put_settings: Update group settings (PUT /group/{groupId}/settings)
- create_audit: Get group level audit logs (POST /group/{groupId}/audit)

## Fields

- `org_id`: string [REQUIRED for list_projects, get_project, update_project, delete_project, list_issues, get_issue, list_package_issues] (organization ID)
- `project_id`: string [REQUIRED for get_project, update_project, delete_project] (project ID)
- `issue_id`: string [REQUIRED for get_issue] (issue ID)
- `purl`: string [REQUIRED for list_package_issues] (package URL identifier)
- `version`: string [REQUIRED for all requests as query param] (API version date, e.g., 2024-10-15)

## Example Request Bodies

**Update Project:**
```json
{"data": {"attributes": {"name": "my-project"}, "type": "project"}}
```
