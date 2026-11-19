---
name: notion-pages
description: "Complete Notion workspace management \u2014 pages, databases, blocks,\
  \ users, search, and comments with full query filtering, sorting, and rich content\
  \ support. Use when the user mentions notion, page, database, wiki, doc, note, workspace,\
  \ block, comment.\n (API 1.0.0) (API 2.0.0)"
version: 1.0.0
skill_type: external
base_url_env: NOTION_BASE_URL
auth_env_var: NOTION_API_TOKEN
auth_type: bearer
triggers:
  - notion
  - page
  - database
  - wiki
  - doc
  - note
  - workspace
  - block
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires NOTION_BASE_URL and NOTION_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Notion-Pages

Complete Notion workspace management — pages, databases, blocks, users, search, and comments with full query filtering, sorting, and rich content support. Use when the user mentions notion, page, database, wiki, doc, note, workspace, block, comment.
 (API 1.0.0) (API 2.0.0)

## API Endpoints

- **POST** `/v1/data_sources` - Create a data source
- **PATCH** `/v1/data_sources/{data_source_id}` - Update a data source
- **GET** `/v1/data_sources/{data_source_id}` - Retrieve a data source
- **POST** `/v1/pages` - Create a page
- **PATCH** `/v1/pages/{page_id}` - Update page properties
- **GET** `/v1/pages/{page_id}` - Retrieve a page
- **PATCH** `/v1/blocks/{block_id}` - Update a block
- **GET** `/v1/blocks/{block_id}` - Retrieve a block
- **DELETE** `/v1/blocks/{block_id}` - Delete a block
- **GET** `/v1/comments` - Retrieve comments
- **POST** `/v1/comments` - Create comment
- **POST** `/v1/search` - Search by title
- **GET** `/v1/databases/{database_id}` - Retrieve a database
- **GET** `/v1/users` - List all users
- **GET** `/v1/users/me` - Retrieve your token's bot user

## Actions

- create: Create a data source (POST /v1/data_sources)
- update: Update a data source (PATCH /v1/data_sources/{data_source_id})
- get_by_id: Retrieve a data source (GET /v1/data_sources/{data_source_id})
- create_page: Create a page (POST /v1/pages)
- update_page_properties: Update page properties (PATCH /v1/pages/{page_id})
- get_retrieve_page: Retrieve a page (GET /v1/pages/{page_id})
- update_block: Update a block (PATCH /v1/blocks/{block_id})
- get_retrieve_block: Retrieve a block (GET /v1/blocks/{block_id})
- delete: Delete a block (DELETE /v1/blocks/{block_id})
- list: Retrieve comments (GET /v1/comments)
- create_comment: Create comment (POST /v1/comments)
- search: Search by title (POST /v1/search)
- get_retrieve_database: Retrieve a database (GET /v1/databases/{database_id})
- list_users: List all users (GET /v1/users)
- get_retrieve_your_tokens_bot: Retrieve your token's bot user (GET /v1/users/me)

## Fields

### Data Sources (Create a data source)
- `parent`: object [REQUIRED] ({page_id [REQUIRED]}) — Parent configuration
- `properties`: object [REQUIRED] — Property schema of data source
- `title`: array [OPTIONAL] — Title or heading

## Example Request Bodies

**Create a page in a database:**
```json
{
  "parent": {"database_id": "d9824bdc-8445-4327-be8b-5b47500af6ce"},
  "icon": {"type": "emoji", "emoji": "📝"},
  "properties": {
    "Name": {"title": [{"text": {"content": "Weekly Standup Notes"}}]},
    "Status": {"select": {"name": "In Progress"}},
    "Tags": {"multi_select": [{"name": "meeting"}, {"name": "engineering"}]},
    "Due Date": {"date": {"start": "2025-03-28"}},
    "Priority": {"number": 5},
    "Assignee": {"people": [{"object": "user", "id": "user-uuid-here"}]},
    "URL": {"url": "https://meet.google.com/abc-defg-hij"},
    "Completed": {"checkbox": false}
  }
}
```

**Create a page under another page (with content blocks):**
```json
{
  "parent": {"page_id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"},
  "properties": {
    "title": [{"text": {"content": "Project Roadmap"}}]
  },
  "children": [
    {"object": "block", "type": "heading_2", "heading_2": {"rich_text": [{"type": "text", "text": {"content": "Q1 Goals"}}]}},
    {"object": "block", "type": "paragraph", "paragraph": {"rich_text": [{"type": "text", "text": {"content": "Focus on infrastructure and performance."}}]}}
  ]
}
```

**Query database with compound filter and sort:**
```json
{
  "filter": {
    "and": [
      {"property": "Status", "select": {"does_not_equal": "Archived"}},
      {"or": [
        {"property": "Priority", "number": {"greater_than_or_equal_to": 3}},
        {"property": "Tags", "multi_select": {"contains": "urgent"}}
      ]}
    ]
  },
  "sorts": [
    {"property": "Priority", "direction": "descending"},
    {"property": "Due Date", "direction": "ascending"}
  ],
  "page_size": 25
}
```

**Query database with date filter and pagination:**
```json
{
  "filter": {
    "property": "Created",
    "date": {"on_or_after": "2025-01-01"}
  },
  "sorts": [{"timestamp": "created_time", "direction": "descending"}],
  "start_cursor": "a1b2c3d4-cursor-from-previous-response",
  "page_size": 50
}
```

**Append block children (add content to a page):**
```json
{
  "children": [
    {
      "object": "block",
      "type": "heading_1",
      "heading_1": {
        "rich_text": [{"type": "text", "text": {"content": "Meeting Summary"}, "annotations": {"bold": true}}]
      }
    },
    {
      "object": "block",
      "type": "paragraph",
      "paragraph": {
        "rich_text": [
          {"type": "text", "text": {"content": "We discussed the "}, "annotations": {}},
          {"type": "text", "text": {"content": "launch timeline"}, "annotations": {"bold": true, "italic": true}},
          {"type": "text", "text": {"content": " and agreed on March 28th."}}
        ]
      }
    },
    {
      "object": "block",
      "type": "to_do",
      "to_do": {
        "rich_text": [{"type": "text", "text": {"content": "Finalize the deployment checklist"}}],
        "checked": false
      }
    },
    {
      "object": "block",
      "type": "to_do",
      "to_do": {
        "rich_text": [{"type": "text", "text": {"content": "Send invites for launch party"}}],
        "checked": true
      }
    },
    {
      "object": "block",
      "type": "bulleted_list_item",
      "bulleted_list_item": {
        "rich_text": [{"type": "text", "text": {"content": "Backend team owns deployment"}}]
      }
    },
    {
      "object": "block",
      "type": "code",
      "code": {
        "rich_text": [{"type": "text", "text": {"content": "curl -X POST https://api.example.com/deploy"}}],
        "language": "bash"
      }
    },
    {
      "object": "block",
      "type": "divider",
      "divider": {}
    },
    {
      "object": "block",
      "type": "callout",
      "callout": {
        "rich_text": [{"type": "text", "text": {"content": "Remember to update the status page before deploying."}}],
        "icon": {"type": "emoji", "emoji": "⚠️"}
      }
    }
  ]
}
```

**Search by title (pages only):**
```json
{
  "query": "meeting notes",
  "filter": {"property": "object", "value": "page"},
  "sort": {"direction": "descending", "timestamp": "last_edited_time"},
  "page_size": 10
}
```

**Search all databases:**
```json
{
  "query": "Project Tracker",
  "filter": {"property": "object", "value": "database"}
}
```

**Create a comment on a page:**
```json
{
  "parent": {"page_id": "d9824bdc-8445-4327-be8b-5b47500af6ce"},
  "rich_text": [
    {"type": "text", "text": {"content": "Looks good! Let's ship this by Friday."}}
  ]
}
```

**Create a database (under a page):**
```json
{
  "parent": {"type": "page_id", "page_id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"},
  "title": [{"type": "text", "text": {"content": "Bug Tracker"}}],
  "is_inline": true,
  "properties": {
    "Title": {"title": {}},
    "Status": {"select": {"options": [{"name": "Open", "color": "red"}, {"name": "In Progress", "color": "yellow"}, {"name": "Closed", "color": "green"}]}},
    "Severity": {"number": {"format": "number"}},
    "Assignee": {"people": {}},
    "Due Date": {"date": {}},
    "Tags": {"multi_select": {"options": [{"name": "frontend"}, {"name": "backend"}, {"name": "infra"}]}},
    "Resolved": {"checkbox": {}}
  }
}
```

**Update a block (change paragraph text):**
```json
{
  "paragraph": {
    "rich_text": [{"type": "text", "text": {"content": "Updated paragraph content with corrected information."}}]
  }
}
```

**Archive a page:**
```json
{
  "archived": true
}
```

**Update page properties:**
```json
{
  "properties": {
    "Status": {"select": {"name": "Done"}},
    "Priority": {"number": 1},
    "Completed": {"checkbox": true}
  }
}
```

## Response

**retrieve_comments response:**
- `comment`: object — Comment configuration
- `has_more`: boolean — Whether has more is enabled
- `next_cursor`: string — Next pagination cursor
- `object`: string — Object
- `results`: array — List of results
- `type`: string — Resource type

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
