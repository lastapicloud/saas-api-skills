---
name: linear-issues
description: 'Manage issues, projects, and cycles in Linear (GraphQL-only API). Use
  when the user mentions linear, issue, project, cycle, sprint, task, bug.

  '
version: 1.0.0
skill_type: external
base_url_env: LINEAR_BASE_URL
auth_env_var: LINEAR_API_KEY
auth_type: bearer
triggers:
  - linear
  - issue
  - project
  - cycle
  - sprint
  - task
  - bug
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LINEAR_BASE_URL and LINEAR_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Linear-Issues

Manage issues, projects, and cycles in Linear (GraphQL-only API). Use when the user mentions linear, issue, project, cycle, sprint, task, bug.


## API Endpoints

- **POST** `/graphql` - List issues (GraphQL: issues query)
- **POST** `/graphql` - Create issue (GraphQL: issueCreate mutation)
- **POST** `/graphql` - Update issue (GraphQL: issueUpdate mutation)
- **POST** `/graphql` - List projects (GraphQL: projects query)
- **POST** `/graphql` - List cycles (GraphQL: cycles query)
- **POST** `/graphql` - List teams (GraphQL: teams query)
- **POST** `/graphql` - Search issues (GraphQL: issueSearch query)

## Actions

- create: List issues (GraphQL: issues query) (POST /graphql)
- create_issue_graphql_issuecreate: Create issue (GraphQL: issueCreate mutation) (POST /graphql)
- update_issue_graphql_issueupdate: Update issue (GraphQL: issueUpdate mutation) (POST /graphql)
- list_projects_graphql_projects: List projects (GraphQL: projects query) (POST /graphql)
- list_cycles_graphql_cycles: List cycles (GraphQL: cycles query) (POST /graphql)
- list_teams_graphql_teams: List teams (GraphQL: teams query) (POST /graphql)
- search_issues_graphql_issuesearch: Search issues (GraphQL: issueSearch query) (POST /graphql)

## Fields

- `teamId`: string [REQUIRED for create_issue] (team ID) — Team unique identifier
- `title`: string [REQUIRED for create_issue] (issue title) — Title or heading
- `description`: string [OPTIONAL for create_issue] (issue description in markdown) — Human-readable description
- `priority`: integer [OPTIONAL for create_issue] (0=none, 1=urgent, 2=high, 3=medium, 4=low) — Priority level
- `assigneeId`: string [OPTIONAL for create_issue] (user ID to assign) — Assignee unique identifier
- `stateId`: string [OPTIONAL for update_issue] (workflow state ID) — State unique identifier
- `labelIds`: array [OPTIONAL for create_issue] (label IDs) — List of labelIds
- `projectId`: string [OPTIONAL for create_issue] (project ID) — Project unique identifier
- `id`: string [REQUIRED for update_issue] (issue ID) — Unique identifier
- `query`: string [REQUIRED for search_issues] (search query) — Search or filter query

## Example Request Bodies

**List Issues:**
```json
{"query": "{ issues(first: 50) { nodes { id title state { name } priority assignee { name } } } }"}
```

**Create Issue:**
```json
{"query": "mutation { issueCreate(input: { teamId: \"TEAM_ID\", title: \"Fix login bug\", description: \"The login page returns a 500 error\", priority: 2 }) { success issue { id identifier title url } } }"}
```

**Search Issues:**
```json
{"query": "{ issueSearch(query: \"login bug\", first: 20) { nodes { id title state { name } } } }"}
```

## Response

**Graphql object:**
- `id`: string — Unique graphql identifier
- `name`: string — Graphql name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
