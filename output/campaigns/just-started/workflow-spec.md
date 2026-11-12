# Workflow spec: Just Raised

**Status:** STRUCTURE-APPROVED 2026-11-12 (amended: cells 7 to 9) · E1 approved 2026-11-12 · E2 drafted, pending approval · E3, DMs pending

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
| 2 | External senior HR leader, and how new | router | Senior HR title AND `previous_company` is not the current company; then `today - start_date <= 30` days | `has_hr` = new (started 30 days ago or less) / established (more than 30 days) / no (founder or CEO) |
| 3 | Open roles | router | Count of open jobs, clusters 0 / 1 to 4 / 5+ | `hiring` = none / some / heavy |
| 4 | HQ country | context-clause | Enum: NG / KE / GH | compliance line |
| 5 | Round details | context-clause | Text: `round_type`, `round_amount` | "your {{round_type}}" |
| 6 | Staff outside the HQ country | context-clause | Boolean: any location outside `hq_country` | cross-border line |
| 7 | Days to 31 Jan 2027 | context-clause, Nigeria only | Date math when `hq_country` = NG | timing line |

Routing: 2 axes, `has_hr` (3) x `hiring` (3) = 9 cells.

**Flags:** Kenya and Ghana have no named customer (icp.md Tier 3); no Ghana payroll rules researched (market.md); Workpay is Kenya-based (competitors.md).

## 5. Routing matrix with angles [ENGINE]

2 axes, `has_hr` (3: new, established, no) x `hiring` (3) = 9 cells. Country is a context-clause: NG gets the 31 Jan 2027 timing line; KE and GH get a general statutory-filing line.

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| 1 | has_hr = established, hiring = none (0 roles) | Just raised, has an outside HR leader, not posting roles yet. HR leader likely owns payroll and filings; the funded hiring hasn't started | Get tax and pension remittances on autopilot, with receipts, before the funded hiring starts |
| 2 | has_hr = established, hiring = some (1 to 4) | HR leader is adding a few people to payroll while running remittances | Each new hire lands on payroll and the remittance file without extra manual work |
| 3 | has_hr = established, hiring = heavy (5+) | HR leader is running a hiring push; payslips, PAYE and pension lines grow every month | Payroll and filing scale with headcount, so the HR leader's time goes to hiring, not remittances |
| 4 | has_hr = no, hiring = none | Just raised, no HR leader; the founder likely still runs payroll; not hiring yet | Take payroll runs and remittances off the founder's desk (Famasi: "about one hour" per run, approved claim) |
| 5 | has_hr = no, hiring = some (1 to 4) | Founder is hiring a few people; each new person lands on the founder's payroll | Set payroll up for the new hires before founder-run payroll stops scaling as the team grows |
| 6 | has_hr = no, hiring = heavy (5+) | Founder is hiring 5+ with no HR title; payroll and filing volume rising with no dedicated owner | Payroll and statutory filing run on their own while the founder hires (the founder's situation, never a gap) |
| 7 | has_hr = new, hiring = none | Likely hired around the round; first weeks spent setting up how payroll and filing run before hiring starts | Start the role with remittances already automated, with receipts, as an early win |
| 8 | has_hr = new, hiring = some (1 to 4) | Onboarding new hires in their first weeks while learning the payroll setup they joined into | New hires go onto payroll and the remittance file from day one, without building a process from scratch |
| 9 | has_hr = new, hiring = heavy (5+) | Likely brought in to run the hiring push the round pays for | Payroll and filing scale on their own, so they can focus on the hiring they were hired for |

**Branch coverage:** `{{open_role_count}}` exists only in cells 2, 3, 5, 6. `{{hr_title}}` exists only in cells 1 to 3 and 7 to 9. "Since you joined" may only appear in cells 7 to 9. `{{round_type}}` and `{{hq_country}}` exist in every cell. `{{days_to_deadline}}` exists only when `hq_country` = NG. `{{abroad_country}}` exists only when signal 6 is true.

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in branches |
|---|---|---|
| `{{first_name}}` | Clay Find People: first name | All |
| `{{company_name}}` | Clay company record: name | All |
| `{{round_type}}` | Crunchbase / news: round type (pre-seed, seed, Series A) | All |
| `{{hq_country}}` | treg LinkedIn profile: HQ country (Nigeria, Kenya, Ghana) | All |
| `{{hr_title}}` | Clay Find People: title of the external HR leader | Cells 1 to 3, 7 to 9 |
| `{{open_role_count}}` | Clay Find Jobs: count of open roles | Cells 2, 3, 5, 6 |
| `{{days_to_deadline}}` | Clay formula: 2027-01-31 minus today | hq_country = NG |
| `{{abroad_country}}` | treg LinkedIn profile / Find Jobs: first location outside `hq_country` | Signal 6 = true |
| `{{social_proof}}` | facts.md: Heroshe line for cells 1 to 3 and 7 to 9, Famasi line for cells 4 to 6 | All |
| `{{sender_signature}}` | facts.md sender identity (TBD) | All |

`round_amount` is enriched but not a copy variable (amounts are often undisclosed).

## 7. Cadence and channel [ENGINE]

- **Periodicity:** always-on. n8n checks funding sources daily; Clay batches new companies weekly. Each company enters once per round.
- **Channel:** email and LinkedIn (gtm-system.md step 8). Verified email: 3 emails (day 0, 3, 7, same thread) plus LinkedIn (empty connection request, then 2 DMs). Risky or no email: LinkedIn only.
- **Sender:** TBD (facts.md).

## Copy

### Email 1 (approved 2026-11-12)

**Subject:** `{payroll after the round|after the round}`

```
{{first_name}},

{{e1l1}}

{{e1l2}}

PaidHR helps growing African businesses pay staff on time and file every statutory remittance {automatically|on its own}.

{{social_proof}}

{Would you like to see how this could simplify payroll at {{company_name}}?|Would you like to take a look at how this could take payroll and remittances off your plate?}

{{sender_signature}}
```

**e1l1** (exhaustive, no fallback)
- + has_hr = new: "I read about {{company_name}}'s {{round_type}}, and that you joined as {{hr_title}} a few weeks ago."
- + has_hr = established: "I read about {{company_name}}'s {{round_type}}."
- + has_hr = no: "I read about {{company_name}}'s {{round_type}}."

**e1l2** (exhaustive, 9 cells, no fallback)
- + Cell 1 (established, 0 roles): "With no open roles listed yet, my guess is the hiring the round pays for is still ahead."
- + Cell 2 (established, 1 to 4): "You have {{open_role_count}} roles open, so I'd guess each new hire adds another payslip and another line in the tax and pension remittances."
- + Cell 3 (established, 5+): "With {{open_role_count}} roles open, payslips and tax and pension lines probably grow every month from here."
- + Cell 4 (no HR, 0 roles): "My guess is payroll still sits with you for now."
- + Cell 5 (no HR, 1 to 4): "With {{open_role_count}} roles open, each new person probably lands on a payroll you run yourself."
- + Cell 6 (no HR, 5+): "With {{open_role_count}} roles open, my guess is payroll and filings are growing as fast as the team you're hiring."
- + Cell 7 (new, 0 roles): "No roles are open yet, so I'd guess your first weeks go on setting up how payroll and filings run before hiring starts."
- + Cell 8 (new, 1 to 4): "With {{open_role_count}} roles open, you're probably adding new hires to payroll while settling into the role."
- + Cell 9 (new, 5+): "With {{open_role_count}} roles open, I'd guess a lot of your first months goes on hiring."

**social_proof** (exhaustive, no fallback)
- + has_hr = new or established: "Heroshe, a cross-border shipping startup, used to take two weeks or more on statutory remittances before moving them to PaidHR."
- + has_hr = no: "Famasi, a health tech startup, saves about one hour on every payroll run with PaidHR."

**Sample (cell 5):**

> Tunde,
>
> I read about Kora's seed round.
>
> With 3 roles open, each new person probably lands on a payroll you run yourself.
>
> PaidHR helps growing African businesses pay staff on time and file every statutory remittance automatically.
>
> Famasi, a health tech startup, saves about one hour on every payroll run with PaidHR.
>
> Would you like to see how this could simplify payroll at Kora?
>
> {{sender_signature}}

### Email 2 (draft, pending approval)

Day 3, same thread ("Re: payroll after the round").

```
{{first_name}},

{{e2l1}}

{{e2l2}}

{{e2l3}}

{{e2l4}}

{Should I send you a short walkthrough of how it works?|Would a short walkthrough of how it works be useful?}

{{sender_signature}}
```

**e2l1** (exhaustive by hq_country)
- + NG: "One date worth keeping in mind: the first annual PAYE return under Nigeria's new tax law is due 31 January."
- + KE or GH: "After a raise, the monthly tax and pension filings in {{hq_country}} usually grow with the team."

**e2l2** (exhaustive by hq_country)
- + NG: "PaidHR is updated for Nigeria's new tax law, effective 1 January 2026."
- + KE or GH: "PaidHR runs payroll for 400+ businesses and 25,000+ employees with zero statutory defaults or delays."

**e2l3**
- + NG: "In 2025 we filed ₦934M in PAYE with zero statutory defaults or delays."
- KE or GH: line omitted.

**e2l4**
- + Staff outside hq_country: "Your team in {{abroad_country}} can be paid from the same payroll."
- FALLBACK: line omitted.
