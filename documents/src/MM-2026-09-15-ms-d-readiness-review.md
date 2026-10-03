# Design Validation Readiness Review MS-D 2026-09-15

<p class="meta">Document type: Meeting Minutes · Meeting: Readiness Review for Design Validation Complete (MS-D) · Date: 2026-09-15, 14:00 to 16:30 · Location: Building 4, room 1.02 and video · Minutes taken by: Jakob Schulz</p>

## Attendees

Hannes Singh (Program Management, chair), Gabriel Becker, Jakob Schulz, Emre Hassan (Program Management), Kenji Wagner, Felix Singh (Functional Safety), Anna Kim, Greta Ivanova (Quality Assurance), David Horvath and Katrin Larsen (Electric Drive Unit Engineering), Umut Okafor and Jonas Kovacs (Thermal Management Engineering), Nils Lefevre (Driver Assistance Engineering), Zoe Wilson and Anna Fischer (Infotainment Engineering), Fatima Kim and David Kovacs (HV Testers), Tanja Ramirez and Paul Tanaka (Vehicle Integration Test), Zain Kim (Change Management).

## Purpose

Readiness review four weeks before the deadline of Design Validation Complete (MS-D, 2026-10-16), as required by MGP-06. The review lists the required test sets that are not Passed, the defects behind them and the decisions needed.

## 1. Gate status

Greta Ivanova presented the traceability report. Of the test sets required for MS-D, roughly a quarter are Passed, the majority is In Progress and 36 are Failed. Under MGP-03 the milestone is reached only when all required test sets are Passed. Under DEP-03 every Open critical defect on a required test set blocks the gate on its own.

Four Open critical defects sit on required test sets:

| Defect | Component | Test case | Test set | Requirements | Owner |
|---|---|---|---|---|---|
| DEF-1114 Gate Driver Board: wrong error code reported | Gate Driver Board (CMP-EDU-06) | TC-03679 Fault injection | TS-EDU-0152 | REQ-EDU-0117, REQ-EDU-0005 | David Horvath |
| DEF-0325 Thermal Control Unit: response too slow | Thermal Control Unit (CMP-THM-04) | TC-01129 EMC immunity | TS-THM-0041 | REQ-THM-0033 | Umut Okafor |
| DEF-0783 Perception Module: response too slow | Perception Module (CMP-ADS-06) | TC-02571 High temperature at +60 °C | TS-ADS-0134 | REQ-ADS-0098, REQ-ADS-0044 | Nils Lefevre |
| DEF-0078 Head Unit: sporadic false trigger | Head Unit (CMP-INF-01) | TC-00291 Vibration profile | TS-INF-0013 | REQ-INF-0011, REQ-INF-0120 | Zoe Wilson |

## 2. DEF-1114 Gate Driver Board

David Horvath reported. The defect has been Open since 2026-05-23 and was escalated on 2026-09-02 under DEP-02. Root cause: the supplier firmware of the isolation driver maps the desaturation fault to the gate undervoltage error code. Replacement samples with corrected supplier firmware arrive on 2026-09-24. Retest of TS-EDU-0152 on the HIL bench is possible from 2026-09-28.

**Decision D-2026-09-15-01: A task force led by David Horvath retests TS-EDU-0152 by 2026-10-02 with the corrected supplier firmware.** Rationale: DEF-1114 alone blocks MS-D and the fix depends on supplier samples that are now scheduled. Based on DEP-03 and BP-GDB-05. Status: Approved. Affects DEF-1114, REQ-EDU-0117, REQ-EDU-0005 and the Gate Driver Board. Fatima Kim executes the retest.

## 3. DEF-0325 Thermal Control Unit

Umut Okafor reported. The Thermal Control Unit responds too slowly to compressor speed limit requests during the EMC immunity test. The root cause is a filter constant in the CAN receive path. A software fix is in test on the bench since 2026-09-11.

**Decision D-2026-09-15-02: The software fix for DEF-0325 is released on 2026-09-22 and TS-THM-0041 is retested in the week of 2026-09-28.** Rationale: fix available, bench booked. Based on DEP-06. Status: Approved. Affects DEF-0325 and REQ-THM-0033. Owner: Umut Okafor with Tanja Ramirez.

## 4. DEF-0783 Perception Module and DEF-0078 Head Unit

Nils Lefevre reported that the Perception Module response time at +60 °C exceeds the limit by 12 percent and that a fix requires a thermal redesign of the housing, which cannot be done before MS-D. Zoe Wilson reported that DEF-0078 is not yet understood; the false trigger appears only in the vibration profile test and only with the Bluetooth stack active.

**Decision D-2026-09-15-03: MS-D is not moved. The deadline stays at 2026-10-16. If DEF-0783 or DEF-0078 remain Open at the deadline, the milestone is recorded as Missed.** Rationale: a milestone is not moved for a single system, and moved milestones destroy plan comparability. Based on MGP-05 and LL-04. Status: Approved. Affects DEF-0783, DEF-0078 and the Design Validation Complete milestone. Hannes Singh informs the steering committee.

**Decision D-2026-09-15-04: DEF-0783 gets a design change request for the Perception Module housing, to be raised by Nils Lefevre by 2026-09-22.** Rationale: the fix is a design change and falls under the Change Control Policy. Based on CCP-01. Status: Approved. Affects DEF-0783 and the Perception Module (CMP-ADS-06).

## 5. CR-0001 retest and untested requirements

Zain Kim confirmed that the retest of the nine requirements affected by CR-0001 is on track; seven of the test sets are Passed, two are In Progress. Anna Kim reported the three requirements without any test set, REQ-ILT-0090, REQ-CHS-0107 and REQ-INF-0164, none of which is required for MS-D.

**Decision D-2026-09-15-05: Test sets for REQ-ILT-0090, REQ-CHS-0107 and REQ-INF-0164 are created before Pre-Series Release (MS-E).** Rationale: RTP-01 requires a test set for every requirement. Based on RTP-01. Status: Approved. Affects REQ-ILT-0090, REQ-CHS-0107 and REQ-INF-0164. Owners: Hannes Patel, Carlos Almeida, Isabel Almeida.

## Actions

| Action | Owner | Due |
|---|---|---|
| Retest TS-EDU-0152 with corrected supplier firmware | David Horvath, Fatima Kim | 2026-10-02 |
| Release software fix for DEF-0325 | Umut Okafor | 2026-09-22 |
| Raise change request for Perception Module housing | Nils Lefevre | 2026-09-22 |
| Inform steering committee about MS-D risk | Hannes Singh | 2026-09-18 |
| Create test sets for the three untested requirements | Hannes Patel, Carlos Almeida, Isabel Almeida | 2027-01-15 |
