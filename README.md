# SaaS API Skills

<p align="center">
  <a href="https://awesome.re">
    <img src="https://awesome.re/badge-flat2.svg" alt="Awesome">
  </a>
  <a href="https://github.com/lastapicloud/saas-api-skills/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License">
  </a>
  <a href="https://github.com/lastapicloud/saas-api-skills/stargazers">
    <img src="https://img.shields.io/github/stars/lastapicloud/saas-api-skills" alt="Stars">
  </a>
  <a href="https://github.com/lastapicloud/saas-api-skills/issues">
    <img src="https://img.shields.io/github/issues/lastapicloud/saas-api-skills" alt="Issues">
  </a>
</p>

<p align="center">
  🦸 A curated collection of <strong>368+ API integration skills</strong> for instantly connecting AI agents to the tools your team uses every day.
</p>

---

## What Are These Skills?

This repository contains **API integration skills** that enable AI agents (like Claude, GPT, and other LLMs) to interact with **340+ SaaS platforms** — from CRMs and databases to email, analytics, and more.

Think of each skill file as a **blueprint** that tells an AI:
- What endpoints exist for this service
- What parameters are needed
- How to authenticate
- Example request bodies

### Example Skills

| Service | Category | Description |
|---------|----------|-------------|
| `stripe-payments.skill.md` | 💳 Payments | Full Stripe integration for payments, subscriptions, customers |
| `slack-messaging.skill.md` | 💬 Communication | Send messages, create channels, manage webhooks |
| `notion-pages.skill.md` | 📝 Productivity | Create pages, databases, and manage workspace |
| `datadog-monitoring.skill.md` | 📊 Observability | Monitor metrics, events, and alerts |
| `openai-api.skill.md` | 🤖 AI & LLM | Chat completions, embeddings, fine-tuning |

---

## Quick Start

### Browse Skills

Explore the [`skills/`](skills/) directory or search for what you need:

```bash
# Find skills related to payments
ls skills/ | grep -i payment

# Find skills related to analytics  
ls skills/ | grep -i analyt
```

### Use in Your AI Project

Each skill file follows a simple structure:

```yaml
---
name: service-name
description: What this integration does
base_url_env: SERVICE_BASE_URL
auth_env_var: SERVICE_API_KEY
auth_type: bearer
triggers:
  - keyword1
  - keyword2
---

# Service Name

Description of the API endpoints and actions available.
```

---

## Categories

### 🤖 AI & Machine Learning (15 skills)
OpenAI, Anthropic, Mistral, Groq, DeepSeek, Ollama, Google Gemini, Azure OpenAI, Cohere, Fireworks, HuggingFace, Together AI, Perplexity, Replicate, xAI

### 📊 Analytics & Observability (25+ skills)
Datadog, New Relic, Splunk, Grafana, Amplitude, Mixpanel, Heap, PostHog, Segment, Hotjar, Pendo, FullStory, Plausible, Sentry, Dynatrace, AppDynamics

### 🔐 Auth & Identity (15+ skills)
Auth0, Clerk, Okta, Kinde, Logto, Supertokens, Stytch, Descope, FusionAuth, Keycloak, Ping Identity

### 💬 Communication (20+ skills)
Slack, Discord, Twilio, SendGrid, Mailgun, Brevo, Microsoft Teams, Webex, Telegram, Intercom

### 📅 Scheduling (15+ skills)
Calendly, Cal.com, Acuity, Google Calendar, Outlook Calendar, Square Appointments, OnceHub, SimplyBook

### 🛒 E-Commerce & Payments (15+ skills)
Stripe, PayPal, Square, Shopify, WooCommerce, Adyen, Braintree, Razorpay

### 💼 Productivity & Project Management (25+ skills)
Notion, Asana, ClickUp, Trello, Linear, Monday, Jira, Todoist, Wrike, Basecamp, Shortcut

### 📝 Documentation & Wiki (12+ skills)
Confluence, GitBook, Notion, Coda, Slite, Nuclino, Tettra, Outline, BookStack

### 🎨 Design & Creative (12+ skills)
Figma, Canva, Adobe Creative Cloud, Bannerbear, Pixlr, VistaCreate, Sivi AI, MURAL, Loom, Frame.io

### 🗄️ Databases (20+ skills)
PostgreSQL, MySQL, MongoDB, Redis, PlanetScale, Turso, Supabase, Neon, CockroachDB, ClickHouse

### ☁️ DevOps & Infrastructure (30+ skills)
AWS, DigitalOcean, Netlify, Vercel, Render, Cloudflare, Fastly, Heroku

### 🔒 Security (10+ skills)
Snyk, SentinelOne, SecurityScorecard, Trend Micro, Qualys

### 📦 Storage (12+ skills)
AWS S3, Google Cloud Storage, Backblaze B2, Cloudflare R2, MinIO, Dropbox, Wasabi

---

## Contributing

We welcome contributions! Here's how to help:

### Adding a New Skill

1. Fork this repository
2. Copy the template below to `skills/your-service-name.skill.md`
3. Fill in the API details (endpoints, authentication, examples)
4. Submit a Pull Request

### Skill Template

```yaml
---
name: your-service-name
description: Brief description of what this service does
version: 1.0.0
skill_type: external
base_url_env: SERVICE_BASE_URL
auth_env_var: SERVICE_API_KEY
auth_type: bearer|api_key|basic
triggers:
  - trigger1
  - trigger2
license: MIT
metadata:
  author: your-github-username
  version: 1.0.0
---

# Service Name

Description of what this skill enables.

## API Endpoints

- **GET** `/endpoint` - Description
- **POST** `/endpoint` - Description

## Actions

- action_name: Description (METHOD /endpoint)

## Fields

- `field_name`: type [REQUIRED|OPTIONAL] - Description

## Example Request Bodies

**Example:**
```json
{"field": "value"}
```
```

### Contribution Guidelines

- ✅ Use clear, descriptive names
- ✅ Include real API endpoints from official documentation
- ✅ Provide valid example request bodies
- ✅ Add appropriate triggers for AI detection
- ❌ Don't include sensitive information or API keys
- ❌ Don't copy proprietary code without permission

---

## Why This Matters

Modern AI agents are powerful, but they need **context** to be useful. These skills give AI agents the knowledge they need to:

- 🔌 Connect to your existing tools (no re-integration needed)
- 📊 Access your data (analytics, CRM, databases)
- ⚡ Take action (send emails, create tasks, process payments)
- 🔄 Automate workflows (connect multiple services together)

---

## Featured Use Cases

| Use Case | Skills Needed |
|----------|---------------|
| Build a customer support bot | Intercom, Zendesk, Slack, Salesforce |
| Create a marketing automation hub | HubSpot, Mailchimp, Twilio, Google Analytics |
| Build an AI analyst | PostgreSQL, Datadog, Slack, Google Sheets |
| Automate invoicing | Stripe, QuickBooks, SendGrid, Notion |

---

## Related Projects

- [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) - Similar concept for Claude
- [awesome-mcp-servers](https://github.com/topics/mcp) - Model Context Protocol integrations
- [lastapi](https://lastapi.cloud) - Turn any database into a REST API

---

## License

This project is licensed under the [MIT License](LICENSE).

---

<p align="center">
  <strong>🚀 Built with ❤️ by the community</strong>
</p>

---

<p align="center" font-size="small">
  <em>These skills are freely available for open source use. If you need instant API integrations with zero coding, 
  <a href="https://lastapi.cloud">LastAPI</a> provides production-ready integrations for all these services and more.</em>
</p>
