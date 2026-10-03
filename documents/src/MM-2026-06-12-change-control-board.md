# Change Control Board Meeting Minutes 2026-06-12

<p class="meta">Document type: Meeting Minutes · Meeting: Change Control Board, Nova EV · Date: 2026-06-12, 09:00 to 10:30 · Location: Building 4, room 2.14 and video · Minutes taken by: Gabriel Hoffmann</p>

## Attendees

Zain Kim (Change Manager, chair), Gabriel Hoffmann (Change Manager, minutes), Hannes Singh (Program Management), Kenji Wagner (Functional Safety), Katrin Jansen (High Voltage Battery Engineering, responsible for CR-0001), Jakob Wagner (Change Manager, responsible for CR-0005), Stefan Andersen (Change Manager, responsible for CR-0004), Ines Brown (High Voltage Battery Engineering).

Quorum according to CCP-09 was confirmed.

## Agenda

1. CR-0001 Raise insulation resistance threshold across HVB components
2. CR-0005 Update communication matrix of Electric Motor
3. CR-0004 Add diagnostic function of Telematics Control Unit
4. Retest planning for approved changes before MS-D

## 1. CR-0001 Raise insulation resistance threshold across HVB components

Katrin Jansen presented the change. The updated working summary of UN ECE R100 (version 2.0, 2026-04-14) raises the isolation resistance threshold in rule R100-6.1.1 from 100 Ω/V to 500 Ω/V. The change affects nine requirements across three components: the Cell Module (REQ-HVB-0047, REQ-HVB-0081, REQ-HVB-0144), the Battery Management System (REQ-HVB-0116, REQ-HVB-0127, REQ-HVB-0025) and the HV Junction Box (REQ-HVB-0117, REQ-HVB-0095, REQ-HVB-0003). Estimated cost 61,530.37 EUR, mostly retest effort. Because the threshold is a calibration parameter (DG-HV-006), no firmware release is needed.

Kenji Wagner confirmed there is no safety risk in raising the threshold.

**Decision D-2026-06-12-01: CR-0001 is approved.** Rationale: the change is required for regulatory compliance and introduces no safety risk. Based on CCP-04 (regulatory changes are approved by default) and R100-6.1.1. Status: Approved. Affects CR-0001 and the nine requirements listed above. Katrin Jansen coordinates as required by CCP-10.

**Decision D-2026-06-12-02: All test sets verifying the nine affected requirements are re-executed before Design Validation Complete (MS-D, 2026-10-16).** Rationale: an approved change invalidates the verification of the affected requirements. Based on CCP-05. Affects the same nine requirements. Owner: Katrin Jansen with the HV Testers (David Kovacs).

## 2. CR-0005 Update communication matrix of Electric Motor

Jakob Wagner presented the change. The proposal updates the communication matrix of the Electric Motor (CMP-EDU-02) to add two signals for diagnostic purposes. Estimated cost 138,993.76 EUR. The signals duplicate information already available from the Motor Control Unit.

**Decision D-2026-06-12-03: CR-0005 is rejected.** Rationale: the benefit does not justify the cost, the diagnostic information is already available. Based on CCP-07 (rejection criteria, cost). Status: Approved. Affects CR-0005.

## 3. CR-0004 Add diagnostic function of Telematics Control Unit

Stefan Andersen presented the change. The proposal adds a remote diagnostic function to the Telematics Control Unit (CMP-INF-03). Estimated cost 309,533.32 EUR, which is above the program management threshold of CCP-03. Hannes Singh asked for a cybersecurity assessment under ISO21434-10.4.1 before a decision.

**Decision D-2026-06-12-04: CR-0004 stays in status Proposed pending a cybersecurity assessment.** Rationale: the cost exceeds the CCP-03 threshold and the security impact is not assessed. Based on CCP-03 and ISO21434-10.4.1. Status: Approved. Affects CR-0004. Owner: Stefan Andersen with Jakob Nguyen (Infotainment Engineering). The board noted that under CCP-08 the proposal expires on 2026-10-24.

## 4. Retest planning for approved changes before MS-D

Ines Brown reported that the HIL bench is fully booked until mid-August. Retest of the CR-0001 test sets can start on 2026-08-17.

**Decision D-2026-06-12-05: Retest of the CR-0001 test sets is scheduled from 2026-08-17, HV Testers reserve the HIL bench for two weeks.** Rationale: bench availability. Based on LL-08. Status: Approved. Affects CR-0001.

## Actions

| Action | Owner | Due |
|---|---|---|
| Update calibration parameter and release calibration data set | Katrin Jansen | 2026-07-31 |
| Reserve HIL bench 2026-08-17 to 2026-08-28 | David Kovacs | 2026-06-19 |
| Cybersecurity assessment for CR-0004 | Jakob Nguyen | 2026-09-30 |
| Set CR-0005 to Rejected in the change tool | Jakob Wagner | 2026-06-13 |

Next Change Control Board: 2026-07-10.
