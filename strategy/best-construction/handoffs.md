# Best Construction Inc. — Opportunity Lifecycle Handoffs

One opportunity moves through eight stages. Each stage has an owner agent, an exit gate, and a handoff block the owner fills in before the next agent starts. The BC Chief of Staff routes every handoff and keeps the stage current in the CRM.

```
Lead → Qualification → Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout
```

| Stage | Owner (primary) | Contributors | Exit gate | Approval needed to exit? |
|-------|-----------------|--------------|-----------|--------------------------|
| 1. Lead | Lead Intelligence Scout, Public Bid Hunter (Commercial/Public) · Residential Homeowner Lead Hunter · PM & HOA Lead Hunter | Local Marketing Lead (inbound routing) | Lead record exists with source + signal | No |
| 2. Qualification | Pipeline & Account Manager | Public Bid Hunter (public), Safety (site risk) | Go / No-go recommendation | **Yes** — approver confirms Go before estimating time is spent on large or bonded jobs |
| 3. Estimate | Estimator | Finance & Job Costing, Safety, Project Manager | Priced estimate with risk register | No (internal) |
| 4. Proposal | Proposal & Bid Writer | Estimator, Public Bid Hunter (compliance) | Complete draft package | **Yes** — G2/G3/G4 before anything is sent or submitted |
| 5. Follow-up | Commercial Outreach Rep | Pipeline & Account Manager | Decision received or opportunity aged out | **Yes** — G1 for each follow-up message |
| 6. Won/Lost | Pipeline & Account Manager | Finance (won), Chief of Staff (lost review) | Contract review done (won) or loss logged (lost) | **Yes** — G5 before any contract is signed |
| 7. Project | Construction Project Manager | Safety, Finance & Job Costing | Substantial completion + punch list closed | **Yes** — G1/G5/G6 for owner communications, change orders, purchases |
| 8. Billing/Closeout | Finance & Job Costing | Project Manager, Account Manager | Final payment + retention received, closeout docs delivered, review/referral asked | **Yes** — G1/G8 for invoices, lien releases, reminders |

## Engine-specific paths

The eight core stages above are shared. The Residential and Property Management / HOA engines add stages in front of Estimate; the Chief of Staff tracks these as sub-stages of Qualification in the CRM.

| Engine | Path |
|--------|------|
| 1. Commercial / Public | Lead → Qualification → Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout |
| 2. Residential | Residential Homeowner Lead Hunter → Lead Qualification → **Outreach** → **Site Visit** / Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout |
| 3. PM / HOA / Multifamily | PM & HOA Lead Hunter → **Account Qualification** → **Decision-Maker Identification** → **Vendor Registration** → **Outreach** → **Meeting / Property Walk** → Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout → **Recurring Account / Additional Properties** |

Engine-specific handoff blocks are at the end of this document.

---

## Common header (every handoff)

```markdown
# BC Handoff — [Stage N → Stage N+1]
- Record ID: BC-YYYY-NNNN
- Opportunity: [project name / address / agency + solicitation no.]
- Segment: [home builder | GC | property manager/HOA/facilities | developer | public agency | prime (we are sub)]
- From: [agent]   To: [agent]   Date: [YYYY-MM-DD]
- Key dates: [bid due / site walk / RFI deadline / start / completion]
- Profile facts relied on: [licence class, bonding, insurance etc. — cite company-profile.yaml keys]
- Unknowns / blockers: [list, or "none"]
- Pending approvals: [G-codes + item, or "none"]
- Links: [CRM record, Drive folder, solicitation, drafts]
```

---

## 1 → 2 · Lead → Qualification

```markdown
## Lead
- Source: [permit portal | planning agenda | bid board | GC invite | inbound web/phone | referral | Apollo/Clay search]
- Signal: [what happened, date, link — e.g. "demo permit issued 2026-10-03 for 12 units, 1450 Main St"]
- Scope guess: [which of our services, from company-profile.yaml services ids]
- Decision maker(s): [name, title, verified email? Y/N, source]
- Size guess: [$ range or SF/LF/CY]
- Distance from Pinole: [miles]
- Why now: [one line]
```

## 2 → 3 · Qualification → Estimate

```markdown
## Qualification
- Recommendation: GO | NO-GO | GO WITH CONDITIONS
- Fit: [services match? licence class covers scope? inside service radius?]
- Requirements check: [bond % and amount vs. bonding limits; insurance limits vs. ours; DIR/prevailing wage; SBE/DBE goals; mandatory pre-bid; experience minimums]
- Competition & relationship: [known bidders, incumbent, our history with this buyer]
- Win probability: [%] and why
- Capacity: [crew/equipment availability for the likely schedule]
- Effort to bid: [hours] vs. expected value
- Approver decision: [quote + date]  ← required for bonded/public or > preferred_project_size max
```

## 3 → 4 · Estimate → Proposal

```markdown
## Estimate
- Basis: [plans/specs rev + date, site visit Y/N, photos, addenda acknowledged #1..#n]
- Quantities: [takeoff summary by line item]
- Direct cost: labour $ / equipment $ / materials $ / subs $ / disposal & haul $ / permits & fees $
- Indirects: [supervision, mobilization, insurance, bond premium, prevailing-wage burden]
- Markup: overhead % / profit % → total $
- Break-even price: $   Walk-away price: $
- Alternates / add-alternates / unit prices: [list]
- Exclusions & assumptions: [list]
- Risk register: [risk, likelihood, cost impact, mitigation]
- Safety notes: [hazards that drive cost: shoring, silica, lead/asbestos survey, traffic control]
```

## 4 → 5 · Proposal → Follow-up

```markdown
## Proposal
- Package: [proposal / bid form / sub quote] — link to DRAFT
- Compliance matrix: [every required form/item → included Y/N]
- Price as approved: $ [approval quote + date]  ← must exist before sending
- Sent/submitted: [how, when, to whom, confirmation no.]
- Decision expected: [date]
- Follow-up plan: [cadence and angle per touch]
```

## 5 → 6 · Follow-up → Won/Lost

```markdown
## Follow-up log
- Touches: [date, channel, approved Y/N, response]
- Buyer feedback: [questions, objections, scope changes]
- Bid results (public): [bid tab link, our rank, low bid, spread %]
- Outcome: WON | LOST | NO DECISION
```

## 6 → 7 · Won → Project  (or Lost → Learning)

```markdown
## Won
- Contract type: [lump sum | unit price | T&M | subcontract]  Value: $
- Contract review: [flagged clauses — pay-when-paid, indemnity, retention %, LDs, insurance/AI requirements, flow-down]
- Signed by approver: [date]  ← G5
- Required before mobilization: [COI, bonds, DIR project registration, permits, submittals, safety plan]
- Budget handed to Finance: [cost codes from estimate]

## Lost
- Reason: [price | scope | relationship | compliance | timing]
- Price gap: [our $ vs. winner $, %]
- Lesson for Estimator / Proposal Writer: [one line each]
- Re-engage date: [when to approach this buyer again]
```

## 7 → 8 · Project → Billing/Closeout

```markdown
## Project status
- Schedule: [planned vs. actual, % complete]
- Change orders: [CO#, description, $, status: draft | approved by us | executed by owner]
- RFIs/submittals open: [count + oldest]
- Safety: [incidents, near misses, open corrective actions]
- Billing: [pay apps submitted, amounts, retention held]
- Punch list: [open items]
- Closeout deliverables: [as-builts, warranties, O&M, lien releases, CalGreen diversion report, certified payroll complete]
```

## 8 · Billing/Closeout → Done

```markdown
## Closeout
- Final contract value: $   Final cost: $   Gross margin: $ / %
- Estimate vs. actual by cost code: [biggest variances + cause]
- Retention: [amount, release date, collected Y/N]
- Lien releases exchanged: [conditional/unconditional, progress/final]
- AR status: [current / 30 / 60 / 90+]
- Client review & referral request: [drafted → approved → sent]
- Feed-back to Estimator: [unit-cost updates]
```

---

## Residential engine — extra blocks

### Lead → Lead Qualification (Residential Hunter → Pipeline & Account Manager)

```markdown
## Residential lead
- Lead name: [only if lawfully public; else "Homeowner"]   Location: [address / city / county]
- Source: [permit portal | planning record | platform | website | GBP | ad | referral] + link + date
- Intent signal: [e.g. ADU permit issued 2026-10-07]
- Likely project: [service ids]   Estimated range: [$ or "insufficient evidence"]
- Score: [0–100] = intent · recency · value · geo · service · contact · active   Class: HOT | WARM | NURTURE | LOW
- Contact basis: [consented inbound | public business contact | mail only]   Suppression checked: Y
- Recommended next action: [ ]
- Draft outreach: [link — DRAFT — NOT APPROVED]
```

### Outreach → Site Visit / Estimate (Outreach Rep → Estimator)

```markdown
## Site visit request
- Homeowner availability: [ ]   Access notes: [gate, pets, parking]
- What they asked for, in their words: [ ]
- Photos/measurements already received: [links]
- Budget or timeline mentioned: [ ]
- Confirmation message to homeowner: [draft — needs approval]
```

## Property Management / HOA engine — extra blocks

### Account Qualification → Decision-Maker Identification

```markdown
## Account
- Company / association: [ ]   Website: [ ]   Portfolio: [# properties / units, counties]
- Property type mix: [apartments | condos | HOA | mixed]
- Capital-improvement evidence: [reserve study, CIP, acquisition, RFP] + source + date
- Vendor program: [portal, requirements: insurance limits, W-9, licence, COI wording] vs. profile → gaps
- Score: [0–100] Class: [ ]   Recurring potential: [ ]
```

### Decision-Maker Identification → Vendor Registration → Outreach

```markdown
## Org map (Company → Regional managers → Properties → Opportunities → Contacts)
| Level | Name | Title | Business email (verified on) | Business phone | Properties covered |
Vendor registration packet: [draft link] — submission requires approval (G7)
Outreach plan: [intro / vendor-partnership / property-specific / meeting request — drafts]
```

### Meeting / Property Walk → Estimate

```markdown
## Property walk
- Property: [name, address, units, year built]   Attendees: [ ]
- Conditions observed: [item, location, qty, photo ref, urgency: safety | near-term | planned]
- Board/approval process: [who approves, next board meeting, # bids required]
- Requested deliverable: [line-item bid by area | option tiers | budget number for reserve planning]
```

### Won/Lost → Recurring Account / Additional Properties

```markdown
## Account expansion
- Jobs completed at this account: [list, $, satisfaction notes]
- Other properties with the same need: [property, need, est. $]
- Proposed next step: [master service agreement | annual pricing | property-walk tour of region]
- Drafts for approval: [expansion email, case study]
```
