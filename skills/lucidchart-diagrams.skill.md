---
name: lucidchart-diagrams
description: Create and manage diagrams, flowcharts, and visual documents via Lucidchart. Use when the user mentions lucidchart, diagram, flowchart, org chart, visual, chart.
version: 1.0.0
skill_type: external
base_url_env: LUCIDCHART_BASE_URL
auth_env_var: LUCIDCHART_API_TOKEN
auth_type: bearer
triggers:
  - lucidchart
  - diagram
  - flowchart
  - org chart
  - visual
  - chart
  - lucid
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  api_version: "1.0"
---

# Lucidchart-Diagrams

Create and manage diagrams, flowcharts, and visual documents via Lucidchart. Use when the user mentions lucidchart, diagram, flowchart, org chart, visual, chart.

## API Endpoints

- **POST** `/documents` - Create a new document
- **GET** `/documents/{id}` - Get document information
- **GET** `/documents/{id}/contents` - Get document contents
- **PUT** `/documents/{id}` - Update a document
- **DELETE** `/documents/{id}` - Delete a document
- **GET** `/documents` - List documents
- **GET** `/documents/{id}/export` - Export document as image (PNG/JPEG)

## Actions

- create: Create a new document (POST /documents)
- get_by_id: Get document information (GET /documents/{id})
- get_contents: Get document contents (GET /documents/{id}/contents)
- update: Update a document (PUT /documents/{id})
- delete: Delete a document (DELETE /documents/{id})
- list: List documents (GET /documents)
- export: Export document as image (GET /documents/{id}/export)

## Fields

- `title`: string [REQUIRED] - Document title
- `product`: string [REQUIRED] - Product type (lucidchart, lucidspark, or lucidscale)
- `parent`: integer [OPTIONAL] - Folder ID to create document in

## Example Request Bodies

**Create Document:**
```json
{"title": "My Flowchart", "product": "lucidchart"}
```

**Update Document:**
```json
{"title": "Updated Flowchart"}
```

**Export Document (GET with Accept header):**
```
Accept: image/png
```
