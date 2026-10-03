# Design Guideline: Interior Lighting Electronics

<p class="meta">Document type: Design Guideline · Document ID: DG-ILT · Version 1.1 · Published 2025-04-07 · Owner: Interior Lighting Engineering (Olivia Schulz)</p>

## Scope

This guideline applies to the electronics of the Interior Lighting system of the Nova EV: the Ambient Light Controller (CMP-ILT-01), the LED Light Strip (CMP-ILT-02), the Reading Lamp (CMP-ILT-03), the Footwell Light (CMP-ILT-04), the Dome Light (CMP-ILT-05), the LED Driver Board (CMP-ILT-06), the Light Guide (CMP-ILT-07) and the Touch Switch (CMP-ILT-08).

## Rules

### DG-ILT-01 Current limit per LED channel

Each LED channel shall be current-limited to 150 mA by hardware on the LED Driver Board, independent of software. A software failure shall never lead to an LED current above the limit. REQ-ILT-0001 (Reading Lamp: Limit current per channel) implements this rule.

### DG-ILT-02 Dimming with vehicle speed

Ambient light intensity shall be reduced linearly from 100 percent at standstill to 40 percent at 130 km/h. The dimming curve shall be a calibration table. REQ-ILT-0004 (LED Light Strip: Dim ambient light with vehicle speed) implements this rule.

### DG-ILT-03 Switch-off after timeout

Any interior light that is switched on manually shall switch off automatically after a configurable timeout, 10 minutes by default, when the vehicle is locked. REQ-ILT-0005 (Footwell Light: Switch off after a timeout) and REQ-ILT-0090 (Touch Switch: Switch off after a timeout) implement this rule. REQ-ILT-0090 has no test set yet and is reported under the Requirement Traceability Policy, rule RTP-01.

### DG-ILT-04 Colour consistency

All ambient light sources in the cabin shall show the same colour within a tolerance of 0.01 in the CIE 1931 colour space when set to the same drive mode. REQ-ILT-0059 (Ambient Light Controller: Match light color to the drive mode) and REQ-ILT-0062 (LED Light Strip: Match light color to the drive mode) implement this rule.

### DG-ILT-05 Fade times

Switching lights on or off shall use a fade of 300 ms to 800 ms. Hard switching is allowed only for the hazard warning flash function.

### DG-ILT-06 LED failure reporting

The LED Driver Board shall detect an open or shorted LED channel and report it as a diagnostic error code. The remaining channels shall stay operational.

### DG-ILT-07 Touch switch debouncing

The Touch Switch shall debounce inputs over at least 40 ms and shall ignore touches shorter than 30 ms, so that vibration does not trigger the switch.

### DG-ILT-08 Communication with infotainment

The Ambient Light Controller shall receive the theme from the Head Unit (CMP-INF-01) over the vehicle network and shall keep the last theme when the connection is lost. REQ-ILT-0003 (Dome Light: Sync with the infotainment theme) implements this rule.

## Verification

Rules DG-ILT-01 and DG-ILT-06 are verified with the test case types "Overvoltage 16 V" and "Fault injection". Rule DG-ILT-02 is verified with "Boundary values". Defect DEF-0375 (Ambient Light Controller: value out of tolerance), open with severity Critical on a test set required for Prototype Build Release (MS-C), is a violation of DG-ILT-04.

## Applicability matrix

| Rule | Components | Requirements |
|---|---|---|
| DG-ILT-01 | LED Driver Board, Reading Lamp | REQ-ILT-0001 |
| DG-ILT-02 | Ambient Light Controller, LED Light Strip | REQ-ILT-0004 |
| DG-ILT-03 | Footwell Light, Touch Switch | REQ-ILT-0005, REQ-ILT-0090 |
| DG-ILT-04 | Ambient Light Controller, LED Light Strip | REQ-ILT-0059, REQ-ILT-0062 |
| DG-ILT-08 | Ambient Light Controller, Dome Light | REQ-ILT-0003 |
