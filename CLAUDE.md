# PaidHR GTM Context OS

## Company

PaidHR (paidhr.com): HR and payroll platform for African businesses. Full description to fill in after research.

## How this folder works

- `.claude/skills/`: reusable Claude skills for GTM tasks. Read when a task matches a skill.
- `context/icp/`: ideal customer profiles and personas. Read before any targeting, list building or copy.
- `context/positioning/`: positioning, differentiators and competitor comparisons. Read before writing any claim about PaidHR.
- `context/messaging/`: approved messaging, value props and objection handling. Read before writing copy.
- `context/brand-kit/`: voice, tone, visual and style rules. Read before producing any copy or asset.
- `context/docs/research/`: raw research notes with sources. Read when you need evidence for a company fact.
- `knowledge-base/playbooks/`: repeatable GTM workflows and specs. Read before running or building a workflow.
- `knowledge-base/learnings/`: what worked, what failed, and why. Read before planning new campaigns.
- `meetings/`: meeting notes and decisions. Read when picking up work that came from a meeting.
- `output/campaigns/`: finished campaign assets and copy. Write here; read to reuse past work.
- `tools/`: scripts and tool configs. Read when a task needs automation or a tool.
- `weekly-priorities/`: one file per ISO week (YYYY-Www.md). Read at the start of every session.
- `work-log/`: one file per ISO week (YYYY-Www.md). Append an entry after every change.

## Rules

1. Cite a source (URL or file path) for every company fact.
2. Never invent numbers. If a figure has no source, mark it as unknown.
3. No em dashes in any copy.
4. Ask before sending or publishing anything.
5. Log every change in this week's work log (`work-log/YYYY-Www.md`) with a timestamp.

## Tools

- **treg** (CLI): paid data lookups (enrichment, SERP, social, ads, scraping). Check the price with `treg catalog get <id>` before every call, then `treg call <id>`. Report each call's cost and estimate the total before loops. Login is project-only via `TREG_CONFIG` (`.treg/config.json`). Docs: https://treg.to/skill.md
- **Miro** (MCP, project plugin `miro@miro-ai`): diagrams, such as GTM system maps and workflow flows.
- **Notion** (MCP, `.mcp.json`): where finished docs are published. GitHub stays the source of truth: write and edit here first, then publish to Notion. Ask before publishing.

## Skills

From github.com/bolaji-ships/gtm-starter-kit. Method docs live in `knowledge-base/playbooks/`.

- **Research to copy, in order:** `campaign-strategy` (15 to 25 tiered campaign ideas), `signal-matrix` (ICP segments and the signals to build first), `build-workflow-spec` (one workflow's structure, no copy), `campaign-copy` (email and LinkedIn copy from an approved spec and verified facts), `miro-gtm-flowchart` (GTM system as a Miro flow chart).
- **Clay builds** (use `tools/rex`): `build-clay`, `prompt-builder`, `campaign-contract`, `design-clay-table-json`, `import-clay-table`, `save-clay-schema`, `calculate-costs`, `workspace-cost-audit`, `export-tables`, `campaign-qa`.
- **Research and deliverability:** `crawl4ai` (crawl sites to Markdown), `agent-browser` (drive a real browser), `inbox-placement-test` (inbox vs spam placement, for EmailBison and MailReach).

