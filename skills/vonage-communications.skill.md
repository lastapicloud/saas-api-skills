---
name: vonage-communications
description: Send SMS and manage Vonage messaging. Use when the user mentions vonage,
  nexmo, SMS, message, voice, verify.
version: 1.0.0
skill_type: external
base_url_env: VONAGE_BASE_URL
auth_env_var: VONAGE_API_SECRET
auth_user_env: VONAGE_API_KEY
auth_type: basic
triggers:
  - vonage
  - nexmo
  - SMS
  - message
  - voice
  - verify
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires VONAGE_BASE_URL and VONAGE_API_SECRET environment variables.
---

# Vonage-Communications

Send SMS and manage Vonage messaging. Use when the user mentions vonage, nexmo, SMS, message, voice, verify.

## API Endpoints

- **POST** `/v1/messages` - Send a message (SMS, WhatsApp, etc.)
- **POST** `/sms/json` - Send SMS (legacy)
- **POST** `/v1/calls` - Create a call
- **GET** `/v1/calls` - List calls
- **GET** `/v1/calls/{callId}` - Get a call
- **POST** `/verify/json` - Start verification
- **POST** `/verify/check/json` - Check verification
- **GET** `/accounts/{apiKey}/balance` - Get account balance
- **GET** `/accounts/{apiKey}/numbers` - List numbers
- **POST** `/number/buy` - Buy a number
- **GET** `/api/accounts/{account_id}` - Get account data by ID
- **GET** `/api/accounts/{account_id}/locations` - Get account locations data by account ID
- **GET** `/api/accounts/{account_id}/locations/{location_id}` - Get location data by account ID and location ID
- **GET** `/self` - User info
- **POST** `/self/calls` - Place a call

## Actions

- create: Send a message (SMS, WhatsApp, etc.) (POST /v1/messages)
- create_json: Send SMS (legacy) (POST /sms/json)
- create_calls: Create a call (POST /v1/calls)
- list: List calls (GET /v1/calls)
- get_by_id: Get a call (GET /v1/calls/{callId})
- create_json_2: Start verification (POST /verify/json)
- create_json_3: Check verification (POST /verify/check/json)
- list_balance: Get account balance (GET /accounts/{apiKey}/balance)
- list_numbers: List numbers (GET /accounts/{apiKey}/numbers)
- create_buy: Buy a number (POST /number/buy)
- get_by_id_accounts: Get account data by ID (GET /api/accounts/{account_id})
- list_locations: Get account locations data by account ID (GET /api/accounts/{account_id}/locations)
- get_by_id_locations: Get location data by account ID and location ID (GET /api/accounts/{account_id}/locations/{location_id})
- list_self: User info (GET /self)
- create_calls_2: Place a call (POST /self/calls)

## Fields

- `from`: string [REQUIRED] (sender number or name)
- `to`: string [REQUIRED] (recipient number)
- `text`: string [REQUIRED for SMS]
- `channel`: string [REQUIRED for v1/messages] ("sms", "whatsapp", "viber_service")
- `message_type`: string [REQUIRED for v1/messages] ("text", "image")
- `number`: string [REQUIRED for verify]
- `brand`: string [REQUIRED for verify]

## Example Request Bodies

**Send Message (v1):**
```json
{"from": "14155550100", "to": "14155550101", "channel": "sms", "message_type": "text", "text": "Your verification code is 123456"}
```

**Start Verification:**
```json
{"number": "14155550101", "brand": "MyApp"}
```
