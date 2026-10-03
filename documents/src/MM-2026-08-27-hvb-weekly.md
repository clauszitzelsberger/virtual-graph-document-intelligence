# High Voltage Battery Engineering Weekly 2026-08-27

<p class="meta">Document type: Meeting Minutes · Meeting: High Voltage Battery Engineering Weekly · Date: 2026-08-27, 13:00 to 14:00 · Location: Building 7, battery lab meeting room · Minutes taken by: Yusuf Nguyen</p>

## Attendees

Jakob Martin (System Engineer, chair), Isabel Martin, Sofia Hoffmann, Ulla Becker (System Engineers), Yusuf Nguyen, Vera Johansson, Ines Brown (Requirements Engineers), Katrin Jansen, Carlos de Vries, Priya Chen (Software Engineers), David Kovacs and Lukas Okafor (HV Testers, guests).

## 1. Retest status for CR-0001

Katrin Jansen reported on the retest of the test sets affected by CR-0001 (Raise insulation resistance threshold across HVB components). The calibration data set with the 500 Ω/V threshold was released on 2026-07-29. Retest on the HIL bench started on 2026-08-17 as decided by the Change Control Board on 2026-06-12. Test set TS-HVB-0003 (verifying REQ-HVB-0003, HV Junction Box: Detect insulation faults) passed on 2026-08-21 after the two defects on its boundary values test case were resolved. TS-HVB-0004, the second test set of the same requirement, is still in progress.

## 2. Defects closed since last week

Carlos de Vries reported DEF-0025 (HV Junction Box: state machine stuck) as Resolved. The state machine did not leave the measurement state when the insulation value crossed the new threshold during the transition. Resolution: software fix.

Aisha Larsen reported DEF-0026 (HV Junction Box: incorrect unit conversion) as Resolved. The calibration data used kΩ where the software expected Ω/V. Resolution: calibration parameter corrected. Ines Brown noted this is a repeat of lesson LL-02: the fault first appeared as a CAN timeout on the bench.

**Decision D-2026-08-27-01: The calibration data release checklist gets a mandatory unit check for every threshold parameter.** Rationale: DEF-0026 was caused by a unit mismatch that a checklist would have caught. Based on DG-HV-006 and LL-03. Status: Approved. Affects DEF-0026 and the Battery Management System (CMP-HVB-01). Owner: Carlos de Vries.

## 3. Wording of REQ-HVB-0116

Vera Johansson raised that REQ-HVB-0116 (Battery Management System: Log cell temperatures) does not state the logging resolution. The design guideline DG-BMS-03 requires 0.5 K, and REQ-HVB-0117 (HV Junction Box: Log cell temperatures) already carries it.

**Decision D-2026-08-27-02: REQ-HVB-0116 is reworded to state the 0.5 K resolution and the persistence on safe state transition.** Rationale: alignment with DG-BMS-03 and consistency with REQ-HVB-0117. Based on DG-BMS-03. Status: Approved. Affects REQ-HVB-0116. Owner: Vera Johansson. No new test set is needed, the existing "Endurance run" test cases already measure the resolution.

## 4. Single test case on REQ-HVB-0059

Yusuf Nguyen reported that the Quality Assurance traceability report lists REQ-HVB-0059 (Battery Management System: Log cell temperatures) with a single test case, which violates RTP-06 for a safety-classified component.

**Decision D-2026-08-27-03: A second test case of type "Cold start at -30 °C" is added to the test set of REQ-HVB-0059 before Pre-Series Release (MS-E).** Rationale: RTP-06 requires at least two test cases for safety-classified components. Based on RTP-06. Status: Proposed, to be confirmed with the HV Testers. Affects REQ-HVB-0059. Owner: Sofia Hoffmann with David Kovacs.

## 5. Bench planning

David Kovacs reported that the climate chamber is booked by Thermal Management for the EMC and thermal retests of the Thermal Control Unit around DEF-0325 until 2026-09-11. HV Testers keep the HIL bench until 2026-08-28 as planned, then it goes to the Electric Drive Unit team for the DEF-1114 retest preparation.

## Actions

| Action | Owner | Due |
|---|---|---|
| Add unit check to calibration release checklist | Carlos de Vries | 2026-09-10 |
| Reword REQ-HVB-0116 in the requirements tool | Vera Johansson | 2026-09-03 |
| Agree second test case for REQ-HVB-0059 with HV Testers | Sofia Hoffmann | 2026-09-17 |
| Report TS-HVB-0004 result | Katrin Jansen | 2026-09-03 |

Next weekly: 2026-09-03.
