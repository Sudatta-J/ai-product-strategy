# Kill Switch Audit

## Product

IRM Wizard Evidence Readiness Pilot.

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | The pilot should assume a primary LLM provider for drafting evidence requests, summarizing evidence packets, mapping control language, and generating leadership summaries. No single provider should own the product logic, prompts, evidence records, mappings, or review decisions. | M | Route the same core tasks to an approved backup model using a provider-neutral prompt and response schema. Disable non-critical generation tasks if quality drops. |
| **Abstraction** | Product logic should call an internal AI service layer rather than direct provider APIs. Prompts, tool calls, confidence outputs, citations, evidence lineage, and review states should be represented in product-owned formats. | M | Freeze direct provider-specific features, use a common request/response contract, and map provider outputs into the same evidence packet, control mapping, and review result schema. |
| **Routing** | Tasks should be routed by risk and workload: low-risk drafting and summarization can use cheaper/faster models; high-risk mapping, gap analysis, and audit-ready summaries require stronger models and human review. | M | Switch low-risk tasks to backup provider first, keep high-risk tasks behind human review, and manually route unsupported tasks to analyst review until evals pass. |
| **Eval** | The product needs an eval set for NIST 800-53 control mapping, evidence completeness, freshness checks, ownership suggestions, gap flags, and leadership summaries. Without evals, provider swaps are subjective and risky. | H | Run a minimum golden set before provider switch: 20 evidence packets, 10 control mappings, 10 stale evidence examples, 10 missing-owner scenarios, and 5 leadership summaries. |

## Portability Score

Partial.

The product can become 48-hour swappable if it owns the workflow, data model, evidence lineage, prompt templates, reviewer decisions, and eval harness. It is not ready if it relies on provider-specific features, unstructured outputs, or manual judgment to compare model quality.

## 48-Hour Swap Plan

### Hour 0-4: Triage
- Freeze non-essential AI feature changes.
- Identify impacted workflows: evidence request drafting, evidence summarization, control mapping, gap detection, quality review support, and leadership summary generation.
- Confirm backup provider access, security approval, model endpoint, rate limits, and logging requirements.

### Hour 4-12: Route
- Move low-risk generation tasks to backup provider first.
- Keep high-risk control mapping and audit-ready outputs behind human approval.
- Use the same input package: control objective, evidence metadata, source, owner, date, review status, and policy context.

### Hour 12-24: Evaluate
- Run the golden eval set against primary and backup providers.
- Compare accuracy, completeness, traceability, refusal behavior, hallucination rate, and reviewer effort.
- Block any output that cannot preserve evidence lineage or flags unsupported conclusions.

### Hour 24-36: Cutover
- Shift approved workflows to backup provider.
- Turn on additional human review for medium-confidence outputs.
- Monitor latency, cost, error rate, reviewer overrides, and failed mappings.

### Hour 36-48: Stabilize
- Update routing rules based on eval results.
- Document known quality gaps and temporary manual controls.
- Prepare leadership note explaining continuity, risk controls, and expected recovery path.

## This Week / This Month / This Quarter

| Timing | Action |
|--------|--------|
| **This week** | Define provider-neutral schemas for evidence packets, control mappings, review decisions, and leadership summaries. Identify approved primary and backup LLM providers. |
| **This month** | Build the first golden eval set for NIST 800-53 evidence readiness and run it across at least two providers. Add routing rules by task risk. |
| **This quarter** | Automate provider failover for low-risk tasks, require eval approval for high-risk tasks, and publish a provider portability runbook for IT GRC and security leadership. |

## If [primary vendor] doubles pricing tomorrow:

The 48-hour response is to route low-risk summarization, drafting, and formatting work to the backup provider while reserving the primary provider for high-risk control mapping, gap analysis, and leadership-ready outputs. In parallel, reduce token-heavy prompts, cache reusable control and policy context, and measure cost per completed evidence packet rather than cost per model call.

## If [primary vendor] ships a competing product:

The defensible layer is not the model. It is the cross-system assurance workflow: evidence lineage across IRM Wizard, IAM, cloud, vulnerability, privacy, cyber defense, SharePoint, and audit sources; human review gates; reusable owner and SME maps; control-to-evidence pattern libraries; reviewer correction history; freshness scoring; exception rationale; and leadership-ready control-health definitions.

## Kill Switch Readiness

The product is **partially ready** for a 48-hour provider swap. It can reach true readiness when four things are in place:

1. No direct provider calls in product workflow code.
2. Provider-neutral schemas for all AI inputs and outputs.
3. Risk-based routing across primary and backup models.
4. Automated eval harness for evidence readiness, mapping quality, traceability, and defensibility.
