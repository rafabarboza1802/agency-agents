# Best Construction Inc. — Agent Team

A 13-agent team for running and growing Best Construction Inc., a California general contractor based in Pinole. The agents live in the `construction/` division and follow the same file format as every other agent in this repo. This folder holds the company configuration and the operating doctrine they share.

## What's here

| File | Purpose |
|------|---------|
| `company-profile.yaml` | **Company configuration.** Licences, registrations, insurance, bonding, service area, services, segment mapping, lead engines, crews, equipment, bid sources, systems, outreach and approval policy. Edit this file, not the agents. |
| `operating-rules.md` | Binding rules: the approval gate (G1–G9), what agents may do automatically, honesty limits |
| `handoffs.md` | Lifecycle handoff templates: Lead → Qualification → Estimate → Proposal → Follow-up → Won/Lost → Project → Billing/Closeout, plus Residential and PM/HOA engine stages |
| `loops/daily-lead-generation.md` | Loop 1, which runs all three lead engines |
| `loops/weekly-bid-pipeline.md` | Loop 2: bid calendar, go/no-go, estimates, proposals, submission checklist |
| `loops/active-project-delivery.md` | Loop 3: daily, weekly and monthly per-job cadence and closeout |
| `../runbooks/scenario-best-construction.md` | NEXUS runbook for the team (also registered in `strategy/runbooks.json` as `best-construction`) |

## The team

| # | Agent (`name`) | File in `construction/` | Engine / area |
|---|----------------|-------------------------|---------------|
| 1 | BC Chief of Staff | `construction-chief-of-staff.md` | Orchestrator and approval gate |
| 2 | BC Lead Intelligence Scout | `construction-lead-intelligence-scout.md` | Engine 1, Commercial / Public |
| 3 | BC Commercial Outreach Rep | `construction-commercial-outreach-rep.md` | Outreach and send queue (all engines) |
| 4 | BC Public Bid Hunter | `construction-public-bid-hunter.md` | Engine 1, public bids and compliance |
| 5 | BC Proposal and Bid Writer | `construction-proposal-bid-writer.md` | Proposals and bid packages |
| 6 | BC Estimator | `construction-estimator.md` | Takeoffs and pricing |
| 7 | BC Pipeline and Account Manager | `construction-pipeline-account-manager.md` | Qualification, CRM, contracts, accounts |
| 8 | BC Construction Project Manager | `construction-project-manager.md` | Delivery |
| 9 | BC Local Marketing Lead | `construction-local-marketing-lead.md` | Local SEO, GBP, ads, inbound routing |
| 10 | BC Safety and Cal-OSHA Advisor | `construction-safety-calosha-advisor.md` | Safety (advisory, flags for human review) |
| 11 | BC Finance and Job Costing Analyst | `construction-finance-job-costing.md` | Job cost, billing, retention, cash, QuickBooks |
| 12 | BC Residential Homeowner Lead Hunter | `construction-residential-homeowner-lead-hunter.md` | Engine 2, Residential |
| 13 | BC Property Management and HOA Lead Hunter | `construction-property-management-hoa-lead-hunter.md` | Engine 3, PM / HOA / Multifamily |

## Using the team from Claude Code

### 1. Fill in the company profile

Open `company-profile.yaml` and replace every `TBD` you can. The most important ones are the CSLB licence number and classes, DIR registration, SAM UEI, insurance limits, bonding limits, crews, equipment, and the specific agencies and portals you watch. Agents treat `TBD` as unknown and will block decisions that depend on it, such as a bonded bid when the bonding limit is unknown.

### 2. Install the agents

From the root of this repo:

```bash
./scripts/install.sh --tool claude-code --division construction
```

This copies the 13 agents into `~/.claude/agents/`. If you'll run Claude Code from a different folder, also copy the shared docs there:

```bash
mkdir -p ~/.claude/best-construction
cp -R strategy/best-construction/* ~/.claude/best-construction/
```

Alternatively, point the agents at the profile with `export BC_COMPANY_PROFILE=/path/to/company-profile.yaml`.

Agents look for the profile in this order: `$BC_COMPANY_PROFILE`, then `./strategy/best-construction/company-profile.yaml`, then `~/.claude/best-construction/company-profile.yaml`.

### 3. Talk to the Chief of Staff

Run the Chief of Staff as the **main session agent**, so it can coordinate the specialists as subagents:

```bash
claude --agent "BC Chief of Staff"
```

You can also start Claude Code normally and say "Activate BC Chief of Staff …". You don't pick specialists; the Chief of Staff routes the work.

Example requests:

```text
Run today's Daily Lead Generation loop across all three engines. Drafts only — give me the approval packet.

Here's a PlanetBids link for a city sidewalk project. Go/no-go, then estimate and draft the bid if it's a go.

Find HOT residential leads from ADU and driveway permits in Contra Costa this week.

Build an account plan for the three largest property-management companies in the East Bay.

We won the Hilltop HOA paver job. Set up the project: schedule, safety plan, budget, billing calendar.

Weekly bid pipeline review.

Job 0190 is running over on excavation. What's the margin impact and should we file a change order?
```

### 4. Approve

Every gated item comes back in a numbered approval packet. Reply with what you approve, for example: `Approve 1, 3. Edit 2: drop the price to the alternate. Skip 4.` Only the items you explicitly approve are sent, submitted or signed.

## Connected tools the agents expect

These are configured in `company-profile.yaml` → `systems`. When the matching connectors are available in your session, the agents use them:

- **HubSpot**: CRM
- **Apollo** and **Clay**: contacts and enrichment
- **Gmail**: drafts and approved sends
- **Google Calendar** and **Calendly**: meetings and site walks
- **Google Drive**: the folder for each project record
- **PandaDoc**: proposals
- **QuickBooks**: job cost, invoices and AR

Without a connector, the agents produce the same work as text and files for you to paste.

## Related skills

If the `best-construction-segments` and `bid-estimator` skills are installed, the agents defer to them: segment pitches and pricing tiers come from the first, and the estimating method from the second. Keep the `segments` mapping in `company-profile.yaml` consistent with the segments skill.

`skills/best-construction-segments.zip` is the current version of the segments skill, matching this config's three lead engines and segment mapping. To update the skill in your claude.ai account, upload that zip under Settings → Capabilities → Skills, replacing the old `best-construction-segments`. When you change `segments` or `lead_engines` in the profile, update the skill the same way.

## Staying in sync with upstream

The Best Construction team is additive. It adds a new division, docs under `strategy/best-construction/`, one runbook, and one-line registrations in the files the division checker enforces (`divisions.json`, `scripts/convert.sh`, `scripts/lint-agents.sh`, `.github/workflows/lint-agents.yml`, `scripts/install.sh`). It also refreshes `scripts/convert-outputs.sha256`. No upstream agent was changed. To pull upstream updates:

```bash
git remote add upstream https://github.com/msitarzewski/agency-agents.git   # once
git fetch upstream && git merge upstream/main
```

Conflicts, if any, will be in those one-line registrations or the manifest. Keep both sides, then run `scripts/test-convert-outputs.sh --update` and the checks below.

## Validation

```bash
./scripts/lint-agents.sh construction/*.md
./scripts/check-divisions.sh
./scripts/check-runbooks.sh
./scripts/check-agent-originality.sh construction/*.md
./scripts/test-convert-outputs.sh
```
