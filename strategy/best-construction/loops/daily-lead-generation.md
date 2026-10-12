# Loop 1 — Daily Lead Generation

**Cadence:** every business day · **Run by:** BC Chief of Staff · **Time box:** ~60–90 min of agent work, ~10 min of approver review

## Three separate lead engines

The loop runs three engines side by side. Their targeting, scoring and outreach stay separate; they meet only in the Chief of Staff's briefing and the shared approval queue.

| Engine | Lead agents | Targets | Scoring | First-touch style |
|--------|-------------|---------|---------|-------------------|
| 1. Commercial / Public | BC Lead Intelligence Scout, BC Public Bid Hunter | GCs, developers, home builders, commercial real estate, government, utilities, primes | Go/no-go + win probability | Signal-based business email; public bids through the solicitation only |
| 2. Residential | BC Residential Homeowner Lead Hunter | Homeowners with identifiable intent | 0–100 intent score | Consented inbound: reply fast. Permit-only leads: mailed letter / door hanger |
| 3. PM / HOA / Multifamily | BC Property Management and HOA Lead Hunter | Apartment communities, condos, HOAs, PM and CAM companies, multifamily owners | 0–100 account score (account-based) | Vendor-partnership email to the real decision-maker; property-specific notes |

## Roster

| Step | Agent | Output |
|------|-------|--------|
| 1a | BC Lead Intelligence Scout | 10–20 commercial signals, scored, deduplicated against CRM |
| 1b | BC Public Bid Hunter | New public solicitations + prime sub-bid invites since yesterday |
| 2 | BC Residential Homeowner Lead Hunter | HOT/WARM homeowner leads with lead cards and outreach drafts |
| 3 | BC Property Management and HOA Lead Hunter | Account and property opportunities, org-map updates, vendor-registration drafts, outreach drafts |
| 4 | BC Local Marketing Lead | Inbound leads (web, GBP, ads, platforms, referrals) routed to the right engine |
| 5 | BC Pipeline and Account Manager | Qualifies top items from every engine; updates CRM stages |
| 6 | BC Commercial Outreach Rep | Commercial drafts + compliance check and send queue for all engines (≤ daily cap) + due follow-ups |
| 7 | BC Chief of Staff | Assembles the **Daily Leads** briefing (one section per engine) and the approval packet |

## Steps

1. **Load context.** Chief of Staff reads `company-profile.yaml`, yesterday's briefing, and open approvals still waiting.
2. **Run the engines in parallel** (steps 1a–4 above). Each engine uses only its own segments from `lead_engines` in the profile. A signal that belongs to another engine is handed across, not worked.
3. **Dedupe + record IDs.** One record per opportunity (PM/HOA: one account record with property-level opportunities). Out-of-area or out-of-licence items are parked with the reason.
4. **Qualify (Pipeline Manager).** Commercial: Go / No-go / Watch for the top 5 and every public posting due in ≤ 21 days. Residential and PM/HOA: confirm HOT/WARM scores and next actions.
5. **Draft outreach.** Commercial Outreach Rep drafts commercial touches and checks the hunters' drafts (segment, verified contact, suppression list, legal footer). Everything stays a **draft**.
6. **Briefing (Chief of Staff).** Email **draft** to `outreach_policy.daily_briefing.to` with subject `Daily Leads — {date}`:
   - Engine 1 — Commercial / Public: top opportunities and new public bids with due dates and recommendations
   - Engine 2 — Residential: HOT and WARM leads (score, signal, next action)
   - Engine 3 — PM / HOA / Multifamily: HOT/WARM accounts and property opportunities (score, decision-maker, next action)
   - Approval list: each draft with a one-line summary and `APPROVE / EDIT / SKIP`
   - Deadlines in the next 7 days
   - Blockers (profile `TBD`s that blocked a decision)
7. **Approve.** The approver replies per item. Only items explicitly approved are sent, then logged.

## Daily metrics

Per engine: new qualified leads · HOT/WARM count · drafts approved / sent · replies · meetings booked · public bids added to pipeline · days-to-first-touch on Tier-1 signals.
