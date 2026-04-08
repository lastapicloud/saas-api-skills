---
name: notion-pages
description: "Complete Notion workspace management \u2014 pages, databases, blocks,\
  \ users, search, and comments with full query filtering, sorting, and rich content\
  \ support. Use when the user mentions notion, page, database, wiki, doc, note, workspace,\
  \ block, comment."
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
---

# Notion-Pages

Complete Notion workspace management — pages, databases, blocks, users, search, and comments with full query filtering, sorting, and rich content support. Use when the user mentions notion, page, database, wiki, doc, note, workspace, block, comment.

## API Endpoints

- **POST** `/pages` - Create a page (in a database or under another page)
- **GET** `/pages/{page_id}` - Retrieve a page and its properties
- **PATCH** `/pages/{page_id}` - Update page properties or archive a page
- **GET** `/blocks/{page_id}/children` - List all child blocks (content) of a page
- **POST** `/databases` - Create a database (as a child of a page)
- **GET** `/databases/{database_id}` - Retrieve a database schema and properties
- **PATCH** `/databases/{database_id}` - Update database title or properties
- **POST** `/databases/{database_id}/query` - Query a database with filters and sorts
- **GET** `/blocks/{block_id}` - Retrieve a single block
- **PATCH** `/blocks/{block_id}` - Update a block's content
- **DELETE** `/blocks/{block_id}` - Delete (archive) a block
- **GET** `/blocks/{block_id}/children` - List child blocks of a block
- **PATCH** `/blocks/{block_id}/children` - Append new child blocks to a page or block
- **GET** `/users` - List all users in the workspace
- **GET** `/users/{user_id}` - Retrieve a single user

## Actions

- create: Create a page (in a database or under another page) (POST /pages)
- get_by_id: Retrieve a page and its properties (GET /pages/{page_id})
- update: Update page properties or archive a page (PATCH /pages/{page_id})
- list: List all child blocks (content) of a page (GET /blocks/{page_id}/children)
- create_databases: Create a database (as a child of a page) (POST /databases)
- get_by_id_databases: Retrieve a database schema and properties (GET /databases/{database_id})
- update_databases: Update database title or properties (PATCH /databases/{database_id})
- query: Query a database with filters and sorts (POST /databases/{database_id}/query)
- get_by_id_blocks: Retrieve a single block (GET /blocks/{block_id})
- update_blocks: Update a block's content (PATCH /blocks/{block_id})
- delete: Delete (archive) a block (DELETE /blocks/{block_id})
- list_children: List child blocks of a block (GET /blocks/{block_id}/children)
- patch_children: Append new child blocks to a page or block (PATCH /blocks/{block_id}/children)
- list_users: List all users in the workspace (GET /users)
- get_by_id_users: Retrieve a single user (GET /users/{user_id})

## Fields

### Page (create / update)
- `parent`: object [REQUIRED for create] - Parent reference: `{"database_id": "uuid"}` or `{"page_id": "uuid"}`
- `properties`: object [REQUIRED for create] - Page properties matching the parent database schema (see property types below)
- `children`: array [OPTIONAL] - Array of block objects to add as page content on creation
- `icon`: object [OPTIONAL] - Page icon: `{"type": "emoji", "emoji": "icon"}` or `{"type": "external", "external": {"url": "..."}}`
- `cover`: object [OPTIONAL] - Cover image: `{"type": "external", "external": {"url": "..."}}`
- `archived`: boolean [OPTIONAL] - Set to `true` to archive (trash) the page

### Database Query (POST /databases/{id}/query)
- `filter`: object [OPTIONAL] - Filter conditions (see filter syntax below)
- `sorts`: array [OPTIONAL] - Sort conditions: `[{"property": "Name", "direction": "ascending"}]`
- `start_cursor`: string [OPTIONAL] - Cursor for pagination (from previous response `next_cursor`)
- `page_size`: integer [OPTIONAL] - Number of results per page (1-100, default 100)
- `filter_properties`: array [OPTIONAL] - List of property names to include in response (reduces payload)

### Database (create / update)
- `parent`: object [REQUIRED for create] - Must be `{"type": "page_id", "page_id": "uuid"}`
- `title`: array [REQUIRED for create] - Database title as rich text array
- `properties`: object [REQUIRED for create] - Property schema definitions (column definitions)
- `is_inline`: boolean [OPTIONAL] - Whether the database appears inline in the parent page

### Block (append children / update)
- `children`: array [REQUIRED for append] - Array of block objects to append
- `type`: string [REQUIRED for update] - Block type (paragraph, heading_1, etc.)
- `{type}`: object [REQUIRED for update] - Block type content object matching the type field

### Search
- `query`: string [OPTIONAL] - Search query text (searches titles only)
- `filter`: object [OPTIONAL] - Filter by object type: `{"property": "object", "value": "page"}` or `{"property": "object", "value": "database"}`
- `sort`: object [OPTIONAL] - Sort results: `{"direction": "ascending", "timestamp": "last_edited_time"}`
- `start_cursor`: string [OPTIONAL] - Pagination cursor
- `page_size`: integer [OPTIONAL] - Results per page (max 100)

### Comment (create)
- `parent`: object [REQUIRED] - Page to comment on: `{"page_id": "uuid"}`
- `rich_text`: array [REQUIRED] - Comment content as rich text array
- `discussion_id`: string [OPTIONAL] - Reply to an existing discussion thread instead of creating a new one

### Comment (list)
- `block_id`: string [REQUIRED, query param] - The page ID to list comments for
- `start_cursor`: string [OPTIONAL, query param] - Pagination cursor
- `page_size`: integer [OPTIONAL, query param] - Results per page (max 100)

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
