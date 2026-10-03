# IEC 62660-2 Working Summary: Reliability and Abuse Testing of Traction Cells

<p class="meta">Document type: Standard (internal working summary) · Document ID: STD-IEC62660-2 · Version 1.0 · Published 2025-05-20 · Owner: HV Testers (David Kovacs)</p>

## Purpose and scope

IEC 62660-2 specifies reliability and abuse test procedures for lithium-ion cells used in electric vehicles. This working summary selects the procedures that the Nova EV program applies to the Cell Module (CMP-HVB-02), the Cell Stack (CMP-HVB-07) and the Cell Monitoring Unit (CMP-HVB-06), and defines how each procedure maps to a test case type in the test management tool.

The summary is maintained by the HV Testers team. It is the reference for the test set structure under the High Voltage Battery requirements.

## Rules

### IEC62660-2-6.2.1 Vibration

Cells and modules shall withstand the vibration profile specified for the mounting location without loss of function, leakage or venting. The test case type "Vibration profile" implements this rule. It is part of every test set that verifies a Cell Module or Cell Stack requirement, for example the test sets under REQ-HVB-0028 and REQ-HVB-0124 (Cell Stack: Enter a safe state on communication loss).

### IEC62660-2-6.2.2 Mechanical shock

Modules shall withstand half-sine shock pulses in three axes. Verification is done at module level on the Cell Module. No cell-level test is required when the module test passes.

### IEC62660-2-6.3.1 Thermal cycling

Cells shall be cycled between -40 °C and +85 °C for the specified number of cycles. Capacity loss after cycling shall be below 5 percent. The test case types "Cold start at -30 °C" and "High temperature at +60 °C" cover the functional part of this rule for the Cell Monitoring Unit, for example REQ-HVB-0146 (Cell Monitoring Unit: Detect insulation faults).

### IEC62660-2-6.4.1 Overcharge

Cells shall be charged beyond the upper voltage limit until the protection acts. The cell shall not ignite or explode. The protection function is a requirement of the Battery Management System, REQ-HVB-0001 (HV Junction Box: Limit charge current) provides the current limitation on the pack side.

### IEC62660-2-6.4.3 External short circuit

Cells shall be short-circuited externally with a defined resistance. The overcurrent protection shall interrupt the current. This rule is verified together with REQ-HVB-0025 and REQ-HVB-0081 (Open the contactors on overcurrent). The Contactor Assembly (CMP-HVB-08) is the interrupting element.

### IEC62660-2-6.5.1 Endurance

Cells shall be cycled at the specified depth of discharge until the end-of-life criterion is reached. The test case type "Endurance run" implements this rule for the program. Endurance results feed the state-of-health estimation, REQ-HVB-0047 (Cell Module: Report state of charge) depends on the endurance model.

## Test planning notes

The test sets for the Cell Module and the Cell Stack that are required for Design Validation Complete (MS-D, 2026-10-16) are executed by the HV Testers. Test planning in the tool follows a fixed pattern per requirement: a nominal test, an environmental test and one abuse or endurance test. Test cases are named after the type and carry the test set identifier in brackets, for example "Vibration profile (TS-HVB-0012)".

Test benches: the climate chamber and the HIL bench are shared with the Thermal Management team. Bench conflicts are resolved in the weekly test planning meeting.

## Applicability matrix

| Rule | Components | Test case type | Related requirements |
|---|---|---|---|
| IEC62660-2-6.2.1 | Cell Module, Cell Stack | Vibration profile | REQ-HVB-0028, REQ-HVB-0124 |
| IEC62660-2-6.2.2 | Cell Module | Vibration profile | REQ-HVB-0017 |
| IEC62660-2-6.3.1 | Cell Monitoring Unit | Cold start, High temperature | REQ-HVB-0146 |
| IEC62660-2-6.4.1 | Battery Management System, HV Junction Box | Overvoltage 16 V, Boundary values | REQ-HVB-0001 |
| IEC62660-2-6.4.3 | Contactor Assembly | Fault injection | REQ-HVB-0025, REQ-HVB-0081 |
| IEC62660-2-6.5.1 | Cell Module | Endurance run | REQ-HVB-0047 |
