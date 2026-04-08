---
name: together-ai
description: Run inference via Together AI. Use when the user mentions together ai,
  together, llm, chat, inference, embedding.
version: 1.0.0
skill_type: external
base_url_env: TOGETHER_AI_BASE_URL
auth_env_var: TOGETHER_AI_API_KEY
auth_type: bearer
triggers:
  - together ai
  - together
  - llm
  - chat
  - inference
  - embedding
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TOGETHER_AI_BASE_URL and TOGETHER_AI_API_KEY environment variables.
---

# Together-Ai

Run inference via Together AI. Use when the user mentions together ai, together, llm, chat, inference, embedding.

## API Endpoints

- **POST** `/v1/chat/completions` - Create chat completion
- **POST** `/v1/completions` - Create completion
- **POST** `/v1/embeddings` - Create embeddings
- **POST** `/v1/images/generations` - Generate image
- **GET** `/v1/models` - List models
- **GET** `/v1/fine-tunes` - List fine-tune jobs
- **POST** `/v1/fine-tunes` - Create fine-tune job

## Actions

- create: Create chat completion (POST /v1/chat/completions)
- create_completions: Create completion (POST /v1/completions)
- create_embeddings: Create embeddings (POST /v1/embeddings)
- create_generations: Generate image (POST /v1/images/generations)
- list: List models (GET /v1/models)
- list_fine_tunes: List fine-tune jobs (GET /v1/fine-tunes)
- create_fine_tunes: Create fine-tune job (POST /v1/fine-tunes)

## Fields

- `model`: string [REQUIRED]
- `messages`: array [REQUIRED for chat]
- `prompt`: string [REQUIRED for complete/image]
- `input`: string [REQUIRED for embed]

## Example Request Bodies

**Create Chat Completion:**
```json
{"model": "meta-llama/Llama-3.3-70B-Instruct-Turbo", "messages": [{"role": "user", "content": "Explain quantum computing in simple terms"}]}
```

**Create Embeddings:**
```json
{"model": "togethercomputer/m2-bert-80M-8k-retrieval", "input": "The quick brown fox jumps over the lazy dog"}
