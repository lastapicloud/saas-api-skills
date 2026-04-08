---
name: anthropic-api
description: Generate text and manage conversations via Anthropic API. Use when the
  user mentions anthropic, claude, ai, llm, text generation, chat.
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
- create_batches: Create a message batch (POST /v1/messages/batches)
- get_by_id: Get batch status (GET /v1/messages/batches/{batch_id})
- list: List message batches (GET /v1/messages/batches)
- create_cancel: Cancel a batch (POST /v1/messages/batches/{batch_id}/cancel)
- create_count_tokens: Count tokens (POST /v1/messages/count_tokens)
- list_models: List available models (GET /v1/models)
- get_by_id_models: Get model details (GET /v1/models/{model_id})

## Fields

- `model`: string [REQUIRED for create]
- `messages`: array [REQUIRED for create]
- `max_tokens`: integer [REQUIRED for create]

## Example Request Bodies

**Create Message:**
```json
{"model": "claude-haiku-4-5", "messages": [{"role": "user", "content": "Summarize the benefits of cloud computing."}], "max_tokens": 1024}
```

**Count Tokens:**
```json
{"model": "claude-haiku-4-5", "messages": [{"role": "user", "content": "Hello, how are you?"}]}
```
