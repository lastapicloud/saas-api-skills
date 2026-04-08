---
name: fireworks-ai
description: Generate text and embeddings via Fireworks AI. Use when the user mentions
  fireworks, fireworks ai, llm, text generation, embedding, inference.
version: 1.0.0
skill_type: external
base_url_env: FIREWORKS_AI_BASE_URL
auth_env_var: FIREWORKS_AI_API_KEY
auth_type: bearer
triggers:
  - fireworks
  - fireworks ai
  - llm
  - text generation
  - embedding
  - inference
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FIREWORKS_AI_BASE_URL and FIREWORKS_AI_API_KEY environment
  variables.
---

# Fireworks-Ai

Generate text and embeddings via Fireworks AI. Use when the user mentions fireworks, fireworks ai, llm, text generation, embedding, inference.

## API Endpoints

- **POST** `/inference/v1/chat/completions` - Create chat completion
- **POST** `/inference/v1/completions` - Create completion
- **POST** `/inference/v1/embeddings` - Create embeddings
- **GET** `/v1/models` - List models
- **GET** `/v1/models/{model_id}` - Get model
- **POST** `/inference/v1/image/generations` - Generate image

## Actions

- create: Create chat completion (POST /inference/v1/chat/completions)
- create_completions: Create completion (POST /inference/v1/completions)
- create_embeddings: Create embeddings (POST /inference/v1/embeddings)
- list: List models (GET /v1/models)
- get_by_id: Get model (GET /v1/models/{model_id})
- create_generations: Generate image (POST /inference/v1/image/generations)

## Fields

- `model`: string [REQUIRED]
- `messages`: array [REQUIRED for chat]
- `prompt`: string [REQUIRED for complete]
- `input`: string/array [REQUIRED for embed]

## Example Request Bodies

**Create Chat Completion:**
```json
{"model": "accounts/fireworks/models/llama-v3p1-70b-instruct", "messages": [{"role": "user", "content": "Explain quantum computing"}]}
```

**Create Embeddings:**
```json
{"model": "nomic-ai/nomic-embed-text-v1.5", "input": "Sample text for embedding"}
```
