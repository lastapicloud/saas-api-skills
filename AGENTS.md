# AGENTS.md — saas-api-skills

> **Public** repo. Curated catalog of 368 API integration skills following the [agentskills.io](https://agentskills.io/specification) spec. Maintained by the LastAPI team. README owns the marketing-side narrative — this file owns the engineering / contributor view.

## What This Is

A community-oriented index of `*.skill.md` files, each describing how an AI agent (Claude, GPT, generic LLM) should call a specific SaaS HTTP API: endpoints, parameters, auth, example payloads. Used by:

- External agents — anyone running an MCP-style agent can clone this repo and load the skill files
- Public showcase of the integrations LastAPI-generated APIs ship with

**This repo is a published mirror, not the runtime source.** The canonical skill files live in `lastapi-framework` (`apigenerator/resources/1 - Project/1 - BaseProject/Project/skills/`); that copy is committed into every generated customer API and read by its `SkillLoader` (`/assistant/*` routes). Nothing fetches this repo at deploy time. The two copies share filenames but have drifted (the framework copy is newer); syncing framework → this repo is manual and currently pending (no automation exists).

## Stack

- **No runtime** — pure markdown collection, no build step, no package.json
- **Spec:** [agentskills.io](https://agentskills.io/specification) — each `*.skill.md` follows the documented frontmatter + section schema
- **Hosting:** GitHub `lastapicloud/saas-api-skills` (public, MIT licensed)

## Architecture

```
saas-api-skills
  ├── skills/                 — 368 *.skill.md files (one per service)
  │   ├── stripe-payments.skill.md
  │   ├── slack-messaging.skill.md
  │   ├── notion-pages.skill.md
  │   └── ... 365 more
  ├── README.md               — public-facing catalog overview + quick start
  ├── CONTRIBUTING.md         — how to add a new skill
  ├── CODE_OF_CONDUCT.md      — community contract
  └── LICENSE                 — MIT
```

Each `*.skill.md` is self-contained and consumable by an LLM with no external lookups. There is no `category` frontmatter field; README groups skills into categories by hand.

Frontmatter keys in use: `name`, `description`, `version`, `skill_type`, `base_url_env`, `auth_env_var`, `auth_type`, `triggers`, `license`, `metadata` (`author`, `version`, optional `documentation`), `compatibility` (`Requires <base_url_env> and <auth_env_var> environment variables.`), plus `auth_user_env` for two-credential auth. Body sections: `API Endpoints`, `Actions`, `Fields`, `Example Request Bodies` (a few files use `Example Requests`).

## Capabilities

- **368 service integrations** ready for AI-agent consumption (Stripe, Slack, Notion, Datadog, OpenAI, …)
- **Spec-compliant** — follows agentskills.io specification, so any compliant agent runtime can load these without per-skill custom code
- **Versioned via git** — every skill file's history is the audit trail
- **Public + community-extensible** — accepts PRs from external contributors per CONTRIBUTING.md

## Public Surface

| Surface | Where |
|---|---|
| Catalog browse | [`skills/`](skills/) directory + README's example table |
| Direct skill URLs | `https://github.com/lastapicloud/saas-api-skills/blob/main/skills/<name>.skill.md` (raw via `raw.githubusercontent.com/...`) |
| Canonical source | `lastapi-framework` template `skills/` (this repo mirrors it) |

No HTTP API of its own — consumers fetch raw files from GitHub.

## Scopes

- **Public — open source under MIT.** External contributors welcome.
- **Catalog scope:** SaaS HTTP APIs that an AI agent might call. Not for SDK-style libraries, not for non-HTTP protocols.
- **Spec-bound:** any file in `skills/` MUST follow agentskills.io. Use CONTRIBUTING.md as the gate.
- **Mirror contract:** skill content changes should land in `lastapi-framework` first, then be synced here; a change made only here never reaches customer APIs.

## Repo

- **GitHub:** `lastapicloud/saas-api-skills` (PUBLIC)
- **License:** MIT
- **Default branch:** `main`
- **Branch protection:** none (open contribution model)
- **CI:** none. There is no skill-schema validator yet — reviewers check frontmatter against CONTRIBUTING.md.

## Cross-Repo Dependencies

```
lastapi-framework template skills/   ← canonical; committed into every generated API
  ↓ manual sync (pending)
saas-api-skills (this repo)          ← public mirror

customer Lambdas  ← SkillLoader reads their own bundled skills/; /assistant/skills exposes them
```

## Workflow

```bash
# Add a new skill
git checkout -b add-<service-name>-skill
# Author skills/<service>-<surface>.skill.md following agentskills.io
# README + CONTRIBUTING.md describe the schema in full
git commit -m "add(<service>): <surface> skill"
gh pr create --base main
```

## Rules

- Every skill must follow [agentskills.io](https://agentskills.io/specification) spec exactly — frontmatter + section ordering + parameter shape.
- Filename pattern: `<service>-<primary-surface>.skill.md` (lowercase, hyphenated, e.g. `stripe-payments.skill.md`); frontmatter `name` should equal the filename stem. Known exceptions inherited from the framework copy: `auth0-users` (`name: auth0-management`), `cloudflareDNS-domains` (`cloudflaredns-domains`), `klaviyo-marketing` (`klaviyo-marketing-campaigns`) — fix in the framework first, since `name` is the runtime skill id.
- Never embed credentials in examples — use placeholder tokens like `${YOUR_STRIPE_API_KEY}`.
- New category? Update README's example table + add a section if there are 5+ skills in the category.
- Don't force-push `main` — public history is the audit trail for all downstream consumers.
