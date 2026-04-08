---
name: googleanalytics-data
description: Query Google Analytics 4 reports and real-time data. Use when the user
  mentions google analytics, GA4, analytics, report, metrics, dimensions.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_ANALYTICS_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - google analytics
  - GA4
  - analytics
  - report
  - metrics
  - dimensions
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_ANALYTICS_BASE_URL and GOOGLE_API_TOKEN environment
  variables.
---

# Googleanalytics-Data

Query Google Analytics 4 reports and real-time data. Use when the user mentions google analytics, GA4, analytics, report, metrics, dimensions.

## API Endpoints

- **POST** `/v1beta/properties/{propertyId}:runReport` - Run a report
- **POST** `/v1beta/properties/{propertyId}:runRealtimeReport` - Run real-time report
- **POST** `/v1beta/properties/{propertyId}:batchRunReports` - Batch run reports
- **POST** `/v1beta/properties/{propertyId}:runPivotReport` - Run pivot report
- **GET** `/v1beta/properties/{propertyId}/metadata` - Get metadata
- **GET** `/v1beta/accountSummaries` - List account summaries
- **GET** `/v1beta/properties` - List properties
- **POST** `/v1beta/properties/{propertyId}:checkCompatibility` - Check metric/dimension compatibility

## Actions

- create: Run a report (POST /v1beta/properties/{propertyId}:runReport)
- create_properties: Run real-time report (POST /v1beta/properties/{propertyId}:runRealtimeReport)
- create_properties_2: Batch run reports (POST /v1beta/properties/{propertyId}:batchRunReports)
- create_properties_3: Run pivot report (POST /v1beta/properties/{propertyId}:runPivotReport)
- list: Get metadata (GET /v1beta/properties/{propertyId}/metadata)
- list_accountsummaries: List account summaries (GET /v1beta/accountSummaries)
- list_properties: List properties (GET /v1beta/properties)
- create_properties_4: Check metric/dimension compatibility (POST /v1beta/properties/{propertyId}:checkCompatibility)

## Fields

- `dateRanges`: array [REQUIRED for report] with `startDate`, `endDate`
- `metrics`: array [REQUIRED] with `name` (e.g., "activeUsers", "sessions")
- `dimensions`: array [OPTIONAL] with `name` (e.g., "country", "browser")
- `dimensionFilter`: object [OPTIONAL]
- `metricFilter`: object [OPTIONAL]
- `limit`: integer [OPTIONAL]

## Example Request Bodies

**Run Report:**
```json
{"dateRanges": [{"startDate": "2024-01-01", "endDate": "2024-01-31"}], "metrics": [{"name": "activeUsers"}], "dimensions": [{"name": "country"}], "limit": 10}
```

**Run Real-Time Report:**
```json
{"metrics": [{"name": "activeUsers"}], "dimensions": [{"name": "city"}]}
```
