# Best Practice: Designing the Battery Management System

<p class="meta">Document type: Best Practice · Document ID: BP-BMS · Version 1.0 · Published 2025-11-24 · Authors: Katrin Jansen, Sofia Hoffmann (High Voltage Battery Engineering)</p>

## Why this document exists

The Battery Management System (CMP-HVB-01) is the component with the most requirements, the most test sets and the most defects in the High Voltage Battery. This best practice collects what the team learned while bringing the Nova EV battery from concept to Design Freeze. It complements the Design Guideline for Battery Management System Software (DG-BMS) with the reasoning behind the rules.

## Architecture in one paragraph

The Battery Management System is the master controller of the pack. It talks to up to twelve Cell Monitoring Units (CMP-HVB-06), one per Cell Module (CMP-HVB-02), over an isolated daisy chain. It measures pack current and insulation resistance through the HV Junction Box (CMP-HVB-04), commands the Contactor Assembly (CMP-HVB-08) and reports state of charge, state of health and limits to the vehicle. Cooling requests go to the Thermal Control Unit (CMP-THM-04), which controls the Battery Cooling Plate (CMP-HVB-05).

## Practices

### BP-BMS-01 Treat the safe state as the primary function

Everything else is secondary. The first requirement written for the component was REQ-HVB-0101 (Battery Management System: Enter a safe state on communication loss), and the fault tolerant time interval of 100 ms from DG-BMS-01 drove the choice of the processor and the operating system. Design the fault reaction path first and fit the rest around it.

### BP-BMS-02 Make thresholds calibration parameters

The insulation threshold, the communication timeout and the balancing window are calibration parameters, not constants in code. This practice paid off in 2026 when UN ECE R100 rule R100-6.1.1 moved the insulation threshold from 100 Ω/V to 500 Ω/V. Change request CR-0001 (Raise insulation resistance threshold across HVB components) could be implemented as a calibration change plus retest, at a cost of about 61,530 EUR, instead of a firmware release.

### BP-BMS-03 One diagnostic error code per fault, forever

Error codes are part of the service interface and are never reused. A wrong error code is treated as a Critical defect under DG-BMS-06. The cost of this discipline is small; the cost of a misleading service diagnosis in the field is not.

### BP-BMS-04 Test the boundaries, not only the nominal case

Most defects on the Battery Management System were found in "Boundary values", "Undervoltage 9 V" and "Fault injection" test cases, not in "Nominal operation". DEF-0039 (Battery Management System: intermittent CAN timeout) was found in an undervoltage test of TS-HVB-0006 and led to a software fix and to the addition of the timeout parameter to the boundary tests. Plan the environmental and boundary test cases first when creating a test set.

### BP-BMS-05 Log temperatures with enough resolution

Cell temperature logs with 1 K resolution hid a cooling imbalance during endurance runs. DG-BMS-03 now requires 0.5 K. The requirements REQ-HVB-0116 (Battery Management System: Log cell temperatures) and REQ-HVB-0117 (HV Junction Box: Log cell temperatures) carry this resolution. REQ-HVB-0059 (Battery Management System: Log cell temperatures) still has only a single test case and should be extended under RTP-06.

### BP-BMS-06 Keep balancing out of the drive cycle

Passive balancing while driving heats the balancing resistors at the worst possible time. DG-BMS-02 restricts balancing to charging and rest. REQ-HVB-0127 (Battery Management System: Balance cell voltages) reflects this and is one of the requirements affected by CR-0001 because the balancing check shares the measurement path with insulation monitoring.

### BP-BMS-07 Review the contactor feedback path in every design review

Contactor welding in the Gen1 program (lesson LL-01) was only detected late because there was no position feedback. DG-HV-008 now requires auxiliary contacts and DG-HV-002 requires a pre-charge circuit. Both are reviewed at every design review of the Contactor Assembly.

## People

Battery Management System requirements are owned by the High Voltage Battery Engineering team: Jakob Martin, Isabel Martin, Sofia Hoffmann, Ulla Becker, Yusuf Nguyen, Vera Johansson, Ines Brown, Katrin Jansen, Carlos de Vries and Priya Chen. Software test sets are executed by the HV Testers, coordinated by David Kovacs.
