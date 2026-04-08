---
name: veracode-security
description: Manage application profiles, scan for vulnerabilities, and review findings
  via the Veracode API. Use when the user mentions veracode, veracode scan, veracode
  finding, application security, SAST veracode, DAST veracode, software composition.
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
- list_findings: List findings for an application (GET /appsec/v2/applications/{application_guid}/findings)
- list_summary_report: Get application summary report (GET /appsec/v2/applications/{application_guid}/summary_report)
- list_sandboxes: List sandboxes for an application (GET /appsec/v1/applications/{application_guid}/sandboxes)

## Fields

- `application_guid`: string [REQUIRED for get_application, update_application, delete_application, list_findings, get_summary_report, list_sandboxes] (application GUID)
- `profile`: object [REQUIRED for create_application] (application profile with name and business_criticality)
- `scan_type`: string [OPTIONAL for list_findings] (filter: STATIC, DYNAMIC, MANUAL, SCA)
- `severity`: integer [OPTIONAL for list_findings] (minimum severity: 0-5)
- `violates_policy`: boolean [OPTIONAL for list_findings] (filter by policy violation)
- `cvss_gte`: number [OPTIONAL for list_findings] (minimum CVSS score)

## Example Request Bodies

**Create Application Profile:**
```json
{"profile": {"name": "My Application", "business_criticality": "HIGH", "policy_id": 1234}}
```
