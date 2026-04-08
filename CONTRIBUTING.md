# Contributing to SaaS API Skills

🎉 Thank you for your interest in contributing!

This project thrives on community contributions. Whether you're adding new skills or improving existing ones, your help makes AI integrations better for everyone.

---

## How to Contribute

### 1. Adding a New Skill

Create a new `.skill.md` file in the `skills/` directory following this structure:

```yaml
---
name: service-name
description: Brief description of what this service does
version: 1.0.0
skill_type: external
base_url_env: SERVICE_BASE_URL
auth_env_var: SERVICE_API_KEY
auth_type: bearer
triggers:
  - trigger-word-1
  - trigger-word-2
license: MIT
metadata:
  author: your-github-username
  version: 1.0.0
---

# Service Name

Description of what this skill enables.

## API Endpoints

- **GET** `/api/v1/resource` - Get resources
- **POST** `/api/v1/resource` - Create resource
- **GET** `/api/v1/resource/{id}` - Get single resource
- **PATCH** `/api/v1/resource/{id}` - Update resource
- **DELETE** `/api/v1/resource/{id}` - Delete resource

## Actions

- list: List all resources (GET /api/v1/resource)
- create: Create a resource (POST /api/v1/resource)
- get: Get a resource (GET /api/v1/resource/{id})
- update: Update a resource (PATCH /api/v1/resource/{id})
- delete: Delete a resource (DELETE /api/v1/resource/{id})

## Fields

- `field_name`: type [REQUIRED|OPTIONAL] - Description

## Example Request Bodies

**Create Resource:**
```json
{"name": "Example", "type": "resource"}
```
```

### 2. Improving Existing Skills

- Add missing endpoints
- Fix typos or outdated information
- Add more complete examples
- Improve documentation

### 3. Reporting Issues

Found a problem? Open an issue with:
- Skill name
- Issue description
- Suggested fix (if any)

---

## Quality Standards

### ✅ What Makes a Great Skill

- **Clear endpoints** - Real API paths from official documentation
- **Complete examples** - Working JSON request bodies
- **Proper authentication** - Correct auth type and env vars
- **Good triggers** - Keywords that help AI detect when to use this skill

### ❌ What to Avoid

- Placeholder or fake endpoints
- Including actual API keys
- Copying proprietary code without permission
- Outdated API information

---

## Quick Checklist

Before submitting your PR, verify:

- [ ] File follows the skill template
- [ ] Endpoints are from official documentation
- [ ] Examples are valid JSON
- [ ] No sensitive data included
- [ ] File is named correctly (`service-name.skill.md`)

---

## Getting Help

- Open an issue for questions
- Check existing skills for reference
- Review official API docs for accuracy

---

<p align="center">
  Thanks for contributing! 🚀
</p>
