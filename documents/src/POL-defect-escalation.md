# Defect Escalation Policy

<p class="meta">Document type: Policy · Document ID: POL-DEP · Version 2.1 · Published 2025-03-01 · Owner: Quality Assurance (Anna Kim) · Applies to: Nova EV program</p>

## Purpose

This policy defines how defects found during testing are classified, owned, escalated and closed. Defects are recorded in the defect tracking tool with an identifier of the form DEF-nnnn, a title, a description, a severity (Critical, Major, Minor), a status (Open, In Progress, Resolved), a creation date and, once resolved, a resolution date and a resolution text.

## Rules

### DEP-01 Every defect is detected by exactly one test case

A defect record always names the test case that detected it. The test case links the defect to its test set, to the requirement under test and to the milestone the test set is required for. This chain is the basis for every escalation decision.

### DEP-02 Critical defects escalate after 14 days

A defect with severity Critical that is still Open 14 days after its creation is escalated to the responsible system engineering lead and to Program Management. The escalation is documented in an email thread or in meeting minutes. Example: DEF-1114 (Gate Driver Board: wrong error code reported), created 2026-05-23 and still Open, was escalated on 2026-09-02.

### DEP-03 Critical open defects block the milestone gate

A test case with an Open or In Progress defect is Failed. A test set with a Failed test case is Failed. A milestone whose required test sets are not all Passed is not reached. Consequently, a single Open critical defect on a required test set blocks the milestone. There is no waiver for critical defects.

### DEP-04 Major and minor defects may be carried over

Major and Minor defects on a required test set also cause the test case to fail. Unlike critical defects, they may be carried over to the next milestone by decision of the milestone review, provided a resolution plan and a date are documented.

### DEP-05 Resolution requires a resolution text

A defect is set to Resolved only when a resolution date and a resolution text are recorded. The resolution text names the fix, for example a software release, a calibration change or a corrected test specification. A defect found to be a test bench issue is resolved with the text "Root cause in test bench, bench repaired".

### DEP-06 Retest after resolution

After a defect is resolved, the detecting test case is re-executed. The test case moves to Passed only when the re-execution passes and no other Open or In Progress defect remains on it.

### DEP-07 Defect ownership

Every defect has exactly one responsible person, an engineer of the system that owns the component under test. The test engineer who executed the detecting test case is informed of every status change.

### DEP-08 Duplicate defects

When two defects describe the same root cause, the later one is resolved with a reference to the earlier one. Both keep their link to their detecting test case.

## Current escalations (as of 2026-09-15)

| Defect | Component | Created | Owner | Blocked milestone |
|---|---|---|---|---|
| DEF-1114 | Gate Driver Board | 2026-05-23 | David Horvath | MS-D Design Validation Complete |
| DEF-0325 | Thermal Control Unit | 2026-08-10 | Umut Okafor | MS-D Design Validation Complete |
| DEF-0783 | Perception Module | 2026-08-21 | Nils Lefevre | MS-D Design Validation Complete |
| DEF-0078 | Head Unit | 2026-08-23 | Zoe Wilson | MS-D Design Validation Complete |

All four defects are Critical and Open. Under DEP-03 each of them alone blocks Design Validation Complete (MS-D, deadline 2026-10-16).
