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

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
