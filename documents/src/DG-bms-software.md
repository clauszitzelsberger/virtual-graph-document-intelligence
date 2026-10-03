# Design Guideline: Battery Management System Software

<p class="meta">Document type: Design Guideline · Document ID: DG-BMS · Version 1.4 · Published 2025-08-18 · Owner: High Voltage Battery Engineering (Katrin Jansen)</p>

## Scope

This guideline defines the software architecture rules for the Battery Management System (CMP-HVB-01) and the Cell Monitoring Unit (CMP-HVB-06) of the Nova EV traction battery. It applies to all software requirements of these components and is the reference for code reviews and for the software test sets.

## Rules

### DG-BMS-01 Safe state on communication loss within 100 ms

When the Battery Management System loses communication with the vehicle network or with a Cell Monitoring Unit for more than 100 ms, it shall open the contactors and enter the safe state. The timeout shall be a calibration parameter. Requirements REQ-HVB-0101 (Battery Management System: Enter a safe state on communication loss), REQ-HVB-0128, REQ-HVB-0164 and REQ-HVB-0170 (Cell Monitoring Unit: Enter a safe state on communication loss) implement this rule. It satisfies ISO26262-6-7.4.5.

### DG-BMS-02 Cell voltage balancing

Passive balancing shall keep the spread between the highest and the lowest cell voltage below 20 mV at the end of charge. Balancing shall run only while the pack is charging or resting, never while driving. REQ-HVB-0127 (Battery Management System: Balance cell voltages) implements this rule.

### DG-BMS-03 Temperature logging

Cell temperatures shall be sampled every 100 ms and logged with a resolution of 0.5 K. The log shall be persisted at least once per minute and on every transition to the safe state. REQ-HVB-0116 (Battery Management System: Log cell temperatures) and REQ-HVB-0117 (HV Junction Box: Log cell temperatures) implement this rule. The wording of REQ-HVB-0116 was aligned with this rule in the HVB weekly on 2026-08-27.

### DG-BMS-04 State of charge reporting

State of charge shall be reported every 100 ms with a tolerance of 3 percent over the operating temperature range. REQ-HVB-0005 (Battery Management System: Report state of charge) and REQ-HVB-0047 (Cell Module: Report state of charge) implement this rule.

### DG-BMS-05 Insulation fault detection

The insulation resistance shall be evaluated against the threshold parameter every 500 ms. A value below the threshold for three consecutive samples is an insulation fault. Requirements REQ-HVB-0007, REQ-HVB-0042 and REQ-HVB-0068 (Battery Management System: Detect insulation faults) implement this rule. The threshold parameter is described in DG-HV-006 and was raised by CR-0001.

### DG-BMS-06 Diagnostic error codes

Every detected fault shall be reported with a unique diagnostic error code. Error codes shall never be reused for different faults. An error code reported for the wrong fault is a Critical defect, because it misleads the service diagnosis.

### DG-BMS-07 Overcurrent handling

On overcurrent the Battery Management System shall command the contactors open within 10 ms and report the event. REQ-HVB-0025 (Battery Management System: Open the contactors on overcurrent) implements this rule together with DG-HV-003.

### DG-BMS-08 Unit test coverage

Software units of the Battery Management System shall reach 100 percent MC/DC coverage before integration. This implements ISO26262-6-9.4.2.

## Verification

Rules DG-BMS-01, DG-BMS-05 and DG-BMS-07 are verified on the HIL bench with the test case types "Fault injection" and "Boundary values". Rule DG-BMS-03 is verified in the "Endurance run" test cases. Defect DEF-0039 (Battery Management System: intermittent CAN timeout), found in an undervoltage test of TS-HVB-0006 in 2025 and resolved by a software fix, was the reason to add the timeout parameter of DG-BMS-01 to the boundary values tests.

## Applicability matrix

| Rule | Components | Requirements | Satisfies |
|---|---|---|---|
| DG-BMS-01 | Battery Management System, Cell Monitoring Unit | REQ-HVB-0101, REQ-HVB-0128, REQ-HVB-0164, REQ-HVB-0170 | ISO26262-6-7.4.5 |
| DG-BMS-02 | Battery Management System | REQ-HVB-0127 | |
| DG-BMS-03 | Battery Management System, HV Junction Box | REQ-HVB-0116, REQ-HVB-0117 | ISO26262-6-10.4.3 |
| DG-BMS-04 | Battery Management System, Cell Module | REQ-HVB-0005, REQ-HVB-0047 | |
| DG-BMS-05 | Battery Management System | REQ-HVB-0007, REQ-HVB-0042, REQ-HVB-0068 | R100-6.1.2 |
| DG-BMS-07 | Battery Management System | REQ-HVB-0025 | R100-7.2.1 |
| DG-BMS-08 | Battery Management System | All software requirements | ISO26262-6-9.4.2 |
