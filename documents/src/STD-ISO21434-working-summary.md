# ISO/SAE 21434 Working Summary: Cybersecurity for Connected Vehicle Functions

<p class="meta">Document type: Standard (internal working summary) · Document ID: STD-ISO21434 · Version 1.1 · Published 2025-09-02 · Owner: Infotainment Engineering (Jakob Nguyen)</p>

## Purpose and scope

ISO/SAE 21434 defines cybersecurity engineering for road vehicles. This working summary extracts the rules the Nova EV program applies to the connected functions of the Infotainment system: the Head Unit (CMP-INF-01), the Telematics Control Unit (CMP-INF-03) and the LTE Modem (CMP-INF-07). The Driver Assistance domain controller (CMP-ADS-01) is in scope where it receives data over the vehicle network from these components.

## Rules

### ISO21434-9.3.1 Item definition and cybersecurity goals

Each connected function shall have a documented item definition with assets, attack paths and cybersecurity goals. The over-the-air update function and the phone pairing function of the Head Unit are two items. REQ-INF-0011 (Head Unit: Download an over-the-air update) and REQ-INF-0120 (Head Unit: Pair a phone via Bluetooth) are the leading requirements.

### ISO21434-10.4.1 Cybersecurity requirements shall be allocated to components

Cybersecurity requirements shall be allocated to the components that implement them. Encryption of telematics traffic is allocated to the Telematics Control Unit, see REQ-INF-0001 (LTE Modem: Boot to the home screen) for the boot integrity part and the Telematics Control Unit requirements for the transport encryption part.

### ISO21434-10.4.4 Secure update

Software updates shall be authenticated and integrity-protected before installation. A failed authentication shall leave the previous software fully functional. REQ-INF-0011 satisfies this rule. Verification includes the test case type "Regression after software update".

### ISO21434-11.4.2 Verification shall include robustness testing

Interfaces exposed to external networks shall be tested for robustness, including malformed input and timing attacks. The test case types "Fault injection" and "EMC immunity" are used as the robustness tests for the Head Unit and the Telematics Control Unit.

### ISO21434-13.3.1 Cybersecurity incident response

Vulnerabilities and incidents found during development shall be recorded as defects with a severity and an owner, and shall be tracked to closure. The defect management process of the program fulfils this rule. Defect DEF-0078 (Head Unit: sporadic false trigger), which is open with severity Critical, is tracked under this rule because it affects the over-the-air update path.

## Program status

The Head Unit currently carries two open critical defects that touch connected functions: DEF-0078 (sporadic false trigger during the vibration profile test TC-00291) and DEF-0952 (Head Unit: state machine stuck, found in a cold start test). Both block test sets that are required for Design Validation Complete (MS-D, 2026-10-16). Owners are Zoe Wilson and Anna Fischer.

## Applicability matrix

| Rule | Components | Leading requirements |
|---|---|---|
| ISO21434-9.3.1 | Head Unit | REQ-INF-0011, REQ-INF-0120 |
| ISO21434-10.4.1 | Telematics Control Unit, LTE Modem | REQ-INF-0001 |
| ISO21434-10.4.4 | Head Unit | REQ-INF-0011 |
| ISO21434-11.4.2 | Head Unit, Telematics Control Unit | REQ-INF-0011, REQ-INF-0016 |
| ISO21434-13.3.1 | All connected components | Defect process |
