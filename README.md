# AI Product Strategy

> IRM Wizard can reduce manual evidence collection and improve audit readiness by turning fragmented evidence tasks into a guided, reviewable, and leadership-ready control-health workflow.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|--------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, and why now.**

- **Product:** IRM Wizard Evidence Readiness Pilot for governance analysts, control owners, evidence owners, and CISO leadership stakeholders.
- **Bet Summary:** IRM Wizard can reduce manual evidence collection and improve audit readiness by turning fragmented evidence tasks into a guided, reviewable, and leadership-ready control-health workflow.
- **AI Value Archetype:** Orchestrator and copilot. AI coordinates cross-functional work, drafts structured outputs, checks evidence readiness, and surfaces decision-ready signals while preserving human review gates.
- **Vulnerability Scores:** Moat 4/5 · Data 4/5 · Platform 2/5
- **Top Risk:** Platform exposure. Incumbent IRM or security platforms could embed similar evidence collection, control mapping, and control-health reporting directly into their existing workflows.
- **Confidence:** Medium
- **Prototype:** [`01-the-bet/prototype.md`](01-the-bet/prototype.md)
- **Kill Criteria:** Stop or pivot if users cannot connect enough trusted evidence sources, control owners do not trust generated mappings, review effort is not materially reduced, or leadership does not find the control-health signal actionable.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in six months.**

- **Data Flywheel Score:** 12/20
- **Weakest Loop:** Network. Cross-team usage does not yet improve the product automatically because shared evidence patterns, owner history, mappings, reviewer decisions, and control-health definitions are not consistently captured as reusable learning assets.
- **Top Encroachment Threat:** Microsoft Security Copilot and Microsoft 365.
- **Competitive Position:** Strong domain context and correction potential, but exposed to platforms that already own the workflow surface. Microsoft can attack through collaboration and security data; IRM Wizard can attack through the system of record.
- **Encroachment Defense:** Build a cross-system assurance workflow with evidence lineage, human review gates, reusable owner and SME maps, source-system authority rules, control-to-evidence patterns, reviewer correction capture, freshness scoring, and leadership-ready control-health definitions.
- **Vendor Portability:** Partial. Provider-neutral schemas, risk-based routing, backup model access, and an automated evaluation harness are required before the product can reliably swap AI providers within 48 hours.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Pricing Model:** Hybrid: seat-based access for adoption plus outcome and usage pricing for reviewed evidence packets, advanced control mapping, and audit-ready outputs.
- **Pricing Today → Tomorrow:** Move from assumed seat-based or enterprise-license access to a **$30/user/month** base fee plus usage pricing for reviewed evidence packets and high-cost audit outputs.
- **Total AI COGS per User:** $2.10/month.
- **Cascading Strategy:** Use lower-cost models for evidence requests, artifact summaries, metadata extraction, reminders, packet formatting, and first-pass summaries. Reserve frontier models for NIST 800-53 mapping, gap analysis, ambiguous control interpretation, exception rationale, and leadership-ready control-health summaries.
- **Routing Mix:** Start at 70% triage / 30% frontier; target 80% / 20% after evaluations prove routine-task quality.
- **Margin Guardrail:** Stress-test inference cost at 3x and redesign architecture or pricing if gross margin falls below 40%.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** High-confidence AC-2 evidence mappings require deterministic checks plus model judgment, with human approval for material audit conclusions.
- **Golden Dataset:** 10 cases, including 3 adversarial cases.
- **Confidence UX:** Combine visible uncertainty, tiered confidence, and human-in-the-loop triggers. AC-2 evidence mapping is never presented as a black-box answer.
- **HITL Architecture:** Human review is a shrinking queue. Uncertain, high-risk, stale, incomplete, or audit-impacting outputs are escalated, and every correction feeds the learning loop.
- **Failure Mode Coverage:** Tests target plausible but incomplete evidence, unsupported owner attestations, stale artifacts, conflicting sources, control-scope errors, and false PASS decisions.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales, and what compounds.**

- **Compounding System:** Recursive learning is active, cross-domain transfer is active but early, and network intelligence is broken until cross-team patterns are captured and reused safely.
- **Governance Posture:** AI agents support IRM Wizard Evidence Readiness workflows beginning with NIST 800-53 AC-2, while final audit conclusions, risk acceptance, policy exceptions, and leadership publishing remain human-owned.
- **Autonomy Boundaries:** Agents may collect, classify, draft, route, and recommend. Humans approve high-impact mappings, exceptions, audit conclusions, regulatory responses, and control-health publication.
- **Escalation Triggers:** Escalate low-confidence, stale, missing, conflicting, sensitive, disputed, high-risk, or non-whitelisted actions.
- **Audit Cadence:** Monitor critical tool calls in real time, review operational quality weekly, governance and access monthly, and regulatory posture quarterly.
- **Shadow AI Audit:** 7 workarounds found · 4 build candidates · $7,500/month in adjacent spend.
- **Agent Boundaries:** Morpheus orchestrates; Evidence Agent collects; Trinity parses; Seraph maps; Oracle reviews; Scribe documents; Learning Agent captures corrections; Escalation Agent drafts follow-ups.
- **Regulatory Exposure:** Limited to high because the workflow supports regulated financial services, cybersecurity governance, access-control evidence, audit readiness, and leadership risk reporting.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How this gets funded, shipped, and adopted.**

- **Horizon 1 (Now):** To be completed in Module 6.
- **Horizon 2 (Next):** To be completed in Module 6.
- **Horizon 3 (Bet):** To be completed in Module 6.
- **Board Narrative:** To be completed in Module 6.
- **Investment Ask:** To be completed in Module 6.
- **Key Strategic Change:** To be completed in Module 6.

→ Details: [`06-the-pitch/`](06-the-pitch/)
