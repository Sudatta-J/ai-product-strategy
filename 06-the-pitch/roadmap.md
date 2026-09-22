# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Ship (0-4 weeks)
*High-confidence capabilities required to establish the trusted AC-2 workflow.*

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| IRM-1 Evidence ingestion foundation | Bet | Trusted evidence ingestion is the minimum viable product foundation. | H |
| IRM-2 Define canonical evidence schema | Moat | A provider-neutral schema creates reusable data assets and reduces platform lock-in. | H |
| IRM-3 Build IRM Wizard evidence task connector | Bet | The pilot needs live requests, owners, deadlines, and control references. | H |
| IRM-4 Connect identity access review exports | Bet | IAM exports supply the primary evidence for the AC-2 use case. | H |
| IRM-5 Add evidence freshness and lineage checks | Contract | Trust depends on proving where evidence came from and whether it remains current. | H |
| IRM-6 AC-2 mapping and readiness assessment | Bet | This is the core customer outcome and pilot scope. | H |
| IRM-7 Implement AC-2 control requirement parser | Contract | Structured obligations are required for consistent, testable mappings. | H |
| IRM-8 Generate evidence-to-control mapping recommendations | Contract | This delivers the core AI value while preserving human approval. | H |
| IRM-9 Detect missing and stale AC-2 evidence | Contract | Preventing false PASS decisions is a release requirement. | H |
| IRM-11 Human review and confidence UX | Contract | The product cannot launch credibly without visible uncertainty and review controls. | H |
| IRM-12 Display confidence tiers and evidence rationale | Contract | Reviewers need citations, rationale, and uncertainty before trusting recommendations. | H |
| IRM-16 Evaluation and governance controls | Guardrails | Evaluation and governance must be part of the MVP architecture. | H |
| IRM-17 Automate the AC-2 golden dataset | Contract | The 10-case dataset provides the initial release gate and regression baseline. | H |
| IRM-18 Enforce agent tool-call allowlist | Guardrails | Unapproved agent actions create immediate security and audit risk. | H |
| IRM-19 Implement privacy and retention controls | Guardrails | The pilot processes sensitive access-control evidence in a regulated environment. | H |

### Horizon 2 — Validate (1-3 months)
*Medium-confidence bets with explicit hypotheses and six-week kill criteria.*

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| IRM-10 Create control-health summary model | Bet | Reviewed evidence can become an actionable leadership signal rather than another status report. | If fewer than 3 of 5 pilot leaders can identify the top gap and accountable owner from the summary by week 6, we stop. | M |
| IRM-13 Build reviewer correction workflow | Moat | Captured corrections will improve future mappings and strengthen the recursive learning loop. | If at least 80% of corrections are not captured structurally or repeat errors do not fall 20% by week 6, we stop. | M |
| IRM-14 Add risk-based human escalation queue | Guardrails | Risk-based routing will reduce manual review without weakening oversight. | If fewer than 70% of escalations reach the correct reviewer or queue volume does not decline by week 6, we stop. | M |
| IRM-21 Pilot reporting and adoption | Bet | A controlled AC-2 pilot will reduce evidence-cycle time and earn analyst trust. | If five analysts and two control owners are not active weekly, or median cycle time does not improve 25% by week 6, we stop. | M |
| IRM-22 Create analyst evidence readiness dashboard | Bet | A unified queue will reduce status chasing and make evidence gaps actionable. | If weekly dashboard use stays below 70% of pilot analysts or status-chasing time does not fall 25% by week 6, we stop. | M |
| IRM-23 Create CISO control-health briefing | Bet | Leadership will value a current, evidence-linked AC-2 view over manually assembled reporting. | If leaders cannot identify posture, top gaps, and owners in under five minutes by week 6, we stop. | M |
| IRM-24 Measure pilot value and model economics | Margin | The workflow can reduce reviewer effort while holding AI COGS near $2.10 per user monthly. | If reviewer effort does not fall 30% or projected gross margin drops below 40% under the 3x cost stress by week 6, we stop. | M |
| IRM-25 Complete pilot go/no-go review | Bet | An explicit decision gate will prevent expansion before trust, adoption, and economics are proven. | If the team cannot produce complete evidence for all five decision dimensions by week 6, we stop expansion. | M |

### Horizon 3 — Explore (3-6 months)
*A low-confidence, small-investment experiment against the clearest platform vulnerability.*

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| IRM-20 Run AI provider swap fire drill | Moat | The canonical schema, routing abstraction, backup-provider access, and automated evaluation harness must work before testing a 48-hour swap. | L |

**Cut from roadmap:** IRM-15 Draft evidence owner follow-up messages. It is a peripheral convenience feature that does not materially prove evidence quality, reviewer trust, defensibility, or economics.

## Board Pitch

**Thesis (1 sentence):**

**The case:**
1. Why now:
2. What's defensible:
3. The economics:

**The risks:**
1. Trust / failure modes:
2. Scale / governance:
3. Competitive:

**The ask:**

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:**

**Now:**
