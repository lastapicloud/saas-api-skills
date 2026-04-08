---
name: clickhouse-analytics
description: Analytics database via ClickHouse. Use when the user mentions clickhouse, OLAP, analytics database, columnar database, real-time analytics.
version: 1.0.0
skill_type: external
base_url_env: CLICKHOUSE_BASE_URL
auth_env_var: CLICKHOUSE_API_KEY
auth_type: basic
triggers:
  - clickhouse
  - OLAP
  - analytics database
  - columnar database
  - real-time analytics
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://clickhouse.com/docs/interfaces/http
---

# Clickhouse-Analytics

Analytics database via ClickHouse. Use when the user mentions clickhouse, OLAP, analytics database, columnar database, real-time analytics.

## API Endpoints

- **POST** `/query` - Execute query
- **GET** `/query` - Execute query (GET)
- **POST** `/ping` - Health check
- **GET** `/stat` - Get statistics
- **POST** `/tables/{database}/{table}/insert` - Insert data
- **GET** `/tables/{database}/{table}/data` - Get table data

## Actions

- execute_query: Execute query (POST /query)
- ping: Health check (POST /ping)
- get_stats: Get statistics (GET /stat)
- insert_data: Insert data (POST /tables/{database}/{table}/insert)
- get_table_data: Get table data (GET /tables/{database}/{table}/data)

## Fields

- `query`: string [REQUIRED] - SQL query
- `database`: string [REQUIRED for table ops] - Database name
- `table`: string [REQUIRED for table ops] - Table name
- `data`: array [REQUIRED for insert] - Data to insert
- `format`: string [OPTIONAL] - Output format (JSON, CSV, etc.)

## Example Request Bodies

**Execute Query:**
```json
{"query": "SELECT count() FROM events", "format": "JSON"}
```

**Insert Data:**
```json
{"data": [{"event": "click", "timestamp": "2024-01-01 10:00:00"}]}
```

**With Parameters:**
```json
{"query": "SELECT * FROM users WHERE created_at > {start_date:DateTime}"}
```
