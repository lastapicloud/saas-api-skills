---
name: mailchimp-marketing
description: 'Manage audiences, campaigns, and email marketing in Mailchimp. Use when
  the user mentions mailchimp, email marketing, campaign, audience, list, subscriber,
  newsletter.

  '
version: 1.0.0
skill_type: external
base_url_env: MAILCHIMP_BASE_URL
auth_env_var: MAILCHIMP_API_KEY
auth_type: basic
triggers:
  - mailchimp
  - email marketing
  - campaign
  - audience
  - list
  - subscriber
  - newsletter
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAILCHIMP_BASE_URL and MAILCHIMP_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Mailchimp-Marketing

Manage audiences, campaigns, and email marketing in Mailchimp. Use when the user mentions mailchimp, email marketing, campaign, audience, list, subscriber, newsletter.


## API Endpoints

- **GET** `/lists` - List audiences (lists)
- **POST** `/lists` - Create an audience
- **GET** `/lists/{list_id}/members` - List audience members
- **POST** `/lists/{list_id}/members` - Add a member to an audience
- **GET** `/lists/{list_id}/members/{subscriber_hash}` - Get a member
- **PATCH** `/lists/{list_id}/members/{subscriber_hash}` - Update a member
- **DELETE** `/lists/{list_id}/members/{subscriber_hash}` - Archive (delete) a member
- **GET** `/campaigns` - List campaigns
- **POST** `/campaigns` - Create a campaign
- **POST** `/campaigns/{campaign_id}/actions/send` - Send a campaign
- **POST** `/campaigns/{campaign_id}/actions/cancel_send` - Cancel a campaign
- **POST** `/campaigns/{campaign_id}/actions/pause` - Pause an automated campaign
- **POST** `/campaigns/{campaign_id}/actions/replicate` - Replicate a campaign
- **DELETE** `/campaigns/{campaign_id}` - Delete a campaign
- **GET** `/reports` - List campaign reports

## Actions

- list: List audiences (lists) (GET /lists)
- create: Create an audience (POST /lists)
- list_audience_members: List audience members (GET /lists/{list_id}/members)
- add_member_audience: Add a member to an audience (POST /lists/{list_id}/members)
- get_by_id: Get a member (GET /lists/{list_id}/members/{subscriber_hash})
- update: Update a member (PATCH /lists/{list_id}/members/{subscriber_hash})
- delete: Archive (delete) a member (DELETE /lists/{list_id}/members/{subscriber_hash})
- list_campaigns: List campaigns (GET /campaigns)
- create_campaign: Create a campaign (POST /campaigns)
- send_campaign: Send a campaign (POST /campaigns/{campaign_id}/actions/send)
- cancel_campaign: Cancel a campaign (POST /campaigns/{campaign_id}/actions/cancel_send)
- create_pause_automated_campaign: Pause an automated campaign (POST /campaigns/{campaign_id}/actions/pause)
- create_replicate_campaign: Replicate a campaign (POST /campaigns/{campaign_id}/actions/replicate)
- delete_campaign: Delete a campaign (DELETE /campaigns/{campaign_id})
- list_campaign_reports: List campaign reports (GET /reports)

## Fields

- `list_id`: string [REQUIRED for audience-scoped actions] (audience/list ID) — List unique identifier
- `campaign_id`: string [REQUIRED for send_campaign] (campaign ID) — Campaign unique identifier
- `email_address`: string [REQUIRED for add_member] (subscriber email) — Email physical or postal address
- `status`: string [REQUIRED for add_member] (subscribed, unsubscribed, cleaned, pending) — Current status
- `merge_fields`: object [OPTIONAL for add_member] (merge fields like FNAME, LNAME) — Merge Fields configuration
- `name`: string [REQUIRED for create_audience] (audience name) — Display name
- `type`: string [REQUIRED for create_campaign] (regular, plaintext, absplit, rss) — Resource type
- `recipients`: object [REQUIRED for create_campaign] (audience targeting with list_id) — Recipients configuration
- `settings`: object [REQUIRED for create_campaign] (subject_line, from_name, reply_to) — Settings configuration
- `count`: integer [OPTIONAL] (results per page) — Count value
- `offset`: integer [OPTIONAL] (pagination offset) — Pagination offset

## Example Request Bodies

**Add Member:**
```json
{"email_address": "user@example.com", "status": "subscribed", "merge_fields": {"FNAME": "Jane", "LNAME": "Doe"}}
```

**Create Campaign:**
```json
{"type": "regular", "recipients": {"list_id": "abc123"}, "settings": {"subject_line": "Monthly Newsletter", "from_name": "My Company", "reply_to": "info@example.com"}}
```

## Response

**Member object:**
- `id`: string — Unique member identifier
- `name`: string — Member name or title
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
