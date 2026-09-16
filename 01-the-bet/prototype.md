# IRM Wizard Evidence Readiness Pilot

## What I Built
An interactive pilot simulation that shows how IRM Wizard can guide an evidence request from intake through collection, control mapping, quality review, and leadership-ready control-health publishing.

## Tool Used
Custom HTML, CSS, and JavaScript prototype.

## Prototype Link
[Open the clickable prototype](../index.html)

## Target User
IRM Wizard users responsible for evidence readiness, control monitoring, audit preparation, and cyber risk reporting, including governance analysts, control owners, evidence owners, and CISO leadership stakeholders.

## Problem
Evidence collection and audit preparation are too manual. Teams spend time identifying evidence owners, requesting artifacts, waiting for responses, checking completeness and freshness, mapping evidence to control objectives, formatting audit-ready packages, and explaining risk/control health to leadership.

## Prototype Workflow
1. Create evidence request
2. Collect source evidence
3. Map evidence to control objective
4. Apply quality review gate
5. Publish control-health signal

## Agent Roles Demonstrated
- Morpheus: Orchestrates the evidence request and routes work to the right owner.
- Evidence Agent: Pulls source evidence and assembles a packet.
- Seraph: Maps evidence to NIST 800-53 control expectations and flags gaps.
- Oracle: Reviews completeness, freshness, traceability, and defensibility.
- Scribe: Packages the reviewed output into an audit-ready record and leadership signal.

## AI Value Archetype
Orchestrator and copilot. The prototype shows AI coordinating cross-functional work, drafting structured outputs, checking evidence readiness, and surfacing decision-ready signals while keeping human review gates in place.

## The Bet in One Sentence
IRM Wizard can reduce manual evidence collection and improve audit readiness by turning fragmented evidence tasks into a guided, reviewable, and leadership-ready control-health workflow.

## MVP Outcome
For selected NIST 800-53 controls, users can create a guided evidence request, identify required artifacts and owners, track evidence readiness, validate mapping and quality, and publish a reviewed control-health signal.

## Success Measures
- Reduction in manual evidence collection effort
- Faster audit preparation cycle time
- Higher evidence completeness and freshness
- Clearer ownership of missing or overdue evidence
- More current leadership view of control health

## Guardrails
- Human approval remains required before audit or leadership use.
- Every evidence item should retain source traceability.
- The system should flag uncertainty rather than invent compliance conclusions.
- Quality review should validate completeness, freshness, mapping, and defensibility before publication.

## Kill Criteria
Stop or pivot if users cannot connect enough trusted evidence sources, if control owners do not trust the generated mappings, if review effort is not materially reduced, or if leadership does not find the control-health signal actionable.
