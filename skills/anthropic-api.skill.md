---
name: anthropic-api
description: 'Generate text and manage conversations via Anthropic API. Use when the
  user mentions anthropic, claude, ai, llm, text generation, chat.

  '
version: 1.0.0
skill_type: external
base_url_env: ANTHROPIC_API_BASE_URL
auth_env_var: ANTHROPIC_API_KEY
auth_type: header
triggers:
  - anthropic
  - claude
  - ai
  - llm
  - text generation
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ANTHROPIC_API_BASE_URL and ANTHROPIC_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Anthropic-Api

Generate text and manage conversations via Anthropic API. Use when the user mentions anthropic, claude, ai, llm, text generation, chat.


## API Endpoints

- **POST** `/v1/messages` - Create a message
- **POST** `/v1/messages/batches` - Create a message batch
- **GET** `/v1/messages/batches/{batch_id}` - Get batch status
- **GET** `/v1/messages/batches` - List message batches
- **POST** `/v1/messages/batches/{batch_id}/cancel` - Cancel a batch
- **POST** `/v1/messages/count_tokens` - Count tokens
- **GET** `/v1/models` - List available models
- **GET** `/v1/models/{model_id}` - Get model details

## Actions

- create: Create a message (POST /v1/messages)
- create_message_batch: Create a message batch (POST /v1/messages/batches)
- get_by_id: Get batch status (GET /v1/messages/batches/{batch_id})
- list: List message batches (GET /v1/messages/batches)
- cancel_batch: Cancel a batch (POST /v1/messages/batches/{batch_id}/cancel)
- create_count_tokens: Count tokens (POST /v1/messages/count_tokens)
- list_available_models: List available models (GET /v1/models)
- get_model_details: Get model details (GET /v1/models/{model_id})

## Fields

- `model`: string [REQUIRED for create] — Model
- `messages`: array [REQUIRED for create] — List of messages
- `max_tokens`: integer [REQUIRED for create] — Max Tokens value

## Example Request Bodies

**Create Message:**
```json
{"model": "claude-haiku-4-5", "messages": [{"role": "user", "content": "Summarize the benefits of cloud computing."}], "max_tokens": 1024}
```

**Count Tokens:**
```json
{"model": "claude-haiku-4-5", "messages": [{"role": "user", "content": "Hello, how are you?"}]}
```

## Response

**Batche object:**
- `id`: string — Unique batche identifier
- `name`: string — Batche name or title
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
