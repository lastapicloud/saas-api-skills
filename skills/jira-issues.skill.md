---
name: jira-issues
description: "Complete Jira project management \u2014 issues (CRUD, search, transitions, assign, link, watchers, comments, attachments, worklogs), projects, boards, sprints, users, fields, priorities, statuses, issue types, and filters. Use when the user mentions jira, issue, ticket, bug, story, task, epic, sprint, backlog, board, kanban, scrum, workflow, transition."
version: 1.0.0
skill_type: external
base_url_env: ATLASSIAN_BASE_URL
auth_env_var: ATLASSIAN_API_TOKEN
auth_user_env: ATLASSIAN_EMAIL
auth_type: basic
triggers:
  - jira
  - issue
  - ticket
  - bug
  - story
  - task
  - epic
  - sprint
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires ATLASSIAN_BASE_URL and ATLASSIAN_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Jira-Issues

Complete Jira project management — issues (CRUD, search, transitions, assign, link, watchers, comments, attachments, worklogs), projects, boards, sprints, users, fields, priorities, statuses, issue types, and filters. Use when the user mentions jira, issue, ticket, bug, story, task, epic, sprint, backlog, board, kanban, scrum, workflow, transition.


## API Endpoints

- **POST** `/rest/api/3/issue` - Create a new issue
- **GET** `/rest/api/3/issue/{issueIdOrKey}` - Get a specific issue
- **PUT** `/rest/api/3/issue/{issueIdOrKey}` - Update an issue
- **DELETE** `/rest/api/3/issue/{issueIdOrKey}` - Delete an issue
- **GET** `/rest/api/3/search` - Search issues using JQL (GET)
- **POST** `/rest/api/3/search` - Search issues using JQL (POST, supports more complex queries)
- **POST** `/rest/api/3/issue/bulk` - Bulk create issues (up to 50)
- **PUT** `/rest/api/3/issue/{issueIdOrKey}/assignee` - Assign an issue
- **GET** `/rest/api/3/issue/{issueIdOrKey}/transitions` - Get available transitions
- **POST** `/rest/api/3/issue/{issueIdOrKey}/transitions` - Transition an issue to a new status
- **POST** `/rest/api/3/issueLink` - Create an issue link
- **GET** `/rest/api/3/issueLink/{linkId}` - Get an issue link
- **DELETE** `/rest/api/3/issueLink/{linkId}` - Delete an issue link
- **GET** `/rest/api/3/issueLinkType` - Get all issue link types
- **GET** `/rest/api/3/issue/{issueIdOrKey}/watchers` - Get issue watchers

## Actions

- create: Create a new issue (POST /rest/api/3/issue)
- get_by_id: Get a specific issue (GET /rest/api/3/issue/{issueIdOrKey})
- update: Update an issue (PUT /rest/api/3/issue/{issueIdOrKey})
- delete: Delete an issue (DELETE /rest/api/3/issue/{issueIdOrKey})
- search: Search issues using JQL (GET) (GET /rest/api/3/search)
- search_3: Search issues using JQL (POST, supports more complex queries) (POST /rest/api/3/search)
- create_bulk: Bulk create issues (up to 50) (POST /rest/api/3/issue/bulk)
- put_assignee: Assign an issue (PUT /rest/api/3/issue/{issueIdOrKey}/assignee)
- list: Get available transitions (GET /rest/api/3/issue/{issueIdOrKey}/transitions)
- create_transitions: Transition an issue to a new status (POST /rest/api/3/issue/{issueIdOrKey}/transitions)
- create_issuelink: Create an issue link (POST /rest/api/3/issueLink)
- get_by_id_issuelink: Get an issue link (GET /rest/api/3/issueLink/{linkId})
- delete_issuelink: Delete an issue link (DELETE /rest/api/3/issueLink/{linkId})
- list_issuelinktype: Get all issue link types (GET /rest/api/3/issueLinkType)
- list_watchers: Get issue watchers (GET /rest/api/3/issue/{issueIdOrKey}/watchers)

## Fields

**IMPORTANT:** Jira create/update wraps all fields inside `{"fields": {...}}`. The system handles this automatically — just provide the inner fields.

### Issue Fields (create/update)
- `project`: object [REQUIRED for create] — Must contain `key` (e.g., `{"key": "PROJ"}`) or `id` (e.g., `{"id": "10110"}`)
- `summary`: string [REQUIRED for create] — Issue title, max 255 chars
- `issuetype`: object [REQUIRED for create] — Must contain `name` (e.g., `{"name": "Bug"}`) or `id` (e.g., `{"id": "1"}`). Common types: Bug, Story, Task, Epic, Sub-task
- `description`: object [OPTIONAL] — Atlassian Document Format (ADF). Structure: `{"type": "doc", "version": 1, "content": [{"type": "paragraph", "content": [{"type": "text", "text": "..."}]}]}`
- `priority`: object [OPTIONAL] — `{"name": "High"}` or `{"id": "2"}`. Values: Highest, High, Medium, Low, Lowest
- `assignee`: object [OPTIONAL] — `{"accountId": "5b10ac..."}` (Atlassian account ID, NOT username)
- `reporter`: object [OPTIONAL] — `{"accountId": "5b10ac..."}`
- `labels`: array [OPTIONAL] — String array, e.g., `["bugfix", "backend"]`
- `parent`: object [OPTIONAL] — For subtasks: `{"key": "PROJ-101"}` or `{"id": "39000"}`
- `timetracking`: object [OPTIONAL] — `{"originalEstimate": "1d 2h", "remainingEstimate": "3h"}`
- `customfield_NNNNN`: varies [OPTIONAL] — Custom fields by ID. Types: text=string, date="YYYY-MM-DD", number=float, select=`{"name": "value"}`

### Issue Identifiers
- `issueIdOrKey`: string [REQUIRED for get/update/delete/transition] — Issue key (e.g., "PROJ-123") or numeric ID (e.g., "39000")

### Search
- `jql`: string [REQUIRED for search] — JQL query (e.g., `project = MYPROJ AND status != Done ORDER BY priority DESC`)
- `startAt`: integer [OPTIONAL] — Pagination offset (default 0)
- `maxResults`: integer [OPTIONAL] — Max results, 1-100 (default 50)
- `fields`: array [OPTIONAL] — Fields to return (e.g., `["summary", "status", "assignee"]`)

### Other Resources
- `filterId`: string [REQUIRED for filter operations] — Numeric filter ID
- `boardId`: integer [REQUIRED for board operations] — Board ID
- `sprintId`: integer [REQUIRED for sprint operations] — Sprint ID

## Example Requests

**Create Issue (Bug with ADF description):**
```json
{
  "fields": {
    "project": {"key": "MYPROJ"},
    "summary": "Login page returns 500 on invalid email format",
    "issuetype": {"name": "Bug"},
    "priority": {"name": "High"},
    "labels": ["backend", "auth"],
    "description": {
      "type": "doc",
      "version": 1,
      "content": [
        {
          "type": "paragraph",
          "content": [
            {"type": "text", "text": "Steps to reproduce: Enter 'notanemail' in the login form and submit. Expected: validation error. Actual: HTTP 500."}
          ]
        }
      ]
    }
  }
}
```

**Search Issues with JQL (GET):**
Query parameters: `jql=project = MYPROJ AND status != Done AND assignee = currentUser() ORDER BY priority DESC, created ASC&startAt=0&maxResults=25&fields=summary,status,assignee,priority`

**Search Issues with JQL (POST):**
```json
{
  "jql": "project = MYPROJ AND type = Bug AND priority IN (High, Highest) AND created >= -7d ORDER BY created DESC",
  "startAt": 0,
  "maxResults": 50,
  "fields": ["summary", "status", "assignee", "priority", "created"]
}
```

**Transition Issue (move to "In Progress"):**
First, get available transitions: `GET /rest/api/3/issue/MYPROJ-123/transitions`
Then, apply the transition using the returned ID:
```json
{
  "transition": {"id": "21"},
  "update": {
    "comment": [
      {
        "add": {
          "body": {
            "type": "doc",
            "version": 1,
            "content": [
              {
                "type": "paragraph",
                "content": [{"type": "text", "text": "Starting work on this issue."}]
              }
            ]
          }
        }
      }
    ]
  }
}
```

**Add Comment:**
```json
{
  "body": {
    "type": "doc",
    "version": 1,
    "content": [
      {
        "type": "paragraph",
        "content": [
          {"type": "text", "text": "Confirmed this bug on staging. Root cause is missing input validation in "},
          {"type": "text", "text": "AuthController.login()", "marks": [{"type": "code"}]},
          {"type": "text", "text": "."}
        ]
      }
    ]
  }
}
```

**Assign Issue:**
```json
{"accountId": "5b10ac8d82e05b22cc7d4ef5"}
```

**Create Issue Link (PROJ-1 blocks PROJ-2):**
```json
{
  "type": {"name": "Blocks"},
  "inwardIssue": {"key": "MYPROJ-1"},
  "outwardIssue": {"key": "MYPROJ-2"},
  "comment": {
    "body": {
      "type": "doc",
      "version": 1,
      "content": [
        {"type": "paragraph", "content": [{"type": "text", "text": "MYPROJ-2 depends on the API changes in MYPROJ-1."}]}
      ]
    }
  }
}
```

**Add Worklog (2 hours):**
```json
{
  "timeSpent": "2h",
  "started": "2026-03-25T09:00:00.000+0000",
  "comment": {
    "type": "doc",
    "version": 1,
    "content": [
      {"type": "paragraph", "content": [{"type": "text", "text": "Investigated root cause and wrote unit tests."}]}
    ]
  }
}
```

**Create Sprint:**
```json
{
  "name": "Sprint 14",
  "originBoardId": 5,
  "startDate": "2026-03-25T00:00:00.000Z",
  "endDate": "2026-04-08T00:00:00.000Z",
  "goal": "Complete authentication module and API rate limiting"
}
```

**Move Issues to Sprint:**
```json
{
  "issues": ["MYPROJ-101", "MYPROJ-102", "MYPROJ-103"]
}
```

**Create Project:**
```json
{
  "key": "NEWPROJ",
  "name": "New Project",
  "projectTypeKey": "software",
  "leadAccountId": "5b10ac8d82e05b22cc7d4ef5",
  "description": "Backend services for the new platform"
}
```

**Create Saved Filter:**
```json
{
  "name": "My Open Bugs",
  "jql": "project = MYPROJ AND type = Bug AND status != Done AND assignee = currentUser()",
  "description": "All open bugs assigned to me",
  "favourite": true
}
```

**Create Sub-task:**
```json
{
  "fields": {
    "project": {"key": "MYPROJ"},
    "parent": {"key": "MYPROJ-100"},
    "summary": "Write unit tests for login validation",
    "issuetype": {"name": "Sub-task"}
  }
}
```

**Create Project Version:**
```json
{
  "name": "2.0.0",
  "projectId": 10001,
  "description": "Major release with new authentication system",
  "releaseDate": "2026-06-01",
  "released": false
}
```

## Response

**create response (201):**
- `id`: string — Numeric issue ID (e.g., "39000")
- `key`: string — Issue key (e.g., "PROJ-123")
- `self`: string — API URL for the created issue

**search response:**
- `issues[]`: array of issue objects
- `issues[].key`: string — Issue key
- `issues[].fields.summary`: string
- `issues[].fields.status.name`: string — Current status
- `issues[].fields.assignee.displayName`: string
- `total`: integer — Total matching issues
- `startAt`: integer — Pagination offset
- `maxResults`: integer

## Error Responses

Jira returns `{"errorMessages": [...], "errors": {...}}` on failure.

| Status | Meaning |
|--------|---------|
| 201 | Issue created successfully |
| 400 | Validation error — `errorMessages` array contains details (e.g., "Field 'summary' is required") |
| 401 | Unauthenticated — invalid or expired API token |
| 403 | No permission — user lacks create/edit permission for this project |
| 404 | Issue, project, or resource not found |
| 409 | Conflict — concurrent modification |
| 429 | Rate limited — too many requests |

**Common 400 errors:**
- `"Field 'summary' is required"` — Missing summary on create
- `"valid issue type is required"` — Invalid issuetype name or id
- `"project is required"` — Missing project key or id
- `"Issue Does Not Exist"` — Wrong issueIdOrKey in URL
