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

**Current pricing:** Assumed base platform access is seat-based or enterprise-license based.

**Proposed AI pricing:** Bundle core evidence readiness workflow into an IRM Wizard package, then meter high-cost killer workflows by control, assessment, evidence packet, or audit cycle.

**Model:** Hybrid: seat/access for adoption plus outcome/usage-based pricing for heavy evidence package generation, advanced control mapping, and audit-ready outputs.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Monthly COGS rises from $2.10 to $6.30 per active user; gross margin remains about 79% at $30 revenue/user/month. | Keep the packaging model, but tighten cascading and reserve frontier models for high-risk outputs. |
| Heaviest segment doubles | Audit-prep leads and governance analysts could consume most high-cost mapping and package-generation tasks, increasing COGS unevenly. | Meter killer workflows by assessment, control family, or evidence packet; add usage alerts and fair-use thresholds. |
| Model provider raises prices 50% | Monthly COGS rises from $2.10 to about $3.15; gross margin remains about 90% if price and usage stay constant. | Use provider-neutral routing, shift low-risk tasks to backup models, cache reusable control context, and renegotiate based on volume. |

## Board One-Pager

**Before (traditional SaaS):** Value is captured mainly through access to workflow records, dashboards, and task tracking.

**After (AI-enabled):** Value is captured through completed evidence readiness outcomes: fewer manual collection hours, faster audit preparation, better evidence completeness, and current control-health signals.

**Net margin shift:** The base model is healthy because average AI COGS is low relative to assumed monthly revenue. Protect margin by bundling leader/filler features and metering killer workflows that create heavy inference or review cost.
