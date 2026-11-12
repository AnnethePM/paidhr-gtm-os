# PaidHR outbound campaign ideas

Built from `CLAUDE.md`, `context/` and `knowledge-base/playbooks/workflow-anatomy.md`. Work in progress. Names and numbers in copy come only from `context/messaging/facts.md` (approved by the user on 2026-11-12).

**Segments** (signal-matrix.md): S1 funded Nigerian tech startups, 20 to 100 staff. S2 Nigerian operators with deskless staff, 100+. S3 Nigerian companies paying staff abroad.
**Personas** (personas.md): Champion = HR operations lead. Buyer = founder/CEO (S2: INFERRED COO or finance). Influencer = employees.

**Volume:** only the funding figure is sourced (51 disclosed Nigerian deals in H1 2026, about 8 a month, market.md). All other volumes are INFERRED bands to confirm with a test pull: Low = under 20 companies a month, Medium = 20 to 100, High = over 100.
**Difficulty:** Easy = standard Clay or treg action. Medium = extra parsing or a new source. Hard = custom scrape or unproven data.

## Ranked ideas

Ranked by signal strength, then by how easy the data is to get.

| # | Name | Mother intent | Segment / persona | Signal and data source | Angle | Volume / month | Difficulty |
|---|---|---|---|---|---|---|---|
| 1 | Just Raised | Companies fundraising | S1 / founder-CEO | Seed to Series A in last 90 days. Nigerian funding news (Nairametrics, TechCabal), Crunchbase via Clay | Hiring follows the round, and so do PAYE and pension filings. Fix payroll before the hiring push | About 8 (sourced: 51 deals in H1 2026) | Easy |
| 2 | HR or Payroll Role Posted | Hiring specific roles | S1, S2 / founder-CEO or hiring manager | Open HR Manager, People Ops, Payroll Officer role. Clay Find Jobs; treg `akta.x.jobs` | The job ad lists remittances as a duty. Let the new hire start with them automated | Medium (INFERRED) | Medium: Nigerian job coverage untested |
| 3 | Headcount Threshold | Companies in hypergrowth (headcount) | S1, S2 / founder-CEO | Crossed 20 or 100 staff, or +25% in 6 months. LinkedIn headcount via treg ($0.0015 per company) or Clay | Payroll that worked at 15 breaks at 40 (Famasi switched "as a team [grew]") | High (INFERRED) | Easy: needs monthly snapshots |
| 4 | Cross-Border Team | Hiring offshore | S3 / founder-CEO | Job posts or LinkedIn locations in Kenya, Ghana, South Africa, UK, US. Clay Find Jobs location filter; treg LinkedIn locations | Lagos and abroad on one payroll, each person paid in their currency | Low (INFERRED) | Medium |
| 5 | New HR Leader (New Hire) | New leadership (past 90/180 days) | S1, S2 / champion | HR, People or Ops lead started under 90 days. Clay Find People title + start date | New leaders inherit payroll; the 2026 bands and the 31 Jan return are their first test | Medium (INFERRED) | Easy (signal untested, icp.md) |
| 6 | Founder-Run Payroll | Have/don't have specific team | S1 / founder-CEO | 20 to 60 staff, funded, no HR or payroll title on LinkedIn. Clay Find People | "Payroll still sits with you." Famasi's hour per run back | Medium (INFERRED) | Easy |
| 7 | Hiring Velocity | Companies in hypergrowth (hiring velocity) | S1, S2 / champion | 5+ open roles at once. Clay Find Jobs + count | Each hire adds a payslip, a PAYE line and a pension line | Medium (INFERRED) | Easy |
| 8 | Shift Workforce Hiring | Hiring specific roles | S2 / champion | Job posts for drivers, riders, store, factory or field staff. Clay Find Jobs | Payslips, leave and EWA on WhatsApp and USSD: "No internet? No problem." | Medium (INFERRED) | Medium |
| 9 | Customer Lookalike | Lookalike of customers | S1 / founder-CEO | Companies like Heroshe, Famasi, Cleva. Clay lookalike | Teams like yours moved payroll off spreadsheets | Medium (INFERRED) | Easy (names approved in facts.md on 2026-11-12) |
| 10 | 31 January Return Countdown | Regulatory changes | All / champion and founder | No account signal: Nigeria Tax Act, first annual return due 31 Jan 2027 (market.md). Base list from Clay | Is payroll on the 2026 bands before the first return? | High (whole base list, INFERRED) | Easy |
| 11 | Creative Payroll Ideas | Niche-specific play | S1, S2 / founder-CEO | No signal. Website and LinkedIn read by Claygent | 3 payroll ideas from what their site shows (riders in 3 cities, staff in Ghana) | High (base list, INFERRED) | Medium: AI step |
| 12 | Event Follow-up | Companies attending an event | S1, S2 / founder-CEO | Sponsors and speakers at Moonshot 2026, HR Expo Africa. Clay HTTP scrape of event pages | Reference their talk or booth; PaidHR was at Moonshot 2026 | Low, seasonal (INFERRED) | Medium |
| 13 | Multi-Site Operator | Niche-specific play | S2 / COO or HR lead | 5+ locations on Google Maps. Google Places API via Clay HTTP | Many branches, one payroll and one record of statutory filing | Medium (INFERRED) | Hard: new build, unproven segment |
| 14 | HR Consultants and Payroll Agencies (Creative non-ICP) | Niche-specific play | Partners / agency founder | Nigerian HR consultancies and payroll outsourcers. Clay company search + website read | White-label payroll: "Launch your own Payroll business today!" | Low (INFERRED) | Medium |
| 15 | Accountants Serving SMEs (Creative non-ICP) | Niche-specific play | Partners / firm partner | Accounting firms listing PAYE or payroll services. Clay company search + website read | Refer clients before the 31 January rush | Low (INFERRED) | Medium |
| 16 | Staff Retention via EWA | Niche-specific play | S2 / HR lead | 100+ staff, many low or mid-wage roles, retention posts. Clay + LinkedIn posts | EWA as a perk at "zero cost to your company" (no lending language) | Low (INFERRED) | Hard: weak signal |
| 17 | Competitor Followers | Competitor customers | S1, S2 / champion | Followers of SeamlessHR or Workpay on LinkedIn. Data access uncertain | Comparing tools? Start with remittances with receipts | Unknown | Hard |
| 18 | Minimum Wage Watch | Regulatory changes | All / founder-CEO | Fires when a new minimum wage is set (review due June 2027, market.md) | Every pay structure changes this month | 0 until triggered | Easy once live |

Required types: Creative (non-ICP) = #14 and #15. New Hire = #5. Lookalike = #9.

## Build first: Just Raised (#1)

- **Strongest signal:** a new round means hiring, and hiring means payroll and statutory filings. All three named customers are funded startups (case-studies.md).
- **Easiest data:** funding news is public, dated and clean.
- **Best story:** "you've just raised" is a natural, non-salesy opener, and it pairs with the 31 January return hook.
- **Weakness:** low volume (about 8 a month). Pair it with #3 Headcount Threshold to fill the pipeline, using the same Clay build.

**Status:** facts.md approved 2026-11-12; sender still TBD. Just Raised spec is STRUCTURE-APPROVED and in copy (`output/campaigns/just-started/workflow-spec.md`).
