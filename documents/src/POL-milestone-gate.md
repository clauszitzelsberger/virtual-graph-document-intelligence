# Milestone Gate Policy

<p class="meta">Document type: Policy · Document ID: POL-MGP · Version 1.3 · Published 2025-01-15 · Owner: Program Management (Hannes Singh) · Applies to: Nova EV program</p>

## Purpose

This policy defines the milestones of the Nova EV program and the conditions under which a milestone counts as reached. Milestones are recorded in the project tracking tool with an identifier of the form MS-x, a name, a deadline and a status (Planned, Reached, Missed).

## Milestones of the Nova EV program

| Milestone | Name | Deadline |
|---|---|---|
| MS-A | Concept Freeze | 2025-11-14 |
| MS-B | Design Freeze | 2026-03-20 |
| MS-C | Prototype Build Release | 2026-07-10 |
| MS-D | Design Validation Complete | 2026-10-16 |
| MS-E | Pre-Series Release | 2027-02-12 |
| MS-F | Production Validation Complete | 2027-06-18 |

Start of production of the Nova EV is planned for 2027-09-01. All milestone deadlines lie before that date.

## Rules

### MGP-01 Every test set is required for exactly one milestone

When a test set is created, it is assigned to the milestone at which its result is needed. The assignment does not change afterwards. A test set that is not required for any milestone is not a valid test set.

### MGP-02 Every milestone requires at least one test set

A milestone without required test sets has no gate criterion and is not accepted in the plan.

### MGP-03 A milestone is reached only when all required test sets are passed

The gate review confirms that every required test set has status Passed. One Failed or In Progress test set is sufficient to keep the milestone open. There is no partial reaching of a milestone and no reaching with open critical defects (see the Defect Escalation Policy, rule DEP-03).

### MGP-04 A milestone whose deadline has passed without being reached is missed

The status Missed is set on the day after the deadline if the gate criterion is not met. A missed milestone stays missed; its remaining test sets are still executed and their results are reported at the next milestone review. Prototype Build Release (MS-C) was missed on 2026-07-11 with 44 required test sets not passed.

### MGP-05 Milestone deadlines are not moved for a single system

A deadline is moved only when at least two systems cannot meet it and Program Management approves the move. A single system that cannot meet the deadline leads to a missed milestone, not to a moved one.

### MGP-06 Readiness review four weeks before the deadline

Program Management holds a readiness review four weeks before each milestone deadline. The review lists all required test sets that are not Passed, the open defects behind them and the responsible people. Decisions taken in the review are recorded in meeting minutes. The readiness review for Design Validation Complete (MS-D) took place on 2026-09-15.

### MGP-07 Test execution before the deadline

For a milestone to be reached, every test case of its required test sets must have been executed on or before the milestone deadline. Results that arrive after the deadline do not count for the gate.

## Status summary (as of 2026-09-15)

Concept Freeze (MS-A) and Design Freeze (MS-B) are reached. Prototype Build Release (MS-C) is missed. Design Validation Complete (MS-D) is at risk: several required test sets are Failed because of open critical defects, among them DEF-1114 on the Gate Driver Board and DEF-0325 on the Thermal Control Unit. Pre-Series Release (MS-E) and Production Validation Complete (MS-F) are planned.

Program managers: Hannes Singh, Gabriel Becker, Jakob Schulz, Emre Hassan, Rafael Sato.
