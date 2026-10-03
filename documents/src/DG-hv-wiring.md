# Design Guideline: High Voltage Wiring and Contactors

<p class="meta">Document type: Design Guideline · Document ID: DG-HV · Version 2.2 · Published 2025-06-30 · Owner: High Voltage Battery Engineering (Jakob Martin)</p>

## Scope

This guideline applies to the high voltage wiring inside the traction battery and to the switching elements: the HV Junction Box (CMP-HVB-04), the Contactor Assembly (CMP-HVB-08) and the connection to the Traction Inverter (CMP-EDU-01). It translates the electrical safety rules of UN ECE R100 into design rules the layout and hardware engineers apply directly.

## Rules

### DG-HV-001 Minimum creepage and clearance

The creepage distance between high voltage conductors and low voltage traces or the chassis shall be at least 8 mm, the clearance at least 5.5 mm. Where pollution degree 3 applies, creepage shall be at least 12.5 mm. This rule supports R100-6.1.1.

### DG-HV-002 Pre-charge circuit before main contactor closing

The main contactors shall never close against a discharged DC link. A pre-charge relay with a series resistor shall bring the DC link to within 10 percent of the pack voltage before the main contactor closes. This rule originates from lesson LL-01 of the Gen1 battery program, where contactor welding was observed.

### DG-HV-003 Contactor opening on overcurrent

The Contactor Assembly shall be able to interrupt the specified overcurrent within 20 ms after detection by the Battery Management System. REQ-HVB-0025 (Battery Management System: Open the contactors on overcurrent) and REQ-HVB-0081 (Cell Module: Open the contactors on overcurrent) implement this rule.

### DG-HV-004 Potential equalisation

All exposed conductive parts of the battery housing and the junction box shall be bonded to the chassis with a resistance below 0.1 Ω. This rule implements R100-5.1.2.

### DG-HV-005 Insulation monitoring measurement point

The insulation monitoring device shall measure between the DC bus and the chassis at a point downstream of the main contactors, inside the HV Junction Box. Requirements REQ-HVB-0003, REQ-HVB-0069 and REQ-HVB-0114 (HV Junction Box: Detect insulation faults) implement this rule.

### DG-HV-006 Insulation threshold parameter

The insulation resistance threshold shall be a calibration parameter, not a compile-time constant, so that a regulatory change can be applied without a software release. The threshold was changed from 100 Ω/V to 500 Ω/V by change request CR-0001 in 2026. Because the threshold is a parameter, CR-0001 required only calibration and retest, no new firmware.

### DG-HV-007 Wire colour and marking

High voltage cables shall be orange over their whole length and shall carry the voltage class marking every 300 mm.

### DG-HV-008 Redundant contactor position feedback

Each main contactor shall provide an auxiliary contact for position feedback. The Battery Management System shall compare commanded and reported position and enter the safe state on mismatch, see REQ-HVB-0101 (Battery Management System: Enter a safe state on communication loss) for the safe state definition.

## Verification

The rules of this guideline are verified with the test case types "Fault injection" (DG-HV-003, DG-HV-008), "Boundary values" (DG-HV-006) and by design review (DG-HV-001, DG-HV-004, DG-HV-007). Defect DEF-0026 (HV Junction Box: incorrect unit conversion), found in a boundary values test of TS-HVB-0003 and resolved by a calibration correction, was a violation of DG-HV-006 in the calibration data.

## Applicability matrix

| Rule | Components | Requirements | Source |
|---|---|---|---|
| DG-HV-001 | HV Junction Box, Battery Housing | Design review | R100-6.1.1 |
| DG-HV-002 | Contactor Assembly | Design review | LL-01 |
| DG-HV-003 | Contactor Assembly, Battery Management System | REQ-HVB-0025, REQ-HVB-0081 | R100-7.2.1 |
| DG-HV-004 | Battery Housing, HV Junction Box | Design review | R100-5.1.2 |
| DG-HV-005 | HV Junction Box | REQ-HVB-0003, REQ-HVB-0069, REQ-HVB-0114 | R100-6.1.2 |
| DG-HV-006 | Battery Management System | REQ-HVB-0007, REQ-HVB-0042 | R100-6.1.1 |
| DG-HV-008 | Contactor Assembly, Battery Management System | REQ-HVB-0101 | ISO26262-6-7.4.5 |
