---
name: sivi-ai-design
description: AI-powered design generation from text prompts via Sivi. Use when the user mentions sivi, AI design, text to design, banner generation, ad creation, marketing graphics, AI designer.
version: 1.0.0
skill_type: external
base_url_env: SIVI_BASE_URL
auth_env_var: SIVI_API_KEY
auth_type: bearer
triggers:
  - sivi
  - AI design
  - text to design
  - banner generation
  - ad creation
  - marketing graphics
  - AI designer
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developer.sivi.ai/
---

# Sivi-AI-Design

AI-powered design generation from text prompts via Sivi. Use when the user mentions sivi, AI design, text to design, banner generation, ad creation, marketing graphics, AI designer.

## API Endpoints

- **POST** `/general/designs-from-content` - Generate designs from structured content
- **GET** `/general/designs-from-content` - Get designs from content
- **POST** `/general/designs-from-prompt` - Generate designs from natural language prompt
- **GET** `/general/designs-from-prompt` - Get designs from prompt
- **GET** `/general/designs` - List all generated designs
- **GET** `/general/designs/{designId}` - Get design details
- **DELETE** `/general/designs/{designId}` - Delete a design
- **POST** `/general/designs/{designId}/download` - Download design
- **GET** `/general/templates` - List available templates
- **GET** `/general/templates/{templateId}` - Get template details

## Actions

- create_from_content: Generate designs from structured content (POST /general/designs-from-content)
- get_from_content: Get designs from content (GET /general/designs-from-content)
- create_from_prompt: Generate designs from prompt (POST /general/designs-from-prompt)
- get_from_prompt: Get designs from prompt (GET /general/designs-from-prompt)
- list_designs: List all designs (GET /general/designs)
- get_design: Get design details (GET /general/designs/{designId})
- delete_design: Delete a design (DELETE /general/designs/{designId})
- download_design: Download design (POST /general/designs/{designId}/download)
- list_templates: List templates (GET /general/templates)
- get_template: Get template details (GET /general/templates/{templateId})

## Fields

- `title`: string [REQUIRED for content] - Design title
- `description`: string [OPTIONAL] - Design description
- `brand`: object [OPTIONAL] - Brand guidelines
- `prompt`: string [REQUIRED for prompt] - Natural language prompt
- `design_type`: string [REQUIRED] - Design type (banner, ad, social_media, etc.)
- `dimensions`: object [OPTIONAL] - Output dimensions
- `language`: string [OPTIONAL] - Output language

## Example Request Bodies

**Generate from Content:**
```json
{"title": "Summer Sale Banner", "description": "50% off all items", "design_type": "banner", "dimensions": {"width": 1200, "height": 628}}
```

**Generate from Prompt:**
```json
{"prompt": "Modern minimalist product banner with geometric shapes", "design_type": "banner", "brand": {"colors": ["#FF5733", "#FFFFFF"]}}
```

**Download Design:**
```json
{"format": "png"}
```
