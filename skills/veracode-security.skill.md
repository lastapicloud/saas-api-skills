---
name: veracode-security
description: 'Manage application profiles, scan for vulnerabilities, and review findings
  via the Veracode API. Use when the user mentions veracode, veracode scan, veracode
  finding, application security, SAST veracode, DAST veracode, software composition.

  '
version: 1.0.0
skill_type: external
base_url_env: VERACODE_BASE_URL
auth_env_var: VERACODE_API_KEY
auth_type: header
triggers:
  - veracode
  - veracode scan
  - veracode finding
  - application security
  - SAST veracode
  - DAST veracode
  - software composition
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires VERACODE_BASE_URL and VERACODE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Veracode-Security

Manage application profiles, scan for vulnerabilities, and review findings via the Veracode API. Use when the user mentions veracode, veracode scan, veracode finding, application security, SAST veracode, DAST veracode, software composition.


## API Endpoints

- **GET** `/appsec/v1/applications` - List all application profiles
- **GET** `/appsec/v1/applications/{application_guid}` - Get application profile details
- **POST** `/appsec/v1/applications` - Create an application profile
- **PUT** `/appsec/v1/applications/{application_guid}` - Update an application profile
- **DELETE** `/appsec/v1/applications/{application_guid}` - Delete an application profile
- **GET** `/appsec/v2/applications/{application_guid}/findings` - List findings for an application
- **GET** `/appsec/v2/applications/{application_guid}/summary_report` - Get application summary report
- **GET** `/appsec/v1/applications/{application_guid}/sandboxes` - List sandboxes for an application

## Actions

- list: List all application profiles (GET /appsec/v1/applications)
- get_by_id: Get application profile details (GET /appsec/v1/applications/{application_guid})
- create: Create an application profile (POST /appsec/v1/applications)
- update: Update an application profile (PUT /appsec/v1/applications/{application_guid})
- delete: Delete an application profile (DELETE /appsec/v1/applications/{application_guid})
- list_findings_application: List findings for an application (GET /appsec/v2/applications/{application_guid}/findings)
- get_application_summary_report: Get application summary report (GET /appsec/v2/applications/{application_guid}/summary_report)
- list_sandboxes_application: List sandboxes for an application (GET /appsec/v1/applications/{application_guid}/sandboxes)

## Fields

- `application_guid`: string [REQUIRED for get_application, update_application, delete_application, list_findings, get_summary_report, list_sandboxes] (application GUID) — Application Gu unique identifier
- `profile`: object [REQUIRED for create_application] (application profile with name and business_criticality) — Profile configuration
- `scan_type`: string [OPTIONAL for list_findings] (filter: STATIC, DYNAMIC, MANUAL, SCA) — Scan resource type
- `severity`: integer [OPTIONAL for list_findings] (minimum severity: 0-5) — Severity value
- `violates_policy`: boolean [OPTIONAL for list_findings] (filter by policy violation) — Whether violates policy is enabled
- `cvss_gte`: number [OPTIONAL for list_findings] (minimum CVSS score) — Cvss Gte

## Example Request Bodies

**Create Application Profile:**
```json
{"profile": {"name": "My Application", "business_criticality": "HIGH", "policy_id": 1234}}
```

## Response

**Application object:**
- `id`: string — Unique application identifier
- `name`: string — Application name or title
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
