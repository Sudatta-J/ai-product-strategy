# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Analyst corrections, Oracle-style review decisions, confidence overrides, missing-field flags, stale-evidence flags, and AC-2 mapping fixes | Better future evidence mapping, stronger freshness checks, more accurate owner follow-up, and fewer false full-mappings | Y | active |
| Cross-Domain Transfer | Reviewed evidence packets, control-to-evidence patterns, source-system authority rules, exception rationale, and reusable NIST 800-53 mapping decisions | Lessons from AC-2 improve adjacent controls such as IA-2, AU-6, CM-6, and RA-5 | Y | active but early |
| Network Intelligence | Cross-team owner history, SME maps, source-system patterns, repeated evidence workarounds, audit requests, and remediation outcomes | Shared intelligence about who owns evidence, which sources are authoritative, which patterns repeat, and where evidence gaps emerge | Y | broken |

**Broken loop identified by partner:** Network Intelligence.

The product can scale evidence requests, but it does not yet automatically convert cross-team activity into reusable intelligence. Without explicit capture, ownership history, evidence patterns, reviewer corrections, and source-system trust rules remain trapped in individual audits, teams, tickets, and conversations.

**Fix plan:** Build a governed shared learning layer:

- Create reusable owner and SME maps by control, system, evidence type, and team.
- Capture every reviewer correction as structured data: original output, corrected output, reason code, reviewer, date, control objective, evidence type, source system, and reuse permission.
- Build a control-to-evidence pattern library starting with AC-2, then expand to IA-2, AU-6, CM-6, and RA-5.
- Maintain source-system authority rules that define which systems are trusted for IAM, cloud, vulnerability, privacy, cyber defense, audit, and IRM Wizard records.
- Publish control-health definitions that can be reused across teams but remain privacy- and access-controlled.
- Add monthly checks for whether manual review rate and false full-mapping rate are decreasing as more reviewed packets flow through the system.

## Context Connectivity

Knowledge should flow from evidence requests, source-system artifacts, human corrections, quality-review decisions, and leadership control-health reporting back into reusable product memory.

**Where knowledge flows today:**

- IRM Wizard holds control records, evidence tasks, issues, audit workflows, and workflow status.
- IAM tools hold access review exports, privileged access lists, provisioning/removal activity, and recertification campaign results.
- SharePoint and collaboration tools hold evidence documents, attestations, screenshots, and working files.
- Vulnerability, cloud security, cyber defense, privacy, and product security tools hold source evidence for adjacent control families.
- GRC analysts and control owners hold tacit knowledge about which evidence is authoritative, which owners respond, and what auditors accept.

**Where knowledge silos:**

- Evidence ownership often lives in team memory or prior audit threads instead of a reusable owner map.
- Corrections can be trapped in comments, review notes, email, or one-off analyst edits.
- Source-system authority is not always explicit, so the AI may treat policy excerpts, screenshots, and system exports as equally reliable.
- Control mappings can remain local to a single assessment instead of becoming reusable patterns.
- Leadership control-health definitions can differ across teams, making trends hard to compare.

**Context connectivity target:** Create a cross-system assurance layer that connects IRM Wizard, IAM, SharePoint, vulnerability management, cloud security, privacy, cyber defense, product security, internal audit, and reviewer correction history into one governed evidence-readiness memory.

**Freeze test:** If the system froze for 3 months, it would not reliably keep winning against IRM Wizard or Microsoft. The current product would still help coordinate work, but it would not compound fast enough unless corrections, owner maps, source-system rules, and cross-control evidence patterns keep improving. That means the compounding system is promising but not yet defensible.

## Governance Policy

**Scope:** This policy covers AI agents that support IRM Wizard Evidence Readiness workflows for IT GRC, beginning with NIST 800-53 AC-2 Account Management. It covers evidence request orchestration, source evidence collection, evidence-to-control mapping, freshness/completeness checks, exception flagging, quality review support, documentation, and leadership-ready control-health summaries.

This policy does **not** allow agents to make final audit conclusions, approve risk acceptance, certify compliance, submit regulatory responses, approve policy exceptions, or publish final control-health status without authorized human approval.

**Autonomy boundaries:**

| OK Solo | Needs Human | Never Fully Automated |
|---------|-------------|-----------------------|
| Draft routine evidence requests using approved templates | Send escalations outside routine owner follow-up | Final audit conclusion |
| Identify likely evidence owner from approved owner map | Approve evidence mapping for audit use | Formal compliance certification |
| Pull metadata from approved source systems | Publish leadership control-health signal | Regulatory response or regulatory interpretation |
| Flag missing fields, stale evidence, and traceability gaps | Accept compensating control or exception rationale | Final risk acceptance |
| Suggest `Full`, `Partial`, or `None` mapping with rationale | Override disputed evidence owner or reviewer correction | Policy exception approval |
| Prepare draft summary with visible caveats | Reuse team-specific corrections across teams | Disciplinary, HR, or employment action |

**Escalation triggers:** Humans must enter when:

- Confidence is below 90% for audit-ready or leadership-facing outputs.
- Evidence is stale, missing owner/source/date, incomplete, conflicting, or policy-only.
- The AI proposes `Full` mapping for a critical or high-risk control.
- Any output would affect audit posture, regulatory coverage, risk acceptance, or leadership reporting.
- Evidence includes privacy data, privileged access data, restricted system access, or sensitive security findings.
- A control owner disputes a request, evidence interpretation, or mapping decision.
- An exception or remediation item is open.
- A false PASS risk is detected.
- An agent attempts a non-whitelisted tool call or requests access outside its approved scope.

**Audit cadence:**

| Review Type | Owner | Cadence | What Gets Checked |
|-------------|-------|---------|-------------------|
| Operational monitoring | IT GRC Product Owner | Weekly | Low-confidence outputs, stale evidence, unresolved escalations, failed tool calls, overdue owner responses |
| Golden dataset evaluation | IT GRC Product Owner + AI Governance | Weekly during pilot; monthly after stabilization | Mapping accuracy, false full-mapping rate, freshness detection, traceability detection, hallucination rate |
| Human review sample | GRC Lead / Oracle-style reviewer | Monthly | Random sample of approved packets plus all escalations and overrides |
| Access and memory review | Security Architecture + Privacy | Monthly | Who accessed evidence, what persisted, retention, TTL, reuse permissions, restricted data handling |
| Governance review | CISO delegate + AI Governance + IT GRC Lead | Quarterly | Policy adherence, risk trends, model/prompt/routing changes, audit findings, incident history |
| Incident review | Product Owner + CISO delegate | As needed | Any false PASS, data leak, unauthorized tool call, hallucinated evidence, or customer-impacting workflow failure |

**Regulatory exposure (EU AI Act / other):** Risk tier is **limited to high** because the workflow supports regulated financial services, cybersecurity governance, access control evidence, audit readiness, and leadership risk reporting. Applicable regimes and control expectations include NIST 800-53, internal IT/security policies, privacy obligations such as GDPR/CCPA where personal data appears in evidence, financial services audit expectations, and emerging AI governance requirements. The system must preserve audit logs, human approvals, confidence signals, data lineage, source traceability, and model/prompt change history.

**Governance posture:** Governance is a product trust asset. The system should expose its confidence, source lineage, human approvals, and review trail so CISO leadership and internal audit can see why an output is defensible.

## Agent Topology

| Agent | Can Do | Cannot Do | Human Approval Required |
|-------|--------|-----------|-------------------------|
| **Morpheus - Lead GRC Orchestrator** | Intake requests, decompose work, identify likely control/evidence owners, route tasks, detect scope ambiguity, and prepare decisions for human review. | Approve final work products, make final compliance judgments, or silently resolve contested regulatory interpretation. | Required for ambiguous scope, contested ownership, non-standard requests, and delivery to GRC leadership. |
| **Evidence Agent - Source Collection** | Pull or organize approved evidence metadata and artifacts from IRM Wizard, IAM, SharePoint, cloud, vulnerability, privacy, and cyber defense sources within granted permissions. | Access unapproved systems, expand permissions, alter source evidence, or collect sensitive data without approved purpose. | Required when evidence contains restricted data, unexpected sensitive content, or source-system conflicts. |
| **Trinity - Compliance Parser** | Extract structured citations or obligation language from policies, standards, regulatory text, and audit requests. | Perform NIST mapping, gap analysis, or final regulatory interpretation. | Required when regulatory text is ambiguous, contested, or could affect formal compliance posture. |
| **Seraph - Governance Mapper** | Map evidence, citations, standards, and control objectives to NIST 800-53; identify `Full`, `Partial`, or `None` mapping; flag coverage gaps. | Approve its own mappings, publish control-health status, or ignore missing traceability. | Required for all audit-ready mappings, low-confidence outputs, partial/none mappings, and high-risk controls. |
| **Oracle - Quality Gate** | Review completeness, freshness, traceability, mapping soundness, exception rationale, and defensibility before delivery. | Produce primary work products or approve work with substantive accuracy, completeness, traceability, or defensibility gaps. | Required before leadership-ready outputs, audit packages, control-health publication, and any PASS/FAIL style conclusion. |
| **Scribe - Documentation Specialist** | Maintain decision history, evidence packet summaries, assumptions, review outcomes, corrections, and audit-ready records. | Hide caveats, rewrite uncertainty as certainty, or delete review history. | Required before final records are marked audit-ready or reused in future assessments. |
| **Learning Agent - Feedback Capture** | Capture approved reviewer corrections, reason codes, owner mappings, source-system authority rules, and reusable control-to-evidence patterns. | Reuse sensitive evidence, personal data, or team-specific findings across teams without permission and privacy checks. | Required before corrections become reusable network intelligence or update golden dataset/pattern libraries. |
| **Escalation Agent - Follow-Up Drafting** | Draft remediation requests, owner follow-ups, overdue reminders, and escalation summaries using approved templates. | Send leadership escalations, regulatory language, or risk acceptance recommendations without approval. | Required before any escalation outside routine owner follow-up or any message that affects audit/risk posture. |

**Agent chain ownership:** Morpheus owns orchestration until the work is routed. Each specialist owns its draft output. Oracle owns the quality gate. The GRC Lead owns final approval. If one agent hands off incomplete or ambiguous work, Morpheus must route it back or escalate rather than allowing the chain to continue silently.

**Tool-call controls:** Agents may call only approved tools and data sources. Every tool call must be logged with agent, user, purpose, source system, timestamp, data class, and outcome. Non-whitelisted tool calls are blocked and escalated.

**Memory controls:** Persistent memory is limited to approved reusable patterns: owner/SME maps, source-system authority rules, review corrections, control-to-evidence mappings, and non-sensitive workflow metrics. Raw evidence, personal data, restricted security findings, and team-specific exceptions require retention rules, access controls, TTL, and reuse approval.

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| Analysts export IRM Wizard tasks to spreadsheets, then use ChatGPT to summarize overdue evidence | Support tickets and analyst interviews - workflow gap | H | build |
| Control owners paste IAM access-review exports into public AI tools to explain exceptions | Security review and user interviews - trust gap | H | build |
| Teams use Outlook or Teams Copilot to draft evidence requests outside IRM Wizard | Message samples and user interviews - workflow gap | H | partner |
| GRC analysts assemble audit packets in SharePoint folders and use AI to write the narrative | Audit retrospectives and file-pattern review - capability gap | H | build |
| Security teams use vendor AI features to summarize vulnerability and cloud-control exports | API and export patterns - capability gap | M | partner |
| Managers paste control-health data into ChatGPT to rewrite leadership updates | Leadership interviews and document history - trust gap | M | build |
| Power Automate, Zapier, or Make recipes move reminders between IRM Wizard, Jira, email, and Teams | Automation-directory audit - workflow gap | M | partner |

**Total tools found:** 7 workarounds
**Tools after triage:** 4 build candidates
**Estimated hidden spend:** $7,500/month in duplicate licenses, analyst effort, and unmanaged automation
