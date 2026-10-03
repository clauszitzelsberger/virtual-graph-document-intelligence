# ISO 26262-6 Working Summary: Software Level Product Development

<p class="meta">Document type: Standard (internal working summary) · Document ID: STD-ISO26262-6 · Version 1.2 · Published 2025-02-10 · Owner: Functional Safety (Kenji Wagner)</p>

## Purpose and scope

This working summary condenses the parts of ISO 26262-6 that apply to software developed for the Nova EV program. It is not the standard text. It restates the requirements that our Functional Safety team has selected as binding rules for the program, gives each one a stable rule identifier, and maps it to the project requirements that satisfy it. Rule identifiers are used in design reviews, in change requests and in test specifications.

The summary applies to all software components of the High Voltage Battery, the Electric Drive Unit and the Driver Assistance systems that carry a safety classification. The Battery Management System (CMP-HVB-01), the Cell Monitoring Unit (CMP-HVB-06), the Gate Driver Board (CMP-EDU-06) and the Perception Module (CMP-ADS-06) are in scope.

## Rules

### ISO26262-6-7.4.1 Software safety requirements shall be derived from the technical safety concept

Every software safety requirement shall trace to a technical safety requirement and to the hardware element it protects. A requirement without such a trace is not accepted for a safety-classified component. In the Nova EV requirement set this is fulfilled by the component assignment of each requirement, for example REQ-HVB-0101 (Battery Management System: Enter a safe state on communication loss) traces to the Battery Management System.

### ISO26262-6-7.4.5 Safe state shall be reached within the fault tolerant time interval

Software shall transition the element to its safe state within the fault tolerant time interval after a fault is detected. For the Nova EV battery the interval is 100 ms for communication loss and 20 ms for insulation faults. Requirements REQ-HVB-0101, REQ-HVB-0128 (Cell Monitoring Unit: Enter a safe state on communication loss) and REQ-HVB-0017 (Cell Module: Enter a safe state on communication loss) satisfy this rule.

### ISO26262-6-9.4.2 Structural coverage at the software unit level

For units with the highest safety classification, structural coverage shall be measured and MC/DC coverage shall be achieved. Statement and branch coverage alone are not sufficient. This applies to the Battery Management System software and to the Gate Driver Board firmware. Requirement REQ-EDU-0005 (Gate Driver Board: Control field weakening) is verified under this rule.

### ISO26262-6-9.4.3 Fault injection testing at the unit level

Fault injection tests shall be carried out to demonstrate that the software detects and handles the specified faults. The test case type "Fault injection" in the test management tool implements this rule. The open defect DEF-1114 (Gate Driver Board: wrong error code reported) was found by test case TC-03679, a fault injection test, and is a direct consequence of applying this rule.

### ISO26262-6-10.4.3 Software integration testing shall cover interfaces

Interfaces between software units and between software and hardware shall be tested for correct timing, data consistency and error handling. The requirement REQ-HVB-0116 (Battery Management System: Log cell temperatures) and REQ-HVB-0117 (HV Junction Box: Log cell temperatures) are integration-tested under this rule.

### ISO26262-6-11.4.1 Verification of software safety requirements in the target environment

The software safety requirements shall be verified on the target hardware, under representative environmental conditions. Test case types "Cold start at -30 °C" and "High temperature at +60 °C" satisfy this rule for the environmental part.

## Applicability matrix

| Rule | Component | Requirements | Verification |
|---|---|---|---|
| ISO26262-6-7.4.1 | All safety-classified components | All | Traceability review |
| ISO26262-6-7.4.5 | Battery Management System, Cell Monitoring Unit, Cell Module | REQ-HVB-0101, REQ-HVB-0128, REQ-HVB-0017 | Timing test on HIL |
| ISO26262-6-9.4.2 | Battery Management System, Gate Driver Board | REQ-EDU-0005, REQ-HVB-0127 | Coverage report |
| ISO26262-6-9.4.3 | Gate Driver Board | REQ-EDU-0005, REQ-EDU-0117 | TC-03679 and related fault injection cases |
| ISO26262-6-10.4.3 | Battery Management System, HV Junction Box | REQ-HVB-0116, REQ-HVB-0117 | Integration test |
| ISO26262-6-11.4.1 | All | All | Environmental test cases |

## Notes for the program

The Functional Safety team reviews this summary at every milestone gate. The last review before Design Freeze (MS-B, 2026-03-20) found no gaps. The next review is scheduled for Design Validation Complete (MS-D, 2026-10-16). Contact: Kenji Wagner, Felix Singh, Ben Wilson.
