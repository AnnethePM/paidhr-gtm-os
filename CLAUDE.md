# PaidHR GTM Context OS

## Company

PaidHR (paidhr.com): Lagos-based people operations platform (payroll, tax and pension remittance, HR, and PaidLife earned wage access) for African businesses of about 20 to 200+ employees; 400+ businesses and 25,000+ employees (source: `context/docs/research/company.md`).

## How this folder works

- `.claude/skills/`: reusable Claude skills for GTM tasks. Read when a task matches a skill.
- `context/icp/`: `icp.md`, `personas.md`, `signal-matrix.md`. Read before any targeting, list building or copy.
- `context/positioning/`: `positioning.md`, `value-proposition.md`, `competitors.md`. Read before writing any claim about PaidHR.
- `context/messaging/`: `messaging.md`, `facts.md` (the only source of names, numbers and claims for copy). Read before writing copy.
- `context/brand-kit/`: `brand.md` (tone and key phrases). Read before producing any copy or asset.
- `context/docs/`: `case-studies.md` (customer proof), `gtm-system.md` (the outbound system end to end). Read when you need proof or the system design.
- `context/docs/research/`: `company.md`, `customers.md`, `customer-videos.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md` (raw research with sources). Read when you need evidence for a company fact.
- `knowledge-base/playbooks/`: `workflow-anatomy.md`, `signal-matrix-framework.md`, `copy-iron-laws.md`, `copy-frameworks.md`, `linkedin-dm-frameworks.md`, `copy-bans.yaml`, `templates/facts-template.md`, `clay/` (5 Clay guides). Read before running or building a workflow.
- `knowledge-base/learnings/`: what worked, what failed, and why. Read before planning new campaigns.
- `meetings/`: meeting notes and decisions. Read when picking up work that came from a meeting.
- `output/campaigns/`: `campaign-strategy.md` (ranked ideas), `just-started/workflow-spec.md` (Just Raised spec and copy). Write here; read to reuse past work.
- `tools/`: `rex/` (Clay SDK), `crawl4ai/` and `agent-browser/` (install guides). Read when a task needs automation or a tool.
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
- **Notion** (MCP, `.mcp.json`): where finished docs are published, at https://app.notion.com/p/416bc1132dba8112b62ef3c3068c50b1 (PaidHR GTM OS). GitHub stays the source of truth: write and edit here first, then publish to Notion. Ask before publishing.
- **GitHub** (`gh` CLI): source of truth, https://github.com/AnnethePM/paidhr-gtm-os (public).
- **Planned, not connected yet** (named in `gtm-system.md`): Clay, HubSpot, n8n, PlusVibe.

## Skills

From github.com/bolaji-ships/gtm-starter-kit. Method docs live in `knowledge-base/playbooks/`.

- **Research to copy, in order:** `campaign-strategy` (15 to 25 tiered campaign ideas), `signal-matrix` (ICP segments and the signals to build first), `build-workflow-spec` (one workflow's structure, no copy), `campaign-copy` (email and LinkedIn copy from an approved spec and verified facts), `miro-gtm-flowchart` (GTM system as a Miro flow chart).
- **Clay builds** (use `tools/rex`): `build-clay`, `prompt-builder`, `campaign-contract`, `design-clay-table-json`, `import-clay-table`, `save-clay-schema`, `calculate-costs`, `workspace-cost-audit`, `export-tables`, `campaign-qa`.
- **Research and deliverability:** `crawl4ai` (crawl sites to Markdown), `agent-browser` (drive a real browser), `inbox-placement-test` (inbox vs spam placement, for EmailBison and MailReach).

