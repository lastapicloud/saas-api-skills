---
name: bookstack-docs
description: 'Manage BookStack books, chapters, and pages. Use when the user mentions
  bookstack, book, chapter, page, wiki, documentation.

  '
version: 1.0.0
skill_type: external
base_url_env: BOOKSTACK_BASE_URL
auth_env_var: BOOKSTACK_TOKEN_SECRET
auth_type: header
triggers:
  - bookstack
  - book
  - chapter
  - page
  - wiki
  - documentation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BOOKSTACK_BASE_URL and BOOKSTACK_TOKEN_SECRET environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Bookstack-Docs

Manage BookStack books, chapters, and pages. Use when the user mentions bookstack, book, chapter, page, wiki, documentation.


## API Endpoints

- **GET** `/api/books` - List books
- **GET** `/api/books/{bookId}` - Get a book
- **POST** `/api/books` - Create a book
- **PUT** `/api/books/{bookId}` - Update a book
- **DELETE** `/api/books/{bookId}` - Delete a book
- **GET** `/api/chapters` - List chapters
- **POST** `/api/chapters` - Create a chapter
- **GET** `/api/pages` - List pages
- **POST** `/api/pages` - Create a page
- **PUT** `/api/pages/{pageId}` - Update a page

## Actions

- list: List books (GET /api/books)
- get_by_id: Get a book (GET /api/books/{bookId})
- create: Create a book (POST /api/books)
- update: Update a book (PUT /api/books/{bookId})
- delete: Delete a book (DELETE /api/books/{bookId})
- list_chapters: List chapters (GET /api/chapters)
- create_chapter: Create a chapter (POST /api/chapters)
- list_pages: List pages (GET /api/pages)
- create_page: Create a page (POST /api/pages)
- update_page: Update a page (PUT /api/pages/{pageId})

## Fields

- `name`: string [REQUIRED for create] — Display name
- `description`: string [OPTIONAL] — Human-readable description
- `book_id`: integer [REQUIRED for create chapter/page] — Book unique identifier
- `chapter_id`: integer [OPTIONAL for create page] — Chapter unique identifier
- `html`: string [OPTIONAL] (page content) — Html
- `markdown`: string [OPTIONAL] (page content) — Markdown

## Example Request Bodies

**Create Book:**
```json
{"name": "Developer Guide", "description": "A comprehensive guide for developers"}
```

**Create Page:**
```json
{"name": "Installation", "book_id": 1, "html": "Follow these steps to install."}

## Response

**Book object:**
- `id`: string — Unique book identifier
- `name`: string — Book name or title
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
