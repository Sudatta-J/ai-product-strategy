# Golden Dataset & Reliability Contract

## Golden Dataset Spec

**MVP evaluation task:** Map evidence to NIST 800-53 **AC-2 Account Management**.

**Structured output expected for every test case:**

```text
Control: AC-2
Evidence Type:
Mapping Decision: Full / Partial / None
Mapped Control Objective:
Evidence Freshness: Current / Stale / Unknown
Completeness: Complete / Missing Fields / Insufficient
Traceability: Source + Owner + Date Present? Yes/No
Issue Flag:
Required Follow-up:
Confidence: High / Medium / Low
Human Review: Required / Not Required
```

**Freshness rule:** Evidence older than the current quarter, or missing an evidence date, must be flagged as `Stale` or `Unknown`.

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | AC-2 evidence packet includes Q3 user access review export, source system name, evidence owner, review date, reviewer sign-off, and no unresolved exceptions. | Full mapping. Evidence type: user access review export. Freshness: Current. Completeness: Complete. Traceability: Yes. Issue flag: None. Human review: Not Required. | N | rule + LLM |
| 2 | Privileged access list includes admin accounts and entitlement levels, but no evidence owner or review/approval date. | Partial mapping. Evidence type: privileged access list. Freshness: Unknown. Completeness: Missing Fields. Traceability: No. Issue flag: missing owner/date. Required follow-up: obtain owner attestation and review date. Human review: Required. | Y | rule + LLM |
| 3 | Joiner/mover/leaver ticket shows user role change was requested and approved, but does not show access was provisioned or removed. | Partial mapping. Evidence type: JML ticket. Freshness: Current if ticket date is current quarter. Completeness: Insufficient. Issue flag: request approval is not proof of completed account change. Required follow-up: provisioning/removal evidence. Human review: Required. | N | rule + LLM |
| 4 | Terminated user access removal evidence shows account disabled within required timeframe, includes source, owner, removal date, and ticket link. | Full mapping. Evidence type: terminated user access removal. Freshness: Current. Completeness: Complete. Traceability: Yes. Issue flag: None. Human review: Not Required. | N | rule + LLM |
| 5 | Owner attestation says "access looks appropriate" but does not list accounts, system scope, evidence date, or review population. | Partial mapping. Evidence type: owner attestation. Freshness: Unknown. Completeness: Insufficient. Traceability: No. Issue flag: vague attestation. Required follow-up: account population and dated sign-off. Human review: Required. | Y | rule + LLM |
| 6 | Exception ticket documents one orphaned privileged account, assigns remediation owner, includes due date, and links to the access review that found it. | Partial mapping. Evidence type: exception/remediation ticket. Freshness: Current if ticket date is current quarter. Completeness: Complete for exception tracking, but not full AC-2 evidence alone. Issue flag: open remediation. Required follow-up: verify closure or accepted risk. Human review: Required. | N | rule + LLM |
| 7 | Access recertification campaign results show 98% completion, two overdue reviewers, source system, campaign owner, certification period, and exception list. | Partial mapping. Evidence type: access recertification results. Freshness: Current. Completeness: Missing Fields until overdue reviews are resolved. Issue flag: incomplete certification. Required follow-up: resolve overdue reviewers or document exceptions. Human review: Required. | N | rule + LLM |
| 8 | Account provisioning approval includes manager approval, business justification, requested role, source ticket, requester, approver, and approval date. | Partial mapping. Evidence type: account provisioning approval. Freshness: Current if approval date is current quarter. Completeness: Complete for approval evidence, but not sufficient alone for ongoing account review. Required follow-up: verify provisioning and periodic review evidence. Human review: Required. | N | rule + LLM |
| 9 | Dormant account report identifies accounts inactive for 90+ days, includes generated date, system, owner, and remediation status for each account. | Full or Partial mapping depending on remediation status. Freshness: Current. Completeness: Complete if all dormant accounts have disposition; Partial if remediation is open. Issue flag: open dormant accounts if any unresolved. Human review: Required when unresolved. | N | rule + LLM |
| 10 | Policy excerpt defines account management review frequency and termination removal requirements, but includes no actual evidence that reviews/removals occurred. | None as direct control evidence. Evidence type: policy/standard excerpt. Freshness: Current if policy date is current. Completeness: Insufficient for AC-2 operating effectiveness. Issue flag: policy is design evidence, not operating evidence. Required follow-up: access review/removal artifacts. Human review: Required. | Y | rule + LLM |

**Adversarial rows included:** 3

Rows 2, 5, and 10 are adversarial because they look superficially useful but should not be accepted as full AC-2 evidence.

**Coverage gaps identified by partner:** The first dataset focuses on AC-2 mapping quality. It does not yet cover all AC-2 sub-objectives, non-human/service accounts, privileged emergency access, system-generated evidence tampering, or cross-system conflicts between IAM exports and IRM Wizard records.

**V1 ship target:** Expand from 10 rows to approximately 150 rows across AC-2 variants, account types, source systems, exception states, evidence freshness conditions, and adversarial examples.

## Confidence UX Design

**Approach:** Combine visible uncertainty, tiered confidence, and human-in-loop triggers. The UX should never present AC-2 evidence mapping as a black-box answer. It should show why the AI believes the evidence maps, what is missing, and when a human must decide.

**High confidence (>90%):** Evidence has source, owner, date, account population, review/approval status, and clear traceability to AC-2. The UI can say: `Ready for analyst confirmation`. Show the mapped control objective, evidence lineage, and why the packet is complete. Human review is optional unless the output will be used for audit delivery or leadership reporting.

**Medium confidence (70-90%):** Evidence appears relevant but has one missing or ambiguous element, such as incomplete remediation, missing reviewer, unclear population, or partial traceability. The UI should visibly soften the answer: `Likely partial mapping - review recommended`. Show the missing fields, source of uncertainty, and recommended follow-up. Human review is required before publication.

**Low confidence (<70%):** Evidence is stale, missing a date, missing ownership, lacks source traceability, conflicts with another source, or is policy-only/design evidence. The UI should block auto-mapping and say: `Not enough evidence to map safely`. The output must enter a human review queue.

**Not confident (<50%):** Evidence is contradictory, unverifiable, unrelated to AC-2, or likely misleading. The UI should block the mapping, prevent leadership-ready language, and require a GRC analyst to either reject the evidence or request new evidence from the owner.

**User control surface:**

- Adjust confidence threshold by workflow: pilot default is 90% for audit-ready use and 70% for analyst workbench triage.
- See AI reasoning: source evidence, mapped objective, missing fields, freshness logic, and why the decision is `Full`, `Partial`, or `None`.
- Correct and override: mapping decision, freshness, completeness, traceability, issue flag, required follow-up, confidence, and human-review status.
- Send correction to learning loop: each edit captures reviewer, date, rationale, corrected output, and whether the correction should become a reusable mapping pattern.
- Escalate from the same screen: request evidence from owner, assign remediation, send to Oracle-style quality review, or mark as not usable for audit.

**Confidence copy examples:**

| Confidence Tier | UI Copy | Allowed Action |
|-----------------|---------|----------------|
| High | `Evidence appears complete and traceable for AC-2. Review lineage before publishing.` | Analyst can confirm; publication still requires approval. |
| Medium | `Evidence likely supports AC-2, but one or more fields need review.` | Analyst review required. |
| Low | `Evidence is incomplete, stale, or missing traceability. Do not use as audit-ready evidence.` | Human review queue. |
| Not confident | `Mapping blocked. Evidence is contradictory, unrelated, or unverifiable.` | Reject or request new evidence. |

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Mapping accuracy | >= 90% on golden dataset before pilot use | Percent of rows where mapping decision and required follow-up match expected output | < 85% |
| False full-mapping rate | <= 3% | Percent of partial/none cases incorrectly marked `Full` | > 5% |
| Evidence freshness detection | >= 95% | Percent of stale/unknown evidence cases correctly flagged | < 90% |
| Traceability detection | >= 95% | Percent of cases where missing source/owner/date is correctly identified | < 90% |
| Hallucination rate | 0 critical hallucinations | Any invented source, owner, date, approval, or remediation status | Any critical hallucination |
| Latency (p95) | <= 10 seconds for a single evidence packet | p95 response time in pilot workflow | > 15 seconds |
| Drift velocity | No more than 5-point accuracy drop month over month | Monthly eval rerun on fixed golden set | > 5-point drop |

## HITL Architecture

**Design principle:** Human-in-the-loop should be a shrinking queue, not permanent babysitting. The system should route only uncertain, high-risk, stale, incomplete, or leadership/audit-impacting outputs to humans, and every correction should improve future routing.

Human review is required when:

- Mapping decision is `Partial` or `None`
- Confidence is below 90%
- Evidence freshness is `Stale` or `Unknown`
- Source, owner, or date is missing
- Evidence is policy-only/design evidence
- Remediation or exception status is open
- Evidence conflicts with another source system
- The AI proposes a leadership-ready control-health signal

**Review queue thresholds:**

| Queue | Trigger | Owner | Target Action |
|-------|---------|-------|---------------|
| Analyst Review | Medium confidence, partial mapping, missing field, or open exception | GRC analyst | Confirm, correct, or request follow-up evidence |
| Evidence Owner Follow-Up | Missing owner, missing source, missing date, stale evidence, or incomplete population | Control/evidence owner | Provide corrected evidence or explain exception |
| Quality Gate | Audit-ready package, leadership signal, ambiguous mapping, or high-impact exception | Oracle-style reviewer / GRC lead | Approve, reject, or send back for revision |
| Escalation | Conflicting sources, likely hallucination, unsupported conclusion, or regulatory ambiguity | GRC lead + relevant SME | Decide defensible treatment and document rationale |

**Escalation path:** AI drafts mapping -> GRC analyst reviews -> control/evidence owner resolves missing evidence -> Oracle-style quality review validates defensibility -> GRC lead approves for audit or leadership use.

**Correction capture:** Every human edit is stored as a structured correction: original AI output, corrected output, reason code, reviewer, date, control objective, evidence type, source system, and reuse permission. These corrections feed the data flywheel by improving future AC-2 mappings, freshness checks, and owner follow-up recommendations.

**Success measure:** Over time, the percentage of AC-2 evidence packets requiring manual review should fall while false full-mapping rate remains below the reliability threshold.

## Red-Team Findings

Likely failure mode: the AI may over-credit plausible but incomplete evidence, especially owner attestations or policy excerpts that sound authoritative but do not prove operating effectiveness. The dataset intentionally includes adversarial rows that force the model to reject or partially map these cases rather than treating them as complete AC-2 evidence.
