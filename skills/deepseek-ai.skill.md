---
name: deepseek-ai
description: AI models via DeepSeek. Use when the user mentions deepseek, deepseek-chat, reasoning model, coding assistant, low cost LLM.
version: 1.0.0
skill_type: external
base_url_env: DEEPSEEK_BASE_URL
auth_env_var: DEEPSEEK_API_KEY
auth_type: bearer
triggers:
  - deepseek
  - deepseek-chat
  - reasoning model
  - coding assistant
  - low cost LLM
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://api-docs.deepseek.com/
---

# Deepseek-AI

AI models via DeepSeek. Use when the user mentions deepseek, deepseek-chat, reasoning model, coding assistant, low cost LLM.

## API Endpoints

- **POST** `/v1/chat/completions` - Create chat completion
- **POST** `/v1/completions` - Create text completion
- **GET** `/v1/models` - List available models
- **GET** `/v1/models/{model}` - Get model information
- **POST** `/v1/embeddings` - Generate embeddings

## Actions

- create_chat: Create chat completion (POST /v1/chat/completions)
- create_completion: Create text completion (POST /v1/completions)
- list_models: List available models (GET /v1/models)
- get_model: Get model information (GET /v1/models/{model})
- create_embedding: Generate embeddings (POST /v1/embeddings)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., deepseek-chat, deepseek-reasoner)
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `max_tokens`: integer [OPTIONAL] - Max tokens to generate
- `top_p`: number [OPTIONAL] - Nucleus sampling
- `stream`: boolean [OPTIONAL] - Stream responses
- `stop`: array [OPTIONAL] - Stop sequences
- `input`: string [REQUIRED for embeddings] - Text to embed

## Example Request Bodies

**Chat Completion:**
```json
{"model": "deepseek-chat", "messages": [{"role": "user", "content": "Explain quantum computing in simple terms"}], "temperature": 0.7, "max_tokens": 500}
```

**Reasoning Model:**
```json
{"model": "deepseek-reasoner", "messages": [{"role": "user", "content": "Solve this math problem: 2x + 5 = 15"}], "temperature": 0.3}
```

**Text Completion:**
```json
{"model": "deepseek-chat", "prompt": "Write a short story about a robot", "temperature": 0.8, "max_tokens": 200}
```

**Embeddings:**
```json
{"input": "The future of artificial intelligence", "model": "deepseek-embedding"}
```
