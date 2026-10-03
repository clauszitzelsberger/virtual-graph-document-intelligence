# Lessons Learned: Gen1 Battery Program

<p class="meta">Document type: Best Practice (lessons learned) · Document ID: BP-LL · Version 2.0 · Published 2025-10-06 · Owner: Quality Assurance (Elena Müller) · Contributors: High Voltage Battery Engineering, HV Testers</p>

## Purpose

This document records the lessons from the predecessor battery program that the Nova EV program has adopted as rules. Each lesson has an identifier of the form LL-nn. Lessons are cited in design guidelines, in change requests and in decisions, so that the reasoning behind a design choice stays traceable.

## Lessons

### LL-01 Always pre-charge before closing the main contactor

In the Gen1 program, main contactors welded in three prototype vehicles because they were closed against a discharged DC link. The root cause was found after eight weeks. Rule DG-HV-002 now requires a pre-charge circuit, and DG-HV-008 requires contactor position feedback. The Contactor Assembly (CMP-HVB-08) of the Nova EV implements both.

### LL-02 Treat CAN timeouts as functional defects, not as test bench noise

Intermittent CAN timeouts were dismissed as bench problems for months in Gen1. Several were real firmware faults. The Nova EV program records every timeout as a defect against the detecting test case. DEF-0039 (Battery Management System: intermittent CAN timeout) and DEF-0026 (HV Junction Box: incorrect unit conversion, first observed as a CAN timeout) were both real product faults and were resolved with a software fix and a calibration correction.

### LL-03 Regulatory thresholds change; design for it

Gen1 hard-coded the isolation threshold and needed a firmware release when the target market changed. Rule DG-HV-006 makes the threshold a calibration parameter. When R100-6.1.1 changed the threshold to 500 Ω/V in 2026, change request CR-0001 was a calibration and retest exercise.

### LL-04 A missed milestone is cheaper than a moved one

Gen1 moved two milestones and lost the ability to compare plan and progress. The Milestone Gate Policy rule MGP-05 now forbids moving a deadline for a single system. Prototype Build Release (MS-C) of the Nova EV was missed on 2026-07-10 and recorded as such.

### LL-05 Untested requirements are found too late

In Gen1, requirements without a test set were discovered at the last gate. The Requirement Traceability Policy rule RTP-01 now reports them at every readiness review. The current report lists REQ-ILT-0090, REQ-CHS-0107 and REQ-INF-0164.

### LL-06 Critical defects need a calendar, not a discussion

A Critical defect that stayed open for a quarter in Gen1 blocked the design validation gate. The Defect Escalation Policy rule DEP-02 now escalates any Critical defect that is Open for more than 14 days. DEF-1114 (Gate Driver Board: wrong error code reported), Open since 2026-05-23, is the current example of why this rule exists.

### LL-07 Temperature logging resolution

Endurance runs in Gen1 logged temperatures with 1 K resolution and missed a 1.5 K cooling imbalance between modules. DG-BMS-03 now requires 0.5 K. See also BP-BMS-05.

### LL-08 Share the bench plan between battery and thermal teams

The HIL bench and the climate chamber are shared between High Voltage Battery and Thermal Management. Gen1 lost test weeks to bench conflicts. The weekly test planning meeting of the Nova EV program allocates the benches four weeks ahead.

### LL-09 Name the responsible person on every artefact

Requirements, test cases, defects and change requests in Gen1 often had a team but no person as owner. Every artefact in the Nova EV program has exactly one responsible person. The policies RTP-03, DEP-07 and CCP-02 make this binding.

### LL-10 Decisions belong in minutes, with the rule they rest on

Many Gen1 decisions existed only in email threads and could not be found later. Nova EV meeting minutes record each decision with a statement, a rationale, the rule it is based on and the affected requirements, changes or defects.

## Applicability

| Lesson | Adopted as | Components affected |
|---|---|---|
| LL-01 | DG-HV-002, DG-HV-008 | Contactor Assembly, HV Junction Box |
| LL-02 | DEP-01, DEP-05 | All |
| LL-03 | DG-HV-006, DG-BMS-05 | Battery Management System |
| LL-04 | MGP-05 | Program |
| LL-05 | RTP-01 | All |
| LL-06 | DEP-02 | All |
| LL-07 | DG-BMS-03 | Battery Management System |
| LL-08 | Test planning meeting | High Voltage Battery, Thermal Management |
| LL-09 | RTP-03, DEP-07, CCP-02 | All |
| LL-10 | Meeting minutes template | Program |
