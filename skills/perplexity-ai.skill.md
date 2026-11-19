---
name: perplexity-ai
description: AI-powered search and research via Perplexity. Use when the user mentions perplexity, AI search, web search, research, grounded answers, citations.
version: 1.0.0
skill_type: external
base_url_env: PERPLEXITY_BASE_URL
auth_env_var: PERPLEXITY_API_KEY
auth_type: bearer
triggers:
  - perplexity
  - AI search
  - web search
  - research
  - grounded answers
  - citations
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.perplexity.ai/
---

# Perplexity-AI

AI-powered search and research via Perplexity. Use when the user mentions perplexity, AI search, web search, research, grounded answers, citations.

## API Endpoints

- **POST** `/search` - Perform web search
- **POST** `/v1/agent` - Create agent workflow
- **POST** `/v1/responses` - Create chat completion with search
- **POST** `/v1/embeddings` - Generate embeddings

## Actions

- search: Perform web search (POST /search)
- create_agent: Create agent workflow (POST /v1/agent)
- create_response: Create chat completion (POST /v1/responses)
- create_embedding: Generate embeddings (POST /v1/embeddings)

## Fields

- `query`: array [REQUIRED for search] - Search queries
- `model`: string [REQUIRED] - Model name (e.g., sonar-small, gpt-4)
- `input`: string [REQUIRED for responses] - Input text/prompt
- `tools`: array [OPTIONAL] - Tools to use (web_search, etc.)
- `instructions`: string [OPTIONAL] - System instructions
- `response_format`: object [OPTIONAL] - Response format (json_schema)
- `input`: string [REQUIRED for embeddings] - Text to embed

## Example Request Bodies

**Web Search:**
```json
{"query": ["What is the latest AI news?", "Perplexity updates"]}
```

**Chat Completion with Search:**
```json
{"model": "sonar-small", "input": "What are the latest developments in AI?", "tools": [{"type": "web_search"}]}
```

**Structured Output:**
```json
{"model": "sonar-small", "input": "List 3 popular AI tools", "response_format": {"type": "json_schema", "json_schema": {"name": "ai_tools", "schema": {"type": "object", "properties": {"tools": {"type": "array", "items": {"type": "object", "properties": {"name": {"type": "string"}, "description": {"type": "string"}}}}}}}}
```

**Embeddings:**
```json
{"input": "The quick brown fox jumps over the lazy dog", "model": "embeddings-multilingual"}
```
