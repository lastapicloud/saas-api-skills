---
name: livechat-support
description: Manage chats, agents, and customers via LiveChat. Use when the user mentions
  livechat, chat, agent, visitor, customer, support.
version: 1.0.0
skill_type: external
base_url_env: LIVECHAT_BASE_URL
auth_env_var: LIVECHAT_API_TOKEN
auth_type: bearer
triggers:
  - livechat
  - chat
  - agent
  - visitor
  - customer
  - support
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LIVECHAT_BASE_URL and LIVECHAT_API_TOKEN environment variables.
---

# Livechat-Support

Manage chats, agents, and customers via LiveChat. Use when the user mentions livechat, chat, agent, visitor, customer, support.

## API Endpoints

- **GET** `/v3.5/chats` - List chats
- **GET** `/v3.5/chats/{chat_id}` - Get chat
- **POST** `/v3.5/chats/start_chat` - Start chat
- **POST** `/v3.5/chats/{chat_id}/send_event` - Send event
- **POST** `/v3.5/chats/{chat_id}/close` - Close chat
- **GET** `/v3.5/agents` - List agents
- **GET** `/v3.5/agents/{agent_id}` - Get agent
- **POST** `/v3.5/agents` - Create agent
- **PUT** `/v3.5/agents/{agent_id}` - Update agent
- **DELETE** `/v3.5/agents/{agent_id}` - Delete agent
- **GET** `/v3.5/groups` - List groups
- **POST** `/v3.5/groups` - Create group
- **PUT** `/v3.5/groups/{group_id}` - Update group
- **DELETE** `/v3.5/groups/{group_id}` - Delete group
- **GET** `/v3.5/customers` - List customers

## Actions

- list: List chats (GET /v3.5/chats)
- get_by_id: Get chat (GET /v3.5/chats/{chat_id})
- create: Start chat (POST /v3.5/chats/start_chat)
- create_send_event: Send event (POST /v3.5/chats/{chat_id}/send_event)
- create_close: Close chat (POST /v3.5/chats/{chat_id}/close)
- list_agents: List agents (GET /v3.5/agents)
- get_by_id_agents: Get agent (GET /v3.5/agents/{agent_id})
- create_agent: Create agent (POST /v3.5/agents)
- update_agent: Update agent (PUT /v3.5/agents/{agent_id})
- delete_agent: Delete agent (DELETE /v3.5/agents/{agent_id})
- list_groups: List groups (GET /v3.5/groups)
- create_group: Create group (POST /v3.5/groups)
- update_group: Update group (PUT /v3.5/groups/{group_id})
- delete_group: Delete group (DELETE /v3.5/groups/{group_id})
- list_customers: List customers (GET /v3.5/customers)

## Fields

- `chat_id`: string [REQUIRED for get/close/send_event] (chat identifier)
- `agent_id`: string [REQUIRED for get/update/delete agent] (agent identifier)
- `group_id`: integer [REQUIRED for get/update/delete group] (group identifier)
- `type`: string [REQUIRED for send_event] (message, file, etc.)
- `text`: string [REQUIRED for message events]
- `name`: string [REQUIRED for create agent] (agent name)
- `role`: string [OPTIONAL for create/update agent] (viceowner, administrator, normal)
- `id`: string [REQUIRED for create agent/group] (agent/group ID)

## Example Request Bodies

**Create Agent:**
```json
{"id": "agent@example.com", "name": "Agent Smith", "role": "normal"}
```

**Update Agent:**
```json
{"id": "agent@example.com", "role": "administrator", "job_title": "Support Lead"}
```

**Create Group:**
```json
{"id": 1, "name": "Support Team", "language": "en"}
```

**Send Event (Message):**
```json
{"type": "message", "text": "Hello! How can I help you today?"}
```

**Start Chat:**
```json
{"users": [{"email": "agent@example.com", "agent": true}], "thread": {"events": [{"type": "message", "text": "Welcome to support!"}]}}
```
