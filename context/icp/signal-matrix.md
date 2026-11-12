# PaidHR signal matrix

Work in progress, to validate with PaidHR sales. Built from `context/icp/icp.md`, `context/icp/personas.md`, `context/docs/research/`, and the method in `knowledge-base/playbooks/signal-matrix-framework.md` and `workflow-anatomy.md`. INFERRED = not supported by research.

## Matrix 1: Segments x personas

Segments are the ICP tiers (icp.md). Single product, so one angle per cell.

| Segment | Target definition (filterable) | Champion: HR ops lead | Economic buyer | Influencer: employees | Priority |
|---|---|---|---|---|---|
| **S1. Funded Nigerian tech startups** | Nigeria HQ, 20 to 100 employees, raised seed to Series A, tech-enabled | Remittances done by hand take weeks; get receipts and time back (Heroshe) | Founder/CEO: get back the hour each payroll run takes (Famasi) | Payslips without asking HR; earned pay before payday | **High**: all 3 named customers fit |
| **S2. Nigerian operators with deskless staff** | Nigeria HQ, 100 to 200+ employees, logistics, retail or manufacturing | Remit tax and pension for a large shift workforce on the 2026 bands, with proof | INFERRED: COO or finance lead (no research). Angle: one record of statutory filing, "Zero" defaults | HR on WhatsApp and USSD, "No internet? No problem." | **Medium**: PaidHR's stated push, no named customer |
| **S3. Nigerian companies paying staff abroad** | Nigeria HQ with staff or job posts in Kenya, Ghana, South Africa, UK or US | One dashboard for local and cross-border pay | Founder/CEO: stop juggling local and global payroll tools | Paid in their currency, wallet to convert or spend | **Medium**: founder names cross-border as a core pain; no named customer |

Company examples: S1 lookalike seeds are Heroshe, Famasi, Cleva (case-studies.md). Other names: requires Clay research with the target-definition filters above. No names fabricated.

Sources: icp.md (tiers); personas.md; value-proposition.md; customer-videos.md; signals.md.

## Matrix 2: Signals

Scores: H / M / L on the four tests. Status per the Iron Law forcing question.

| # | Signal | Type | Segments | Mother intent | Data source | Tool | Buying reason | Volume | Data | Story | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | New funding round, last 90 days | Universal | S1 | Funding: companies fundraising | Nigerian funding news (Nairametrics round-ups, TechCabal); Crunchbase | Crunchbase via Clay "Find Organization"; `treg.web.search` | H (INFERRED: hiring and payroll follow) | L to M (51 disclosed deals H1 2026, market.md) | H | H | VERIFIED |
| 2 | Open HR, People or payroll role in Nigeria | Universal | S1, S2 | Hiring specific roles | Job postings; titles "HR Manager", "People Operations", "Payroll Officer" | Clay "Find Jobs at Company"; treg `akta.x.jobs` ($0.02 per result) | M (INFERRED: new owner of payroll) | M (INFERRED) | M (Nigerian job-board coverage unknown) | H | VERIFIED (test coverage first) |
| 3 | Headcount crosses about 20 or 100, or grows 25%+ in 6 months | Universal | S1, S2 | Hypergrowth (headcount) | LinkedIn company headcount, monthly snapshots | treg `fetchinio.linkedin.company.profile` ($0.0015 per call); Clay "Enrich Company" | M (Famasi switched "as a team [grew]") | H | H | M | VERIFIED |
| 4 | Several open roles at once | Universal | S1, S2 | Hypergrowth (hiring velocity) | Job postings, count per company | Clay "Find Jobs" + count; treg `akta.x.jobs` | M (INFERRED) | H | M | M | VERIFIED |
| 5 | Job posts or LinkedIn locations outside Nigeria | Universal | S3 | Hiring offshore / team offshore | Job post locations; LinkedIn company locations | Clay "Find Jobs" location filter; treg LinkedIn profile `locations` | H (founder: "Compliance and cross-border payouts") | L (INFERRED) | M | H | VERIFIED |
| 6 | Lookalike of Heroshe, Famasi, Cleva | Universal | S1 | Lookalike of customers | Customer domains | Clay lookalike | L to M | M | H | M | VERIFIED (only 3 seeds) |
| 7 | Multi-site operator (store or depot count) | Niche | S2 | Niche-specific play | Google Maps location count | Google Places API via Clay HTTP | M (INFERRED: deskless staff) | M | M | M | VERIFIED (COMPOUND, INFERRED) |
| 8 | Attending or sponsoring Moonshot 2026 or HR Expo Africa | Universal | S1, S2 | Companies attending/sponsoring an event | Event sponsor and speaker pages | Clay HTTP scrape | M | L | M | H | VERIFIED (PARTIAL: seasonal) |
| 9 | Nigeria Tax Act 2025: first annual return due 31 Jan 2027 | Universal | All | Regulatory changes | market.md (DLA Piper, Legit.ng) | None: applies to every employer | H | n/a | n/a | H | COMPOUND only: narrative layer on 1 to 5 |
| 10 | New HR or People leader, last 90 days | Universal | S1, S2 | New leadership | LinkedIn people data | Clay "Find People" title + start date | INFERRED (dropped from ICP: untested) | M | M | H | ON HOLD: test before building |
| 11 | Using a competitor payroll tool | n/a | All | Companies using specific software | BuiltWith | Clay "Find Technology Stack" | M | n/a | L | M | KILLED: BuiltWith can't detect payroll software (framework) |
| 12 | LSETF programme beneficiaries | Niche | S1 | Niche-specific play | LSETF lists | n/a | M | L | L | M | KILLED: names not public (customers.md) |

**Compounding:** 8 of the 10 live signals are universal (one Clay build, keywords and angle change per segment). The Google Maps play (7) is the only niche build. Signal 9 is not a list source; it sits on top of every workflow as the "why now".

## Build first

| Rank | Signal | Why |
|---|---|---|
| 1 | #1 New funding round (S1) | Only signal that matches all 3 named customers; clean data; strongest story ("you've just raised, payroll is next"). Low volume, so pair with #3 |
| 2 | #3 Headcount crosses 20 or 100 (S1, S2) | Highest volume and cheapest data ($0.0015 per company); maps to PaidHR's plan thresholds and Famasi's switch trigger |
| 3 | #2 HR or payroll role posted (S1, S2) | Direct link to the champion persona; strong story. Test Nigerian job coverage on 20 known companies before scaling |
| 4 | #5 Expansion outside Nigeria (S3) | Founder's stated core pain; fits the cross-border product. Low volume, so run as a small targeted workflow |

Every workflow layers #9 (31 Jan 2027 return) as the timing hook from Q4 2026.

## Matrix 3: Workflow tracker

| W # | Status | Workflow | Mother intent | Segment | Launched | Sent | Replies | Meetings | Notes |
|---|---|---|---|---|---|---|---|---|---|
| W1 | Planned | Funding round to payroll | Fundraising | S1 | | | | | |
| W2 | Planned | Headcount threshold | Hypergrowth (headcount) | S1, S2 | | | | | |
| W3 | Planned | HR or payroll role posted | Hiring specific roles | S1, S2 | | | | | |
| W4 | Planned | Cross-border expansion | Hiring offshore | S3 | | | | | |
| W5 | Planned | Hiring velocity | Hypergrowth (hiring) | S1, S2 | | | | | |
| W6 | Planned | Customer lookalike | Lookalike | S1 | | | | | |
| W7 | Planned | Multi-site operator | Niche-specific | S2 | | | | | |
| W8 | Planned | Event attendees | Events | S1, S2 | | | | | |

## Open questions

- Which segment PaidHR wants outbound to lead with (icp.md).
- The S2 economic buyer (no research on finance or COO buyers).
- Volume of Nigerian job postings in Clay and treg job tools.
