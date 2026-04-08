---
name: ollama-ai
description: Local LLM runtime via Ollama. Use when the user mentions ollama, local LLM, local AI, self-hosted, private AI, offline AI.
version: 1.0.0
skill_type: external
base_url_env: OLLAMA_BASE_URL
auth_env_var: OLLAMA_API_KEY
auth_type: none
triggers:
  - ollama
  - local LLM
  - local AI
  - self-hosted
  - private AI
  - offline AI
license: MIT
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.ollama.com/api/
---

# Ollama-AI

Local LLM runtime via Ollama. Use when the user mentions ollama, local LLM, local AI, self-hosted, private AI, offline AI.

## API Endpoints

- **GET** `/api/tags` - List available models
- **POST** `/api/generate` - Generate text completion
- **POST** `/api/chat` - Create chat completion
- **POST** `/api/embeddings` - Generate embeddings
- **POST** `/api/pull` - Pull a model
- **POST** `/api/push` - Push a model
- **POST** `/api/delete` - Delete a model
- **GET** `/api/show` - Show model information
- **POST** `/api/ps` - List running models

## Actions

- list_models: List available models (GET /api/tags)
- generate: Generate text completion (POST /api/generate)
- chat: Create chat completion (POST /api/chat)
- create_embedding: Generate embeddings (POST /api/embeddings)
- pull_model: Pull a model (POST /api/pull)
- push_model: Push a model (POST /api/push)
- delete_model: Delete a model (POST /api/delete)
- show_model: Show model information (GET /api/show)
- list_running: List running models (POST /api/ps)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., llama2, mistral, codellama)
- `prompt`: string [REQUIRED for generate] - Text prompt
- `messages`: array [REQUIRED for chat] - Chat messages
- `input`: string [REQUIRED for embeddings] - Text to embed
- `stream`: boolean [OPTIONAL] - Stream responses
- `options`: object [OPTIONAL] - Model options (temperature, top_p, etc.)
- `system`: string [OPTIONAL] - System prompt
- `template`: string [OPTIONAL] - Prompt template

## Example Request Bodies

**Generate:**
```json
{"model": "llama2", "prompt": "Once upon a time", "stream": false}
```

**Chat:**
```json
{"model": "llama2", "messages": [{"role": "user", "content": "Hello!"}], "stream": false}
```

**Embeddings:**
```json
{"model": "nomic-embed-text", "prompt": "The quick brown fox"}
```

**Model Options:**
```json
{"model": "llama2", "prompt": "Write a story", "options": {"temperature": 0.8, "top_p": 0.9, "num_predict": 200}}
```
