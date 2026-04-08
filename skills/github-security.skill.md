---
name: github-security
description: Manage code scanning alerts, secret scanning, Dependabot alerts, and
  security advisories via the GitHub API. Use when the user mentions code scanning,
  secret scanning, dependabot, security advisory, CVE, vulnerability alert, github
  security, SARIF.
version: 1.0.0
skill_type: external
base_url_env: GITHUB_API_BASE_URL
auth_env_var: GITHUB_API_TOKEN
auth_type: bearer
triggers:
  - code scanning
  - secret scanning
  - dependabot
  - security advisory
  - CVE
  - vulnerability alert
  - github security
  - SARIF
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GITHUB_API_BASE_URL and GITHUB_API_TOKEN environment variables.
---

# Github-Security

Manage code scanning alerts, secret scanning, Dependabot alerts, and security advisories via the GitHub API. Use when the user mentions code scanning, secret scanning, dependabot, security advisory, CVE, vulnerability alert, github security, SARIF.

## API Endpoints

- **GET** `/repos/{owner}/{repo}/code-scanning/alerts` - List code scanning alerts for a repository
- **GET** `/repos/{owner}/{repo}/code-scanning/alerts/{alert_number}` - Get a code scanning alert
- **PATCH** `/repos/{owner}/{repo}/code-scanning/alerts/{alert_number}` - Update a code scanning alert
- **GET** `/repos/{owner}/{repo}/secret-scanning/alerts` - List secret scanning alerts for a repository
- **GET** `/repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}` - Get a secret scanning alert
- **PATCH** `/repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}` - Update a secret scanning alert
- **GET** `/repos/{owner}/{repo}/dependabot/alerts` - List Dependabot alerts for a repository
- **GET** `/repos/{owner}/{repo}/dependabot/alerts/{alert_number}` - Get a Dependabot alert
- **PATCH** `/repos/{owner}/{repo}/dependabot/alerts/{alert_number}` - Update a Dependabot alert
- **GET** `/orgs/{org}/code-scanning/alerts` - List code scanning alerts for an organization
- **GET** `/repos/{owner}/{repo}/code-scanning/analyses`
- **GET** `/gists` - List gists for the authenticated user
- **POST** `/gists` - Create a gist
- **PATCH** `/gists/{gist_id}` - Update a gist
- **PUT** `/gists/{gist_id}/star` - Star a gist

## Actions

- list: List code scanning alerts for a repository (GET /repos/{owner}/{repo}/code-scanning/alerts)
- get_by_id: Get a code scanning alert (GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number})
- update: Update a code scanning alert (PATCH /repos/{owner}/{repo}/code-scanning/alerts/{alert_number})
- list_alerts: List secret scanning alerts for a repository (GET /repos/{owner}/{repo}/secret-scanning/alerts)
- get_by_id_alerts: Get a secret scanning alert (GET /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number})
- update_alerts: Update a secret scanning alert (PATCH /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number})
- list_alerts_2: List Dependabot alerts for a repository (GET /repos/{owner}/{repo}/dependabot/alerts)
- get_by_id_alerts_2: Get a Dependabot alert (GET /repos/{owner}/{repo}/dependabot/alerts/{alert_number})
- update_alerts_2: Update a Dependabot alert (PATCH /repos/{owner}/{repo}/dependabot/alerts/{alert_number})
- list_alerts_3: List code scanning alerts for an organization (GET /orgs/{org}/code-scanning/alerts)
- list_analyses: GET /repos/{owner}/{repo}/code-scanning/analyses (GET /repos/{owner}/{repo}/code-scanning/analyses)
- list_gists: List gists for the authenticated user (GET /gists)
- create: Create a gist (POST /gists)
- update_gists: Update a gist (PATCH /gists/{gist_id})
- put_star: Star a gist (PUT /gists/{gist_id}/star)

## Fields

- `owner`: string [REQUIRED for repo-level endpoints] (repository owner)
- `repo`: string [REQUIRED for repo-level endpoints] (repository name)
- `alert_number`: integer [REQUIRED for get/update endpoints] (alert number)
- `org`: string [REQUIRED for org-level endpoints] (organization name)
- `state`: string [OPTIONAL for list/update] (alert state: open, dismissed, fixed)
- `dismissed_reason`: string [OPTIONAL for update] (reason for dismissal)
- `severity`: string [OPTIONAL for list] (filter by severity: critical, high, medium, low)

## Example Request Bodies

**Update Code Scanning Alert:**
```json
{"state": "dismissed", "dismissed_reason": "won't fix", "dismissed_comment": "Not applicable"}
```

**Update Dependabot Alert:**
```json
{"state": "dismissed", "dismissed_reason": "tolerable_risk", "dismissed_comment": "Accepted risk"}
```
