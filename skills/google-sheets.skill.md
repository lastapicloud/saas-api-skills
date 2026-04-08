---
name: google-sheets
description: Read, write, and manage Google Sheets spreadsheets. Use when the user
  mentions sheets, spreadsheet, google sheets, cells, rows, columns.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_SHEETS_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - sheets
  - spreadsheet
  - google sheets
  - cells
  - rows
  - columns
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_SHEETS_BASE_URL and GOOGLE_API_TOKEN environment variables.
---

# Google-Sheets

Read, write, and manage Google Sheets spreadsheets. Use when the user mentions sheets, spreadsheet, google sheets, cells, rows, columns.

## API Endpoints

- **GET** `/spreadsheets/{spreadsheetId}` - Get spreadsheet metadata
- **GET** `/spreadsheets/{spreadsheetId}/sheets` - List sheets in a spreadsheet
- **GET** `/spreadsheets/{spreadsheetId}/values/{range}` - Read a range of cells
- **PUT** `/spreadsheets/{spreadsheetId}/values/{range}` - Write values to a range
- **POST** `/spreadsheets/{spreadsheetId}/values/{range}:append` - Append rows to a sheet
- **POST** `/spreadsheets` - Create a new spreadsheet
- **POST** `/spreadsheets/{spreadsheetId}/values/{range}:clear` - Clear a range of cells
- **POST** `/v4/spreadsheets/{spreadsheetId}:batchUpdate`
- **POST** `/v4/spreadsheets`
- **GET** `/v4/spreadsheets/{spreadsheetId}`
- **POST** `/v4/spreadsheets/{spreadsheetId}:getByDataFilter`
- **GET** `/v4/spreadsheets/{spreadsheetId}/developerMetadata/{metadataId}`
- **POST** `/v4/spreadsheets/{spreadsheetId}/developerMetadata:search`
- **POST** `/v4/spreadsheets/{spreadsheetId}/sheets/{sheetId}:copyTo`
- **POST** `/v4/spreadsheets/{spreadsheetId}/values/{range}:append`

## Actions

- get_by_id: Get spreadsheet metadata (GET /spreadsheets/{spreadsheetId})
- list: List sheets in a spreadsheet (GET /spreadsheets/{spreadsheetId}/sheets)
- get_by_id_values: Read a range of cells (GET /spreadsheets/{spreadsheetId}/values/{range})
- update: Write values to a range (PUT /spreadsheets/{spreadsheetId}/values/{range})
- create: Append rows to a sheet (POST /spreadsheets/{spreadsheetId}/values/{range}:append)
- create_spreadsheets: Create a new spreadsheet (POST /spreadsheets)
- create_values: Clear a range of cells (POST /spreadsheets/{spreadsheetId}/values/{range}:clear)
- create_spreadsheets_2: POST /v4/spreadsheets/{spreadsheetId}:batchUpdate (POST /v4/spreadsheets/{spreadsheetId}:batchUpdate)
- create_spreadsheets_3: POST /v4/spreadsheets (POST /v4/spreadsheets)
- get_by_id_spreadsheets: GET /v4/spreadsheets/{spreadsheetId} (GET /v4/spreadsheets/{spreadsheetId})
- create_spreadsheets_4: POST /v4/spreadsheets/{spreadsheetId}:getByDataFilter (POST /v4/spreadsheets/{spreadsheetId}:getByDataFilter)
- get_by_id_developermetadata: GET /v4/spreadsheets/{spreadsheetId}/developerMetadata/{metadataId} (GET /v4/spreadsheets/{spreadsheetId}/developerMetadata/{metadataId})
- search: POST /v4/spreadsheets/{spreadsheetId}/developerMetadata:search (POST /v4/spreadsheets/{spreadsheetId}/developerMetadata:search)
- create_sheets: POST /v4/spreadsheets/{spreadsheetId}/sheets/{sheetId}:copyTo (POST /v4/spreadsheets/{spreadsheetId}/sheets/{sheetId}:copyTo)
- create_values_2: POST /v4/spreadsheets/{spreadsheetId}/values/{range}:append (POST /v4/spreadsheets/{spreadsheetId}/values/{range}:append)

## Fields

- `spreadsheetId`: string [REQUIRED for all except create_spreadsheet] (the spreadsheet ID)
- `range`: string [REQUIRED for read_range, write_range, append_rows, clear_range] (A1 notation, e.g. "Sheet1!A1:D5")
- `title`: string [REQUIRED for create_spreadsheet] (spreadsheet title)
- `values`: array of arrays [REQUIRED for write_range, append_rows] (row data)
- `valueInputOption`: string [OPTIONAL] (RAW or USER_ENTERED, default USER_ENTERED)

## Example Request Bodies

**Write Range:**
```json
{"values": [["Name", "Age"], ["Alice", 30], ["Bob", 25]], "valueInputOption": "USER_ENTERED"}
```

**Create Spreadsheet:**
```json
{"properties": {"title": "My New Spreadsheet"}}
```

**Read Range (Query Params):**
Query parameter: `valueRenderOption=FORMATTED_VALUE`
