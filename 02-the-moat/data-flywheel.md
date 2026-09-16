# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 3/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 4/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 2/5 |

### Correction Loop - 3/5
**What you capture today:** Analyst and reviewer corrections to evidence mappings, completeness checks, stale evidence flags, owner suggestions, exception handling, and control-health summaries.

**How it compounds:** Repeated corrections improve future evidence requests, mapping recommendations, freshness checks, and review prompts for similar controls. This becomes more defensible if corrections are stored as structured learning signals rather than free-text comments.

### Preference Loop - 3/5
**What you capture today:** Reviewer preferences for evidence packet format, leadership summary style, control-health language, escalation thresholds, due-date expectations, and audit-ready output structure.

**How it compounds:** The product can personalize outputs by team, control family, and reviewer, reducing rework over time. The loop is moderate because it requires repeated use across assessments before preferences become reliable.

### Domain Context Loop - 4/5
**What you capture today:** Company-specific control records, NIST 800-53 mappings, policy and control objective relationships, evidence owner history, IAM signals, vulnerability inputs, cloud security findings, audit requests, exceptions, and review rationale.

**How it compounds:** Every reviewed evidence packet strengthens the product's understanding of which evidence is authoritative, which owners are accountable, which mappings are defensible, and which control-health signals leadership can trust.

### Network Loop - 2/5
**What you capture today:** Cross-team participation from governance analysts, evidence owners, IAM, cyber defense, cloud security, vulnerability management, privacy, product security, internal audit, and leadership stakeholders.

**How it compounds:** More teams could make the product better by contributing reusable ownership history, evidence patterns, mapping decisions, and review outcomes. Today this is the weakest loop because value may remain trapped in isolated workflows unless cross-team learning is intentionally designed into the product.

**Total Flywheel Score: 12/20**
**Weakest Loop:** Network
**Fix for weakest loop:** Create shared, reusable learning assets across teams: evidence pattern library, control-to-evidence map, owner and SME history, source-system mapping catalog, reviewer correction log, and control-health signal definitions. This directly addresses the M1 vulnerability that IRM Wizard or Microsoft could win by embedding AI into the platforms where teams already collaborate.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Microsoft Security Copilot and Microsoft 365
**Vector:** Use Microsoft Graph, Teams, SharePoint, Entra, Defender, Purview, and Power Platform to ship evidence collection, owner follow-up, access review signals, control-health summaries, and leadership reporting directly where security and governance teams already collaborate.
**Time-to-threat:** 6 to 12 months
**% of value at risk:** 45%

### 2. Vertical Competitor
**Attacker:** IRM Wizard
**Vector:** Ship a native AI control and evidence readiness assistant inside IRM Wizard that drafts evidence requests, suggests owners, checks completeness and freshness, maps evidence to controls, tracks overdue items, and publishes control-health summaries inside the system of record.
**Time-to-threat:** 6 to 12 months
**% of value at risk:** 60%

### 3. Adjacent Expansion
**Attacker:** AuditBoard or a focused audit automation vendor
**Vector:** Add evidence readiness, NIST 800-53 mapping, audit package generation, and control-health reporting as one more workflow inside audit preparation and control testing products.
**Time-to-threat:** 9 to 18 months
**% of value at risk:** 35%

---

## 90-Day Encroachment Plan

*Most dangerous plan from the encroacher, followed by the defense.*

**Attacker:**
IRM Wizard

**Attack vector (target the weakest loop):**
Target the weak network loop by making IRM Wizard's existing customer activity compound automatically. The attack is to turn control records, evidence tasks, owner assignments, audit requests, risk records, issues, exceptions, and review history into shared AI recommendations inside the system of record.

**Weeks 1-4 - what they ship:**
A native Evidence Readiness Assistant embedded in IRM Wizard. It drafts evidence requests, suggests likely evidence owners, checks missing or stale evidence, maps artifacts to NIST 800-53 control objectives, and summarizes readiness status inside existing control and audit workflows.

**Weeks 5-8 - how they poach users:**
They position it as a no-switching-cost upgrade for teams already using IRM Wizard. Governance analysts, control owners, and audit partners do not need to leave their current workflow; the assistant uses existing tasks, controls, owners, evidence records, issues, and dashboards to produce immediate value.

**Weeks 9-12 - why users don't come back:**
Users stay because the product captures network activity by default. Every completed evidence task, corrected mapping, owner response, overdue item, audit request, and review decision improves future recommendations inside IRM Wizard, making the standalone pilot feel like an extra step.

**Your defense:**
Do not compete as a sidecar chatbot. Build a cross-system assurance workflow that IRM Wizard alone cannot fully own: structured evidence lineage across IRM Wizard, IAM, cloud, vulnerability, privacy, cyber defense, SharePoint, and audit sources; human review gates; reusable owner and SME maps; source-system authority rules; control-to-evidence pattern libraries; reviewer correction capture; freshness scoring; exception rationale; and leadership-ready control-health definitions that improve across teams and source systems.
