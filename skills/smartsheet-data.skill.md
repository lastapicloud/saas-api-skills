---
name: smartsheet-data
description: Manage Smartsheet sheets, rows, and columns. Use when the user mentions
  smartsheet, sheet, row, column, workspace.
version: 1.0.0
skill_type: external
base_url_env: SMARTSHEET_BASE_URL
auth_env_var: SMARTSHEET_ACCESS_TOKEN
auth_type: bearer
triggers:
  - smartsheet
  - sheet
  - row
  - column
  - workspace
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SMARTSHEET_BASE_URL and SMARTSHEET_ACCESS_TOKEN environment
  variables.
---

# Smartsheet-Data

Manage Smartsheet sheets, rows, and columns. Use when the user mentions smartsheet, sheet, row, column, workspace.

## API Endpoints

- **GET** `/2.0/sheets` - List sheets
- **GET** `/2.0/sheets/{sheetId}` - Get a sheet
- **POST** `/2.0/sheets` - Create a sheet
- **DELETE** `/2.0/sheets/{sheetId}` - Delete a sheet
- **GET** `/2.0/sheets/{sheetId}/rows` - List rows
- **POST** `/2.0/sheets/{sheetId}/rows` - Add rows
- **PUT** `/2.0/sheets/{sheetId}/rows` - Update rows
- **DELETE** `/2.0/sheets/{sheetId}/rows` - Delete rows
- **GET** `/2.0/sheets/{sheetId}/columns` - List columns
- **POST** `/2.0/sheets/{sheetId}/columns` - Add columns

## Actions

- list: List sheets (GET /2.0/sheets)
- get_by_id: Get a sheet (GET /2.0/sheets/{sheetId})
- create: Create a sheet (POST /2.0/sheets)
- delete: Delete a sheet (DELETE /2.0/sheets/{sheetId})
- list_rows: List rows (GET /2.0/sheets/{sheetId}/rows)
- create_rows: Add rows (POST /2.0/sheets/{sheetId}/rows)
- put_rows: Update rows (PUT /2.0/sheets/{sheetId}/rows)
- delete_rows: Delete rows (DELETE /2.0/sheets/{sheetId}/rows)
- list_columns: List columns (GET /2.0/sheets/{sheetId}/columns)
- create_columns: Add columns (POST /2.0/sheets/{sheetId}/columns)

## Fields

- `name`: string [REQUIRED for create sheet]
- `columns`: array [REQUIRED for create sheet] with `title`, `type`, `primary`
- `cells`: array [REQUIRED for add rows] with `columnId`, `value`
- `toTop`: boolean [OPTIONAL for add rows]
- `toBottom`: boolean [OPTIONAL for add rows]

## Example Request Bodies

**Create Sheet:**
```json
{"name": "Project Tracker", "columns": [{"title": "Task", "type": "TEXT_NUMBER", "primary": true}, {"title": "Status", "type": "PICKLIST"}]}
```

**Add Rows:**
```json
[{"toBottom": true, "cells": [{"columnId": 1234567890, "value": "Design homepage"}, {"columnId": 1234567891, "value": "In Progress"}]}]
```
