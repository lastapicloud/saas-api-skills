---
name: loops-email
description: Send transactional emails and manage contacts via Loops. Use when the
  user mentions loops, email, transactional email, contact, event.
version: 1.0.0
skill_type: external
base_url_env: LOOPS_BASE_URL
auth_env_var: LOOPS_API_KEY
auth_type: bearer
triggers:
  - loops
  - email
  - transactional email
  - contact
  - event
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LOOPS_BASE_URL and LOOPS_API_KEY environment variables.
---

# Loops-Email

Send transactional emails and manage contacts via Loops. Use when the user mentions loops, email, transactional email, contact, event.

## API Endpoints

- **POST** `/v1/transactional` - Send transactional email
- **POST** `/v1/contacts/create` - Create contact
- **PUT** `/v1/contacts/update` - Update contact
- **DELETE** `/v1/contacts/delete` - Delete contact
- **GET** `/v1/contacts/find` - Find contact
- **POST** `/v1/events/send` - Send event
- **GET** `/v1/mail-lists` - List mailing lists
- **GET** `/fmedatastreaming/TrafficLoopCount/TrafficLoopCounts.fmw` - Provides traffic loop counts for the input time interval. The LOOP_ID and DATETIME combinations are unique in the
- **GET** `/fmedatastreaming/TrafficLoopCount/TrafficLoops.fmw` - Provides all the traffic loops maintained by the City of Surrey in GeoJSON format. LANE_DIRECTION indicates the heading

## Actions

- create: Send transactional email (POST /v1/transactional)
- create_contacts: Create contact (POST /v1/contacts/create)
- put_update: Update contact (PUT /v1/contacts/update)
- delete_delete: Delete contact (DELETE /v1/contacts/delete)
- list: Find contact (GET /v1/contacts/find)
- create_send: Send event (POST /v1/events/send)
- list_mail_lists: List mailing lists (GET /v1/mail-lists)
- list_trafficloopcounts_fmw: Provides traffic loop counts for the input time interval. The LOOP_ID and DATETI (GET /fmedatastreaming/TrafficLoopCount/TrafficLoopCounts.fmw)
- list_trafficloops_fmw: Provides all the traffic loops maintained by the City of Surrey in GeoJSON forma (GET /fmedatastreaming/TrafficLoopCount/TrafficLoops.fmw)

## Fields

- `transactionalId`: string [REQUIRED for send]
- `email`: string [REQUIRED]
- `eventName`: string [REQUIRED for send_event]
- `dataVariables`: object [OPTIONAL]

## Example Request Bodies

**Send Transactional Email:**
```json
{"transactionalId": "txn-welcome-email", "email": "user@example.com", "dataVariables": {"firstName": "Alex", "activationUrl": "https://app.example.com/activate"}}
```

**Create Contact:**
```json
{"email": "newuser@example.com", "firstName": "Alex", "lastName": "Rivera", "source": "website"}
```
