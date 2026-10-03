# UN ECE R100 Rev.3 Working Summary: Electrical Safety of the Traction Battery

<p class="meta">Document type: Standard (internal working summary) · Document ID: STD-UNECE-R100 · Version 2.0 · Published 2026-04-14 · Owner: High Voltage Battery Engineering (Ines Brown)</p>

## Purpose and scope

UN ECE Regulation No. 100 covers the electrical safety of vehicles with an electric power train. This working summary lists the provisions the Nova EV program treats as binding rules for the High Voltage Battery system and its components: the Battery Management System (CMP-HVB-01), the Cell Module (CMP-HVB-02), the Battery Housing (CMP-HVB-03), the HV Junction Box (CMP-HVB-04), the Battery Cooling Plate (CMP-HVB-05) and the Contactor Assembly (CMP-HVB-08).

Version 2.0 of this summary was issued after the target market update of April 2026. The main change is the isolation resistance threshold in rule R100-6.1.1, which moved from 100 Ω/V to 500 Ω/V for DC buses. This change is the reason for change request CR-0001 (Raise insulation resistance threshold across HVB components).

## Rules

### R100-5.1.1 Protection against direct contact

Live parts shall be protected against direct contact by enclosures or barriers meeting the specified protection degree. The Battery Housing and the HV Junction Box are the components that implement this rule. Requirements REQ-HVB-0012 and REQ-HVB-0024 (Battery Housing: Detect insulation faults) are related because the insulation monitoring confirms that the barrier is intact.

### R100-5.1.2 Protection against indirect contact

Exposed conductive parts shall be galvanically connected to the electrical chassis. Resistance between exposed conductive parts and the chassis shall be below 0.1 Ω at a current of at least 0.2 A.

### R100-6.1.1 Isolation resistance of DC buses

The isolation resistance between the high voltage DC bus and the electrical chassis shall be at least 500 Ω/V of the working voltage. This is the value that applies to the Nova EV target markets from April 2026. It replaces the former 100 Ω/V value used in the concept phase.

The requirements that satisfy this rule are all requirements of the type "Detect insulation faults" in the High Voltage Battery: REQ-HVB-0003 and REQ-HVB-0069 and REQ-HVB-0114 (HV Junction Box), REQ-HVB-0007 and REQ-HVB-0042 and REQ-HVB-0068 (Battery Management System), REQ-HVB-0006 and REQ-HVB-0051 and REQ-HVB-0096 (Contactor Assembly), REQ-HVB-0094 and REQ-HVB-0157 (Cell Module).

### R100-6.1.2 Isolation resistance monitoring

An on-board isolation resistance monitoring system shall be provided, together with a warning to the driver when the isolation resistance drops below the minimum value. The Battery Management System implements the monitoring, the HV Junction Box provides the measurement point. REQ-HVB-0007 (Battery Management System: Detect insulation faults) is the leading requirement.

### R100-6.2.1 Isolation resistance after water exposure

The isolation resistance requirement shall also be met after the vehicle has been exposed to the washing and immersion procedures described in the regulation. The Battery Housing and the Battery Cooling Plate are affected. REQ-HVB-0058 and REQ-HVB-0125 (Battery Cooling Plate: Detect insulation faults) verify this.

### R100-7.2.1 Protection against overcurrent

The traction battery shall be protected against overcurrent by a device that interrupts the current within the specified time. The Contactor Assembly is the interrupting device. REQ-HVB-0025 (Battery Management System: Open the contactors on overcurrent) and REQ-HVB-0081 (Cell Module: Open the contactors on overcurrent) satisfy this rule.

## Impact of version 2.0 on the program

Change request CR-0001 raises the threshold in the affected requirements from 100 Ω/V to 500 Ω/V. The change was approved by the Change Control Board on 2026-06-12 based on rule R100-6.1.1 of this document. All test sets verifying the affected requirements have to be re-executed before Design Validation Complete (MS-D, 2026-10-16). Retest is coordinated by Katrin Jansen with the HV Testers.

## Applicability matrix

| Rule | Components | Leading requirements |
|---|---|---|
| R100-5.1.1 | Battery Housing, HV Junction Box | REQ-HVB-0012, REQ-HVB-0024 |
| R100-5.1.2 | Battery Housing | Design guideline DG-HV-004 |
| R100-6.1.1 | HV Junction Box, Battery Management System, Contactor Assembly, Cell Module | REQ-HVB-0003, REQ-HVB-0007, REQ-HVB-0006, REQ-HVB-0094 |
| R100-6.1.2 | Battery Management System, HV Junction Box | REQ-HVB-0007, REQ-HVB-0069 |
| R100-6.2.1 | Battery Housing, Battery Cooling Plate | REQ-HVB-0058, REQ-HVB-0125 |
| R100-7.2.1 | Contactor Assembly, Battery Management System | REQ-HVB-0025, REQ-HVB-0081 |
