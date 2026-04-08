---
name: mailchimp-marketing
description: Manage audiences, campaigns, and email marketing in Mailchimp. Use when
  the user mentions mailchimp, email marketing, campaign, audience, list, subscriber,
  newsletter.
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
- **GET** `/reports/{campaign_id}` - Get campaign report

## Actions

- list: List audiences (lists) (GET /lists)
- create: Create an audience (POST /lists)
- list_members: List audience members (GET /lists/{list_id}/members)
- create_members: Add a member to an audience (POST /lists/{list_id}/members)
- get_by_id_members: Get a member (GET /lists/{list_id}/members/{subscriber_hash})
- update_members: Update a member (PATCH /lists/{list_id}/members/{subscriber_hash})
- delete_members: Archive (delete) a member (DELETE /lists/{list_id}/members/{subscriber_hash})
- list_campaigns: List campaigns (GET /campaigns)
- create_campaigns: Create a campaign (POST /campaigns)
- create_send: Send a campaign (POST /campaigns/{campaign_id}/actions/send)
- create_cancel_send: Cancel a campaign (POST /campaigns/{campaign_id}/actions/cancel_send)
- create_pause: Pause an automated campaign (POST /campaigns/{campaign_id}/actions/pause)
- create_replicate: Replicate a campaign (POST /campaigns/{campaign_id}/actions/replicate)
- delete_campaigns: Delete a campaign (DELETE /campaigns/{campaign_id})
- list_reports: List campaign reports (GET /reports)
- get_by_id_reports: Get campaign report (GET /reports/{campaign_id})

## Fields

- `list_id`: string [REQUIRED for audience-scoped actions] (audience/list ID)
- `campaign_id`: string [REQUIRED for send_campaign] (campaign ID)
- `email_address`: string [REQUIRED for add_member] (subscriber email)
- `status`: string [REQUIRED for add_member] (subscribed, unsubscribed, cleaned, pending)
- `merge_fields`: object [OPTIONAL for add_member] (merge fields like FNAME, LNAME)
- `name`: string [REQUIRED for create_audience] (audience name)
- `type`: string [REQUIRED for create_campaign] (regular, plaintext, absplit, rss)
- `recipients`: object [REQUIRED for create_campaign] (audience targeting with list_id)
- `settings`: object [REQUIRED for create_campaign] (subject_line, from_name, reply_to)
- `count`: integer [OPTIONAL] (results per page)
- `offset`: integer [OPTIONAL] (pagination offset)

## Example Request Bodies

**Add Member:**
```json
{"email_address": "user@example.com", "status": "subscribed", "merge_fields": {"FNAME": "Jane", "LNAME": "Doe"}}
```

**Create Campaign:**
```json
{"type": "regular", "recipients": {"list_id": "abc123"}, "settings": {"subject_line": "Monthly Newsletter", "from_name": "My Company", "reply_to": "info@example.com"}}
```
