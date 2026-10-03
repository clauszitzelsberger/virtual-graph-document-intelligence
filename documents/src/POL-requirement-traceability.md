# Requirement Traceability Policy

<p class="meta">Document type: Policy · Document ID: POL-RTP · Version 1.2 · Published 2025-01-15 · Owner: Quality Assurance (Greta Ivanova) · Applies to: Nova EV program</p>

## Purpose

This policy defines the traceability that every requirement of the Nova EV program must have: to the component it belongs to, to the test sets that verify it, to the rules of standards and guidelines it satisfies, and to the person who owns it. Requirements are recorded in the requirements management tool with an identifier of the form REQ-SYS-nnnn, where SYS is the three-letter system code (HVB, EDU, CHS, BDY, INF, ADS, THM, ILT).

## Rules

### RTP-01 Every requirement has at least one test set

A requirement without a test set cannot be verified and cannot contribute to a milestone gate. Requirements without test sets are reported by Quality Assurance at every readiness review. As of 2026-09-15 three requirements have no test set: REQ-ILT-0090 (Touch Switch: Switch off after a timeout), REQ-CHS-0107 (Air Suspension Module: Adjust ride height) and REQ-INF-0164 (Instrument Cluster: Show speed and remaining range).

### RTP-02 Every requirement belongs to exactly one component

The component assignment defines the system, the engineering team and the test team. A requirement that applies to several components is split into one requirement per component.

### RTP-03 Every requirement has exactly one owner

The owner is an engineer of the system that owns the component. The owner is the contact for change requests, defects and reviews concerning the requirement.

### RTP-04 Test sets may verify several requirements

A test set may verify more than one requirement of the same component when the test procedure is identical. The test set then appears under each requirement it verifies.

### RTP-05 Requirements derived from standards cite the rule

A requirement that implements a rule of a standard, a policy or a design guideline shall reference the rule identifier, for example R100-6.1.1 or DG-BMS-03. The reference is recorded as a "satisfies" link from the requirement to the rule.

### RTP-06 Minimum test depth

A requirement of a safety-classified component shall be verified by at least two test cases. Requirements with a single test case are reported at the readiness review. As of 2026-09-15 five requirements are covered by only one test case, among them REQ-HVB-0059 (Battery Management System: Log cell temperatures) and REQ-EDU-0069 (Electric Motor: Derate on overtemperature).

### RTP-07 Requirement identifiers are stable

A requirement identifier is never reused. A requirement that is withdrawn keeps its identifier and is marked as withdrawn in the requirements tool.

## Reporting

Quality Assurance runs the traceability report before every readiness review. The report lists requirements without test sets (RTP-01), requirements with a single test case (RTP-06) and requirements without a rule reference where a rule applies (RTP-05). Contacts: Greta Ivanova, Anna Kim, Elena Müller.
