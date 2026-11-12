# Workflow spec: Just Raised

**Status:** DRAFT 2026-11-12 · sections 1 to 4 drafted, signals table pending approval · angle matrix, variables, cadence pending · copy pending

Source idea: #1 in `output/campaigns/campaign-strategy.md`. Built on `context/icp/`, `context/icp/signal-matrix.md` and `context/docs/gtm-system.md`.

## 1. Mother Intent [ENGINE]

A tech startup headquartered in Nigeria, Kenya or Ghana announced a pre-seed, seed or Series A round in the last 100 days. Catalog intent: Companies fundraising.

## 2. Inclusion / Exclusion [ICP]

**Include**
- HQ in Nigeria, Kenya or Ghana; 20 to 100 employees; tech-enabled; round in the last 100 days.
- Recipient: a senior HR leader (Head of HR, HR Lead, HR Manager, People Lead, Head of People) who joined from another company. If none, the CEO or co-founder.

**Exclude**
- HR leaders promoted internally (the company stays; the founder gets the email).
- PaidHR customers and open deals (HubSpot).
- Contacted in the last 90 days.
- Under 20 or over 100 employees.
- HR and payroll software vendors (competitors.md).
- Rounds with no announced date.

## 3. Sources [ENGINE]

- Trigger: Crunchbase via Clay "Find Organization" (HQ in NG, KE or GH); TechCabal and Nairametrics funding round-ups scraped by n8n.
- Company profile: treg `fetchinio.linkedin.company.profile` via Clay HTTP (headcount, HQ country, locations), $0.0015 per company.
- People: Clay Find People (title, current and previous company).
- Open roles: Clay Find Jobs.
- Emails: Clay email waterfall, then verification.

## 4. Signals table [ENGINE]

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| 1 | Round in the last 100 days | trigger | Boolean: `round_date >= today - 100` AND `round_type` in {pre-seed, seed, Series A} AND `hq_country` in {NG, KE, GH} | true / false |
| 2 | External senior HR leader | router | Boolean: senior HR title AND `previous_company` is not the current company | `has_hr` = yes (HR leader) / no (founder or CEO) |
| 3 | Open roles | router | Count of open jobs, clusters 0 / 1 to 4 / 5+ | `hiring` = none / some / heavy |
| 4 | HQ country | context-clause | Enum: NG / KE / GH | compliance line |
| 5 | Round details | context-clause | Text: `round_type`, `round_amount` | "your {{round_type}}" |
| 6 | Staff outside the HQ country | context-clause | Boolean: any location outside `hq_country` | cross-border line |
| 7 | Days to 31 Jan 2027 | context-clause, Nigeria only | Date math when `hq_country` = NG | timing line |

Routing: 2 axes, `has_hr` (2) x `hiring` (3) = 6 cells.

**Flags:** Kenya and Ghana have no named customer (icp.md Tier 3); no Ghana payroll rules researched (market.md); Workpay is Kenya-based (competitors.md).

## 5. Routing matrix with angles [ENGINE]

Pending.

## 6. Variables contract [ENGINE]

Pending.

## 7. Cadence and channel [ENGINE]

Pending.
