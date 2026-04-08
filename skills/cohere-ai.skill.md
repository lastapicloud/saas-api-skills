---
name: cohere-ai
description: Generate text, embeddings, and rerank via Cohere AI. Use when the user
  mentions cohere, ai, generate, embed, rerank, classify, llm.
version: 1.0.0
skill_type: external
base_url_env: COHERE_AI_BASE_URL
auth_env_var: COHERE_AI_API_KEY
auth_type: bearer
triggers:
  - cohere
  - ai
  - generate
  - embed
  - rerank
  - classify
  - llm
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COHERE_AI_BASE_URL and COHERE_AI_API_KEY environment variables.
---

# Cohere-Ai

Generate text, embeddings, and rerank via Cohere AI. Use when the user mentions cohere, ai, generate, embed, rerank, classify, llm.

## API Endpoints

- **POST** `/v2/chat` - Generate text with chat
- **POST** `/v2/embed` - Generate embeddings
- **POST** `/v2/rerank` - Rerank documents
- **POST** `/v1/classify` - Classify text
- **POST** `/v1/tokenize` - Tokenize text
- **POST** `/v1/detokenize` - Detokenize tokens
- **GET** `/v1/models` - List models
- **POST** `/v1/summarize` - Summarize text

## Actions

- create: Generate text with chat (POST /v2/chat)
- create_embed: Generate embeddings (POST /v2/embed)
- create_rerank: Rerank documents (POST /v2/rerank)
- create_classify: Classify text (POST /v1/classify)
- create_tokenize: Tokenize text (POST /v1/tokenize)
- create_detokenize: Detokenize tokens (POST /v1/detokenize)
- list: List models (GET /v1/models)
- create_summarize: Summarize text (POST /v1/summarize)

## Fields

- `model`: string [REQUIRED]
- `messages`: array [REQUIRED for chat]
- `texts`: array [REQUIRED for embed]
- `query`: string [REQUIRED for rerank]
- `documents`: array [REQUIRED for rerank]

## Example Request Bodies

**Generate Text (Chat):**
```json
{"model": "command-a-03-2025", "messages": [{"role": "user", "content": "Explain quantum computing in simple terms."}]}
```

**Rerank Documents:**
```json
{"model": "rerank-v3.5", "query": "What is deep learning?", "documents": ["Deep learning uses neural networks.", "SQL is a database language.", "Neural networks mimic the brain."]}
```
