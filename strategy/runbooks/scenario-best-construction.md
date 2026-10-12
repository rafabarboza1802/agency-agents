# 🏗️ Runbook: Best Construction Inc. — Construction Company Operations

> **Mode**: NEXUS-Micro, run continuously as three loops | **Duration**: ongoing | **Agents**: 13 (`construction/` division)

This runbook adapts NEXUS to running a California general contractor rather than shipping software. The quality gate is the same idea, different gate: **nothing leaves the company without the owner's explicit approval**.

---

## Scenario

Best Construction Inc. (Pinole, CA; licensed California general contractor) wants a standing AI team that:

- Finds work through **three separate lead engines**: Commercial / Public, Residential, Property Management / HOA / Multifamily
- Qualifies, estimates, proposes and follows up
- Delivers won work safely and profitably, and gets paid

Company facts (licences, insurance, bonding, crews, equipment, service area, bid sources) live in `strategy/best-construction/company-profile.yaml`, not in agent prompts.

## Team

| Group | Agent | File |
|-------|-------|------|
| Command | BC Chief of Staff | `construction/construction-chief-of-staff.md` |
| Lead engine 1 — Commercial / Public | BC Lead Intelligence Scout | `construction/construction-lead-intelligence-scout.md` |
| | BC Public Bid Hunter | `construction/construction-public-bid-hunter.md` |
| Lead engine 2 — Residential | BC Residential Homeowner Lead Hunter | `construction/construction-residential-homeowner-lead-hunter.md` |
| Lead engine 3 — PM / HOA / Multifamily | BC Property Management and HOA Lead Hunter | `construction/construction-property-management-hoa-lead-hunter.md` |
| Sales & preconstruction | BC Pipeline and Account Manager | `construction/construction-pipeline-account-manager.md` |
| | BC Commercial Outreach Rep | `construction/construction-commercial-outreach-rep.md` |
| | BC Estimator | `construction/construction-estimator.md` |
| | BC Proposal and Bid Writer | `construction/construction-proposal-bid-writer.md` |
| Delivery | BC Construction Project Manager | `construction/construction-project-manager.md` |
| | BC Safety and Cal-OSHA Advisor | `construction/construction-safety-calosha-advisor.md` |
| | BC Finance and Job Costing Analyst | `construction/construction-finance-job-costing.md` |
| Growth | BC Local Marketing Lead | `construction/construction-local-marketing-lead.md` |

## Operating loops

| Loop | Cadence | Doc |
|------|---------|-----|
| Daily Lead Generation | Every business day | `strategy/best-construction/loops/daily-lead-generation.md` |
| Weekly Bid Pipeline | Weekly + when a bid is due inside 7 days | `strategy/best-construction/loops/weekly-bid-pipeline.md` |
| Active Project Delivery | Daily / weekly / monthly per job | `strategy/best-construction/loops/active-project-delivery.md` |

## Lifecycle and handoffs

`Lead → Qualification → Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout`, plus the engine-specific stages (Residential: outreach and site visit; PM/HOA: account qualification, decision-maker identification, vendor registration, property walk, recurring account). Templates: `strategy/best-construction/handoffs.md`.

## Quality gates

| Gate | Rule | Owner |
|------|------|-------|
| Approval gate | No email, proposal, bid, price, contract, purchase, submission or external communication without explicit, item-specific approval | BC Chief of Staff |
| Profile gate | No claim about licences, insurance, bonding, certifications, crews or references that isn't in the company profile | Every agent |
| Bid responsiveness | Compliance matrix 100% complete before a bid is put up for approval | BC Public Bid Hunter |
| Margin gate | Price at or above `min_margin_percent`, or the exception is shown to the owner | BC Estimator + BC Finance |
| Safety gate | Stop-work-level hazards escalated immediately; no excavation without a valid 811 ticket | BC Safety + BC Project Manager |

Binding rules: `strategy/best-construction/operating-rules.md`.

## Activation

```
Activate BC Chief of Staff. Load the Best Construction company profile and
operating rules, then run today's Daily Lead Generation loop across all three
lead engines. Prepare drafts only and give me the approval packet.
```
