---
name: pixlr-image-editor
description: Photo editing and image manipulation via Pixlr. Use when the user mentions pixlr, photo editor, image editing, image manipulation, batch processing, photo filter.
version: 1.0.0
skill_type: external
base_url_env: PIXLR_BASE_URL
auth_env_var: PIXLR_API_KEY
auth_type: bearer
triggers:
  - pixlr
  - photo editor
  - image editing
  - image manipulation
  - batch processing
  - photo filter
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
---

# Pixlr-Image-Editor

Photo editing and image manipulation via Pixlr. Use when the user mentions pixlr, photo editor, image editing, image manipulation, batch processing, photo filter.

## API Endpoints

- **POST** `/post` - Create a new image edit job
- **GET** `/job/{jobId}` - Get job status
- **GET** `/jobs` - List all jobs
- **DELETE** `/job/{jobId}` - Delete a job
- **POST** `/batch` - Create batch image processing job
- **GET** `/batch/{batchId}` - Get batch job status
- **GET** `/templates` - List available templates
- **GET** `/templates/{templateId}` - Get template details

## Actions

- create_job: Create a new image edit job (POST /post)
- get_job: Get job status (GET /job/{jobId})
- list_jobs: List all jobs (GET /jobs)
- delete_job: Delete a job (DELETE /job/{jobId})
- create_batch: Create batch image processing job (POST /batch)
- get_batch: Get batch job status (GET /batch/{batchId})
- list_templates: List available templates (GET /templates)
- get_template: Get template details (GET /templates/{templateId})

## Fields

- `template`: string [REQUIRED for create] - Template ID
- `image_url`: string [REQUIRED for create] - Source image URL
- `output_format`: string [OPTIONAL] - Output format (png, jpg, webp)
- `name`: string [OPTIONAL] - Job name
- `modifications`: object [OPTIONAL] - Image modifications

## Example Request Bodies

**Create Image Edit Job:**
```json
{"template": "basic_edit", "image_url": "https://example.com/photo.jpg", "output_format": "png"}
```

**Batch Processing:**
```json
{"template": "resize", "image_urls": ["https://example.com/1.jpg", "https://example.com/2.jpg"], "output_format": "jpg"}
```
