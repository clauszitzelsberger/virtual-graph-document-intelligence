# Best Practice: Gate Driver Board Design for Traction Inverters

<p class="meta">Document type: Best Practice · Document ID: BP-GDB · Version 1.0 · Published 2026-02-16 · Authors: Katrin Larsen, Xenia Müller (Electric Drive Unit Engineering)</p>

## Why this document exists

The Gate Driver Board (CMP-EDU-06) is a sub-component of the Traction Inverter (CMP-EDU-01). It drives the power switches and is the last line of defence between a control error and a destroyed inverter. This best practice describes how the Nova EV gate driver was designed and what the team would do differently after the first prototype builds.

## Architecture in one paragraph

The Gate Driver Board receives switching commands from the Motor Control Unit (CMP-EDU-04), isolates them, drives the gates of the power modules and monitors desaturation, gate voltage and temperature. On a fault it turns the switches off within 2 µs, latches a diagnostic error code and reports it to the Motor Control Unit, which decides whether to derate, to open the park lock actuator interlock or to shut down.

## Practices

### BP-GDB-01 Separate the fault path from the control path

The fault shutdown is implemented in hardware and does not depend on the firmware. Firmware only reports and latches. This is the reason REQ-EDU-0005 (Gate Driver Board: Control field weakening) and REQ-EDU-0117 (Gate Driver Board: Engage the park lock) can be verified independently: field weakening is control path, park lock interlock is fault path.

### BP-GDB-02 Verify error codes with fault injection

Every diagnostic error code shall be provoked at least once in a "Fault injection" test case and the reported code shall be compared with the expected code. This practice found DEF-1114 (Gate Driver Board: wrong error code reported) in test case TC-03679 on 2026-05-22: a desaturation fault was reported with the code of a gate undervoltage fault. The defect is Critical because the Motor Control Unit reacts differently to the two faults. It is still Open and blocks test set TS-EDU-0152, which is required for Design Validation Complete (MS-D).

### BP-GDB-03 Derating before shutdown

The board reports temperature to the Motor Control Unit early enough for a derating step before the hardware over-temperature shutdown acts. REQ-EDU-0069 (Electric Motor: Derate on overtemperature) depends on this signal. That requirement is currently covered by a single test case and is listed under RTP-06.

### BP-GDB-04 Isolation and creepage

Gate driver isolation follows the same creepage rule as the battery, DG-HV-001, because the board carries the DC link voltage. The rule is verified by design review, not by test.

### BP-GDB-05 Supplier firmware is part of the design

The isolation driver ICs run supplier firmware. Supplier firmware updates are treated as changes under the Change Control Policy and require a retest of the fault injection test cases. The escalation of DEF-1114 in September 2026 concluded that replacement samples with updated supplier firmware are needed before the retest.

### BP-GDB-06 Coverage on the fault reporting firmware

The fault reporting firmware is safety-classified and shall reach MC/DC coverage as required by ISO26262-6-9.4.2. The coverage report is part of the release evidence for each firmware version.

## Lessons from the first prototype builds

Fault injection tests found more defects than all environmental tests together. The team recommends planning at least one fault injection case per diagnostic error code from the start, and reserving HIL bench time for it early, because the HIL bench is shared with the High Voltage Battery team.

## People

Gate Driver Board requirements are owned by the Electric Drive Unit Engineering team: Xenia Müller, Emre Bianchi, Rafael Schulz, Mateo Sato, Zoe Kovacs, David Horvath, Vera Schneider, Katrin Larsen, Lukas Horvath and Gabriel Patel. DEF-1114 is owned by David Horvath. Fault injection tests are executed by the HV Testers, Fatima Kim executed TC-03679.
