---
name: linear-issues
description: Manage issues, projects, and cycles in Linear (GraphQL-only API). Use
  when the user mentions linear, issue, project, cycle, sprint, task, bug.
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
- create_graphql: Create issue (GraphQL: issueCreate mutation) (POST /graphql)
- create_graphql_2: Update issue (GraphQL: issueUpdate mutation) (POST /graphql)
- create_graphql_3: List projects (GraphQL: projects query) (POST /graphql)
- create_graphql_4: List cycles (GraphQL: cycles query) (POST /graphql)
- create_graphql_5: List teams (GraphQL: teams query) (POST /graphql)
- create_graphql_6: Search issues (GraphQL: issueSearch query) (POST /graphql)

## Fields

- `teamId`: string [REQUIRED for create_issue] (team ID)
- `title`: string [REQUIRED for create_issue] (issue title)
- `description`: string [OPTIONAL for create_issue] (issue description in markdown)
- `priority`: integer [OPTIONAL for create_issue] (0=none, 1=urgent, 2=high, 3=medium, 4=low)
- `assigneeId`: string [OPTIONAL for create_issue] (user ID to assign)
- `stateId`: string [OPTIONAL for update_issue] (workflow state ID)
- `labelIds`: array [OPTIONAL for create_issue] (label IDs)
- `projectId`: string [OPTIONAL for create_issue] (project ID)
- `id`: string [REQUIRED for update_issue] (issue ID)
- `query`: string [REQUIRED for search_issues] (search query)

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
