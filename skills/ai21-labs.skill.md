---
name: ai21-labs
description: AI21 Labs Jurassic and Jamba AI models. Use when the user mentions ai21, jurassic, jamba, AI21, text generation.
version: 1.0.0
skill_type: external
base_url_env: AI21_BASE_URL
auth_env_var: AI21_API_KEY
auth_type: bearer
triggers:
  - ai21
  - jurassic
  - jamba
  - AI21
  - text generation
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.ai21.com/
---

# Ai21-Labs

AI21 Labs Jurassic and Jamba AI models. Use when the user mentions ai21, jurassic, jamba, AI21, text generation.

## API Endpoints

- **POST** `/v1/jamba-instruct/chat` - Chat completion (Jamba)
- **POST** `/v1/jamba/chat` - Chat completion (Jamba)
- **POST** `/v1/jurassic-2/chat` - Chat completion (Jurassic)
- **POST** `/v1/jurassic-2/completions` - Text completion (Jurassic)
- **GET** `/v1/models` - List available models
- **POST** `/v1/embeddings` - Generate embeddings
- **POST** `/v1/rerank` - Rerank documents

## Actions

- chat_jamba: Chat completion with Jamba (POST /v1/jamba-instruct/chat)
- chat_jurassic: Chat completion with Jurassic (POST /v1/jurassic-2/chat)
- complete_jurassic: Text completion (POST /v1/jurassic-2/completions)
- list_models: List available models (GET /v1/models)
- create_embedding: Generate embeddings (POST /v1/embeddings)
- rerank: Rerank documents (POST /v1/rerank)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., jamba-1.5-mini, jamba-1.5-large, jurassic-2-mid)
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `maxTokens`: integer [OPTIONAL] - Max tokens
- `topP`: number [OPTIONAL] - Nucleus sampling
- `stop`: array [OPTIONAL] - Stop sequences
- `input`: string [REQUIRED for embeddings] - Text to embed
- `query`: string [REQUIRED for rerank] - Query text
- `documents`: array [REQUIRED for rerank] - Documents to rerank

## Example Request Bodies

**Jamba Chat:**
```json
{"model": "jamba-1.5-mini", "messages": [{"role": "user", "content": "Hello"}]}
```

**Jurassic Completion:**
```json
{"model": "jurassic-2-mid", "prompt": "Once upon a time", "maxTokens": 100, "temperature": 0.7}
```

**Embeddings:**
```json
{"input": "The quick brown fox jumps over the lazy dog", "model": "jamba-embeddings"}
```

**Rerank:**
```json
{"model": "jamba-rerank", "query": "What is AI?", "documents": ["AI is artificial intelligence", "Python is a programming language"]}
```
