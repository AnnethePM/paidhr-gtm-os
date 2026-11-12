# PaidHR ICP

Built only from `context/docs/research/`. Each line cites its research file. "Open question" = not supported by research yet.

## 1. Firmographic

Tiered by strength of evidence. Work Tier 1 first; Tiers 2 and 3 are bets until a named customer proves them.

| | Tier 1: proven core | Tier 2: PaidHR's stated push, unproven | Tier 3: stretch |
|---|---|---|---|
| Country | Nigeria (Lagos HQ) | Nigeria | Kenya, South Africa, Ghana |
| Headcount | About 20 to 100 | 100 to 200+ ("Enterprise" plan) | Any, if paying staff across borders |
| Industry | Tech-enabled startups (shipping, health tech, fintech) | Logistics, retail, manufacturing | Companies with staff in several countries |
| Stage | Funded startup | Established operator | Open question |
| Workforce | Desk-based | Shift, field or deskless (WhatsApp and USSD) | Mixed, multi-currency |
| Evidence | All 3 named customers (Heroshe, Famasi, Cleva); "Standard" plan "20 - 100 Employees"; about 60 employees per business on average (INFERRED: 25,000+ employees / 400+ businesses) | Accion press release (June 2025) names these sectors; LinkedIn targets "fast-growing and enterprise organizations"; WhatsApp and USSD built for deskless staff. No named customer | Markets claimed (Accion, TechArena); "$2M+" cross-border payments. No named customer outside Nigeria |
| Source | case-studies.md; company.md: Pricing; customers.md: Company sizes | customers.md: Industries, Company sizes; signals.md: 7 | company.md: Markets; signals.md: 5 |

**Conflict to resolve with PaidHR:** the 2025 story (SMEs under 200) and the 2026 story (enterprise) point at different tiers. If PaidHR's goal is enterprise, Tier 2 needs a named customer before outbound can lean on it (customers.md).

## 2. Technographic

| Today they use | Evidence | Source |
|---|---|---|
| Spreadsheets / Excel | "For Cleva, Excel served its purpose but as they grew" | signals.md: section 2 |
| Manual remittances and bank transfers | Famasi: "for remittances I had to do them individually" | customer-videos.md: Famasi |
| HR software that can't remit statutory deductions | Heroshe: "most HR software ... they're unable to help most HR professionals process [statutory] deductions" | customer-videos.md: Heroshe |
| Payroll still on pre-2026 tax bands | DLA: old bands produce incorrect deductions | market.md: Employer liability |
| Separate local and global payroll tools | "no more juggling between local and Global payroll tools" | customer-videos.md: Cross Border |

Open question: which named payroll or HR tools prospects use today (no data).

## 3. Intent signals

Only signals a rep can see from outside the company, before any conversation. Market-wide events are timing context, not signals. Full evidence in signals.md.

**Account signals (observable, use to build lists)**

| Signal | Why it points to PaidHR | How to detect | Evidence strength | Source |
|---|---|---|---|---|
| Headcount growing through about 20 to 200 | Plans start at "20 - 100 Employees"; Famasi switched "as a team [grew]" | LinkedIn company size and headcount (treg LinkedIn company profile tools) | 1 customer quote + pricing page | company.md: Pricing, Team size; customer-videos.md |
| Open roles in Nigeria, especially several at once | Hiring adds payroll and remittance work | Job postings (treg job tools: `akta.x.jobs` $0.02 per result; `mobiusengine-jobs.jobs.company` needs a key) | INFERRED, no customer evidence | signals.md: 4 |
| New funding round (seed to Series A) | All 3 named customers are funded startups | Funding news (e.g. Nairametrics funding round-ups) | 3 customers, pattern only | signals.md: 3; case-studies.md |
| Locations or job posts outside Nigeria (Kenya, Ghana, South Africa, UK, US) | Founder: core pain is "Compliance and cross-border payouts" | LinkedIn locations; job post locations | Founder quote; no cross-border customer named | signals.md: 5 |

**Timing context (applies to every Nigerian employer, use to frame outreach, not to pick accounts)**

| Event | Use | Source |
|---|---|---|
| First annual PAYE return under the new Act, due 31 Jan 2027 | Deadline hook from about Q4 2026 | market.md |
| Lagos enforcement (premises sealed, power of substitution) | Credibility for the compliance angle; verify before quoting | market.md: enforcement |
| Minimum wage review (due June 2027 per the minister) | Future hook if a new rate is set | market.md: minimum wage |

**Dropped:** "New HR, People or payroll hire". No research shows it predicts a purchase. Re-add once tested.

## 4. Persona

Full detail in personas.md.

| Role | Who | Source |
|---|---|---|
| Champion | HR or HR operations lead who runs payroll and remittances | customer-videos.md: Heroshe |
| Economic buyer | Founder or CEO who still runs payroll personally | customer-videos.md: Famasi; customers.md: Cleva |
| Influencer | Employees (pay on time, payslips, EWA) | signals.md: 1 ("Refer us to your employer"); company.md: PaidLife |

## 5. Engagement readiness

Qualified on the first call, not visible from outside. Each question maps to a pain a customer actually described.

| Discovery question | Ready if | Source |
|---|---|---|
| How do you remit PAYE and pension today, and how long does it take? | By hand, or takes days to weeks (Heroshe: "two weeks or more") | customer-videos.md: Heroshe |
| How do you confirm staff were paid? | Manual checks (Famasi: "individually text everyone") | customer-videos.md: Famasi |
| Who runs payroll, and how long does a run take? | Founder or HR lead, an hour or more (Famasi: "about one hour") | customer-videos.md: Famasi |
| Has payroll been updated for the 2026 tax bands? | Unsure, or done by hand | market.md |
| Have you had calls or letters from the tax office? | Yes | customer-videos.md: Heroshe |

**Not ready:** under 20 employees, or already on a tool that remits statutory deductions and is updated for the 2026 bands.

Sources: company.md: Pricing; customer-videos.md; market.md.

## Not a fit

| Who | Why | Source |
|---|---|---|
| Fewer than 20 employees | No plan listed below "20 - 100 Employees". INFERRED as a floor: research doesn't say PaidHR turns smaller teams away | company.md: Pricing |
| Needs employer of record to hire without an entity | PaidHR does not list EOR; Workpay and Remote do | competitors.md (research) |
| Payroll mainly outside Africa | Positioning is "HR management for the African context" | competitors.md (research): positioning |

## Open questions

- Which tier PaidHR wants outbound to target: Tier 1 (proven) or Tier 2 (enterprise push).
- Does PaidHR sell to teams under 20?
- Who is the economic buyer in Tier 2? Founder-run payroll (Famasi) likely doesn't hold at 100+ employees; no research on finance buyers.
- Exact upper headcount limit, if any, for Enterprise.
- Win rates by industry or country.
- What share of customers are outside Nigeria.
