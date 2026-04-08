---
name: ringcentral-communications
description: Manage RingCentral calls, messages, and meetings. Use when the user mentions
  ringcentral, call, phone, SMS, meeting, fax.
version: 1.0.0
skill_type: external
base_url_env: RINGCENTRAL_BASE_URL
auth_env_var: RINGCENTRAL_ACCESS_TOKEN
auth_type: bearer
triggers:
  - ringcentral
  - call
  - phone
  - SMS
  - meeting
  - fax
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RINGCENTRAL_BASE_URL and RINGCENTRAL_ACCESS_TOKEN environment
  variables.
---

# Ringcentral-Communications

Manage RingCentral calls, messages, and meetings. Use when the user mentions ringcentral, call, phone, SMS, meeting, fax.

## API Endpoints

- **POST** `/restapi/v1.0/account/~/extension/~/sms` - Send SMS
- **GET** `/restapi/v1.0/account/~/extension/~/message-store` - List messages
- **POST** `/restapi/v1.0/account/~/extension/~/ringout` - Make a call (RingOut)
- **GET** `/restapi/v1.0/account/~/extension/~/call-log` - Get call log
- **GET** `/restapi/v1.0/account/~/extension/~` - Get extension info
- **GET** `/restapi/v1.0/account/~/extension` - List extensions
- **POST** `/restapi/v1.0/account/~/extension/~/meeting` - Create a meeting
- **GET** `/restapi/v1.0/account/~/extension/~/meeting` - List meetings
- **GET** `/restapi/v1.0/account/~` - Get account info
- **GET** `/restapi/v1.0/account/~/extension/~/presence` - Get presence
- **PUT** `/restapi/v1.0/account/~/extension/~/meeting/{meetingId}` - Update meeting
- **DELETE** `/restapi/v1.0/account/~/extension/~/meeting/{meetingId}` - Delete meeting
- **PUT** `/restapi/v1.0/account/~/extension/~/presence` - Update presence

## Actions

- create: Send SMS (POST /restapi/v1.0/account/~/extension/~/sms)
- list: List messages (GET /restapi/v1.0/account/~/extension/~/message-store)
- create_ringout: Make a call (RingOut) (POST /restapi/v1.0/account/~/extension/~/ringout)
- list_call_log: Get call log (GET /restapi/v1.0/account/~/extension/~/call-log)
- list_extension: Get extension info (GET /restapi/v1.0/account/~/extension/~)
- list_extension_2: List extensions (GET /restapi/v1.0/account/~/extension)
- create_meeting: Create a meeting (POST /restapi/v1.0/account/~/extension/~/meeting)
- list_meeting: List meetings (GET /restapi/v1.0/account/~/extension/~/meeting)
- list_account: Get account info (GET /restapi/v1.0/account/~)
- list_presence: Get presence (GET /restapi/v1.0/account/~/extension/~/presence)
- update: Update meeting (PUT /restapi/v1.0/account/~/extension/~/meeting/{meetingId})
- delete: Delete meeting (DELETE /restapi/v1.0/account/~/extension/~/meeting/{meetingId})
- put_presence: Update presence (PUT /restapi/v1.0/account/~/extension/~/presence)

## Fields

- `from`: object [REQUIRED for SMS] with `phoneNumber`
- `to`: array [REQUIRED for SMS] with `phoneNumber`
- `text`: string [REQUIRED for SMS]
- `topic`: string [REQUIRED for meeting]
- `meetingType`: string [OPTIONAL] ("Scheduled", "Instant", "Recurring")

## Example Request Bodies

**Send SMS:**
```json
{"from": {"phoneNumber": "+15551234567"}, "to": [{"phoneNumber": "+15559876543"}], "text": "Hello from RingCentral!"}
```

**Create Meeting:**
```json
{"topic": "Weekly Standup", "meetingType": "Scheduled"}
```
