# Cost Curve & Pricing Strategy

## Packaging Decision

**Hero SKU:** IRM Wizard Evidence Readiness Pilot

**Packaging model:** Hybrid: bundled access for the core workflow plus outcome/usage-based pricing for high-value evidence packets and reviewed control-health outputs.

| Packaging Question | Decision | Rationale |
|--------------------|----------|-----------|
| **Access or outcome?** | Closer to outcome | The user is not just buying access to an AI feature; they are buying reduced evidence collection effort, faster audit readiness, and leadership-ready control-health visibility. |
| **Leader** | Evidence readiness workflow | This is the feature users come for: create evidence requests, collect source artifacts, map evidence to controls, review quality, and publish control-health signals. |
| **Filler** | Drafting, summarization, formatting, and reminder nudges | Useful add-ons that improve analyst productivity and make the workflow feel polished, but they should not define the paid value alone. |
| **Killer** | High-volume automated control mapping, gap analysis, and audit-ready package generation | These can drive heavy inference and review cost. If usage is concentrated in fewer than 70% of users or tied to high-value audit events, package as usage-based or add-on rather than unlimited bundle. |
| **Killer usage %** | Expected below 70% in MVP | Not every user will generate high-volume audit packages. Governance analysts and audit-prep leads will likely drive most intensive usage. |
| **Bundle or add-on?** | Bundle the leader and filler; meter the killer | Core evidence readiness should be included to drive adoption. Heavy evidence package generation and advanced control mapping should be metered by control, assessment, evidence packet, or audit cycle. |

**70% rule:** If more than 70% of active users rely on a feature every cycle, bundle it into the base workflow. If usage is lower but high-value or high-cost, make it an add-on or usage-based tier.

## Cost Curve

| Feature | Complexity | Model Tier | Cost/Req | Volume % | Weighted |
|---------|------------|------------|----------|----------|----------|
| Draft evidence requests, reminders, formatting, and basic summaries | Simple | Small | $0.010 | 45% | $0.0045 |
| Evidence extraction, source matching, freshness checks, and packet assembly | Medium | Mid | $0.035 | 35% | $0.0123 |
| NIST 800-53 mapping, gap analysis, exception rationale, and leadership-ready summaries | Complex | Frontier | $0.090 | 20% | $0.0180 |
| **Blended** |  |  |  | **100%** | **$0.0348** |

**Blended cost per request:** Approximately **$0.035**.

**Cost curve readout:** Most interactions should stay in small or mid-tier models. Frontier usage is reserved for defensibility-sensitive work where mistakes would create audit, compliance, or leadership risk.

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $1.20 | Assumes high-risk tasks such as control mapping, gap analysis, and final leadership summaries use the stronger model. |
| Inference (cascading/triage) | $0.45 | Assumes drafting, extraction, summarization, reminders, and formatting mostly use a lower-cost model. |
| Infrastructure | $0.20 | Workflow orchestration, logging, monitoring, and secure API/service costs. |
| Data/storage | $0.15 | Evidence metadata, lineage, mappings, review decisions, and reusable pattern libraries. |
| Human-in-the-loop | $0.10 | Incremental review operations for flagged outputs; core analyst labor is not counted as AI COGS. |
| **Total AI COGS** | **$2.10** | Base-case AI cost per active user per month. |

## Margin Calculator

| Input | Your Number | Stress (3x) |
|-------|-------------|-------------|
| Avg requests/user/month | 60 | 60 |
| Cost per request (blended) | $0.035 | $0.105 |
| Monthly COGS per user | $2.10 | $6.30 |
| Revenue per user/month | $30.00 | $30.00 |
| Gross margin per user | $27.90 | $23.70 |
| Gross margin % | 93% | 79% |

**Margin readout:** The model remains above the 40% gross margin stress threshold even if inference cost triples. The bigger margin risk is not average usage; it is concentrated killer usage from high-volume control mapping, gap analysis, and audit package generation.

## Cascading Strategy

**Triage model:** Lower-cost model for drafting evidence requests, summarizing artifacts, extracting metadata, generating reminders, formatting evidence packets, and preparing first-pass summaries.

**Frontier model:** Stronger model for NIST 800-53 mapping, gap analysis, ambiguous control interpretation, exception rationale, and final leadership-ready control-health summaries.

**Routing rule:** Route low-risk productivity tasks to the triage model by default. Escalate to the frontier model when the task affects audit defensibility, control coverage, regulatory interpretation, leadership reporting, or low-confidence evidence mapping.

**Expected cascade ratio:** 70% triage / 30% frontier in the MVP. Target 80% triage / 20% frontier after evals prove quality on routine evidence tasks.

## Pricing Model

**Pricing strategy:** Penetrate first, then maximize.

Start by making the core evidence readiness workflow easy to adopt for governance analysts and control owners. Once usage proves time savings, audit readiness improvement, and leadership value, expand pricing around completed evidence packets, reviewed control mappings, and audit-cycle outcomes.

**Unit of work:** Reviewed evidence packet.

A reviewed evidence packet includes the evidence request, source artifacts, owner attribution, freshness check, control-objective mapping, quality review status, exception notes, and leadership-ready control-health signal.

**Current pricing:** Assumed base platform access is seat-based or enterprise-license based.

**Proposed AI pricing:** Base fee of **$30/user/month** for the core workflow, plus usage pricing for reviewed evidence packets and high-cost audit outputs.

**Structure:**
- **Base:** $30/user/month for evidence request orchestration, basic drafting, summaries, reminders, and workflow visibility.
- **Usage:** $5/reviewed evidence packet for validated evidence lineage, control mapping, freshness checks, exception rationale, and control-health signal generation.
- **Audit cycle add-on:** Enterprise package for high-volume audit preparation, large control families, or quarterly assessment events.

**Model:** Hybrid: seat/access for adoption plus outcome/usage pricing for reviewed evidence packets, advanced control mapping, and audit-ready outputs.

**Labor test:** If manual evidence coordination takes even 30 minutes of analyst time per evidence packet, a $5 reviewed-packet fee is materially cheaper than manual work at typical GRC labor rates. This supports outcome pricing without making the product feel like a usage tax.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Monthly COGS rises from $2.10 to $6.30 per active user; gross margin remains about 79% at $30 revenue/user/month. | Keep the packaging model, but tighten cascading and reserve frontier models for high-risk outputs. |
| Heaviest segment doubles | Audit-prep leads and governance analysts could consume most high-cost mapping and package-generation tasks, increasing COGS unevenly. | Meter killer workflows by assessment, control family, or evidence packet; add usage alerts and fair-use thresholds. |
| Model provider raises prices 50% | Monthly COGS rises from $2.10 to about $3.15; gross margin remains about 90% if price and usage stay constant. | Use provider-neutral routing, shift low-risk tasks to backup models, cache reusable control context, and renegotiate based on volume. |

## Board One-Pager

### Before: Traditional SaaS

| Metric | Assumption |
|--------|------------|
| Revenue | $30/user/month x 1,000 users = $30,000/month |
| COGS | $3,000/month fixed platform, workflow, support, and storage costs |
| Gross margin | 90% |
| Pricing narrative | Customers pay for access to workflow records, dashboards, and task tracking. Value is real, but pricing is weakly connected to completed evidence outcomes. |

### After: AI-Powered

| Metric | Assumption |
|--------|------------|
| Revenue | $30/user/month base x 1,000 users + $5/reviewed evidence packet x 2,000 packets = $40,000/month |
| COGS | $2.10 AI COGS/user/month x 1,000 users + estimated $3,000 platform/support costs = $5,100/month |
| Gross margin | 87% |
| Pricing narrative | Customers pay for a workflow plus reviewed evidence outcomes: fewer manual collection hours, faster audit prep, clearer evidence ownership, and leadership-ready control-health signals. |

### Net Margin Shift

| Measure | Shift |
|---------|-------|
| Revenue | +$10,000/month |
| Gross profit | From $27,000/month to $34,900/month |
| Gross margin % | From 90% to 87% |
| Board interpretation | Margin percentage decreases slightly because AI introduces variable COGS, but gross profit and net revenue retention potential improve because pricing is tied to completed evidence outcomes. |

**Board narrative:** This is a good trade: AI lowers margin percentage modestly but expands monetizable value. We should protect margin by bundling leader/filler workflows, metering high-cost killer workflows, and keeping frontier model usage reserved for defensibility-sensitive work.
