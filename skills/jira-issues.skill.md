---
name: jira-issues
description: "Complete Jira project management \u2014 issues (CRUD, search, transitions,\
  \ assign, link, watchers, comments, attachments, worklogs), projects, boards, sprints,\
  \ users, fields, priorities, statuses, issue types, and filters. Use when the user\
  \ mentions jira, issue, ticket, bug, story, task, epic, sprint, backlog, board,\
  \ kanban, scrum, workflow, transition."
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
- **POST** `/rest/api/3/issue/{issueIdOrKey}/comment` - Add a comment
- **GET** `/rest/api/3/issue/{issueIdOrKey}/worklog` - Get worklogs
- **POST** `/rest/api/3/issue/{issueIdOrKey}/worklog` - Add worklog
- **GET** `/rest/api/3/field` - Get all fields
- **GET** `/rest/api/3/priority` - Get all priorities
- **GET** `/rest/api/3/priority/{priorityId}` - Get a specific priority
- **GET** `/rest/api/3/status` - Get all statuses
- **GET** `/rest/api/3/status/{idOrName}` - Get a specific status
- **GET** `/rest/api/3/issuetype` - Get all issue types
- **GET** `/rest/api/3/issuetype/{issueTypeId}` - Get a specific issue type
- **POST** `/rest/api/3/filter` - Create a saved filter
- **GET** `/rest/api/3/filter/{filterId}` - Get a saved filter
- **PUT** `/rest/api/3/filter/{filterId}` - Update a saved filter
- **DELETE** `/rest/api/3/filter/{filterId}` - Delete a saved filter
- **GET** `/rest/api/3/filter/search` - Search saved filters
- **POST** `/rest/api/3/project` - Create a project
- **GET** `/rest/api/3/project` - Get all projects
- **GET** `/rest/api/3/project/{projectIdOrKey}` - Get a project
- **GET** `/rest/api/3/board` - Get all boards
- **GET** `/rest/api/3/board/{boardId}/sprint` - Get sprints
- **POST** `/rest/api/3/sprint` - Create a sprint
- **PUT** `/rest/api/3/sprint/{sprintId}` - Update sprint
- **POST** `/rest/api/3/sprint/{sprintId}/issue` - Move issues to sprint

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
- create_comment: Add a comment (POST /rest/api/3/issue/{issueIdOrKey}/comment)
- list_worklog: Get worklogs (GET /rest/api/3/issue/{issueIdOrKey}/worklog)
- create_worklog: Add worklog (POST /rest/api/3/issue/{issueIdOrKey}/worklog)
- list_field: Get all fields (GET /rest/api/3/field)
- list_priority: Get all priorities (GET /rest/api/3/priority)
- get_by_id_priority: Get a specific priority (GET /rest/api/3/priority/{priorityId})
- list_status: Get all statuses (GET /rest/api/3/status)
- get_by_id_status: Get a specific status (GET /rest/api/3/status/{idOrName})
- list_issuetype: Get all issue types (GET /rest/api/3/issuetype)
- get_by_id_issuetype: Get a specific issue type (GET /rest/api/3/issuetype/{issueTypeId})
- create_filter: Create a saved filter (POST /rest/api/3/filter)
- get_by_id_filter: Get a saved filter (GET /rest/api/3/filter/{filterId})
- update_filter: Update a saved filter (PUT /rest/api/3/filter/{filterId})
- delete_filter: Delete a saved filter (DELETE /rest/api/3/filter/{filterId})
- search_filter: Search saved filters (GET /rest/api/3/filter/search)
- create_project: Create a project (POST /rest/api/3/project)
- list_project: Get all projects (GET /rest/api/3/project)
- get_by_id_project: Get a project (GET /rest/api/3/project/{projectIdOrKey})
- list_board: Get all boards (GET /rest/api/3/board)
- list_sprint: Get sprints (GET /rest/api/3/board/{boardId}/sprint)
- create_sprint: Create a sprint (POST /rest/api/3/sprint)
- update_sprint: Update sprint (PUT /rest/api/3/sprint/{sprintId})
- create_sprint_issue: Move issues to sprint (POST /rest/api/3/sprint/{sprintId}/issue)

## Fields

- `issueIdOrKey`: string [REQUIRED for get/update/delete/transition] (issue ID or key)
- `projectIdOrKey`: string [REQUIRED for create] (project ID or key)
- `summary`: string [REQUIRED for create issue] (issue summary)
- `description`: object [OPTIONAL] (ADF document)
- `issuetype`: object [REQUIRED for create] (issue type)
- `priority`: object [OPTIONAL] (priority)
- `assignee`: object [OPTIONAL] (assignee account)
- `labels`: array [OPTIONAL] (issue labels)
- `project`: object [REQUIRED for create] (project reference)
- `parent`: object [OPTIONAL for subtask] (parent issue)
- `filterId`: string [REQUIRED for filter operations] (filter ID)
- `boardId`: integer [REQUIRED for board operations] (board ID)
- `sprintId`: integer [REQUIRED for sprint operations] (sprint ID)

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
