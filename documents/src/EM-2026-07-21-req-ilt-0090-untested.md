# Email Thread: REQ-ILT-0090 Has No Test Coverage

<p class="meta">Document type: Email thread (exported) · Subject: REQ-ILT-0090 has no test set · Participants: Anna Kim, Hannes Patel, Olivia Schulz, Felix Kim · Period: 2026-07-20 to 2026-07-21</p>

---

**From:** Anna Kim (anna.kim@nova-ev.example)
**To:** Hannes Patel
**Cc:** Olivia Schulz
**Date:** 2026-07-20 10:45
**Subject:** REQ-ILT-0090 has no test set

Hi Hannes,

The traceability report I ran for the Prototype Build Release review shows REQ-ILT-0090 (Touch Switch: Switch off after a timeout) without any test set. Under the Requirement Traceability Policy, rule RTP-01, every requirement needs at least one test set. You are listed as the owner.

Two other requirements are in the same situation, REQ-CHS-0107 in Chassis and REQ-INF-0164 in Infotainment, I am writing to their owners separately.

Can you tell me whether this is an oversight or whether the requirement is meant to be verified by another requirement's test set? If it is the latter, the test set should be linked to REQ-ILT-0090 as well, RTP-04 allows a test set to verify several requirements.

Best, Anna

---

**From:** Hannes Patel (hannes.patel@nova-ev.example)
**To:** Anna Kim
**Cc:** Olivia Schulz
**Date:** 2026-07-20 16:20
**Subject:** RE: REQ-ILT-0090 has no test set

Hi Anna,

It is an oversight. REQ-ILT-0090 was added late, when the Touch Switch (CMP-ILT-08) got its own timeout behaviour under design guideline rule DG-ILT-03. The Footwell Light has the same rule and REQ-ILT-0005 (Footwell Light: Switch off after a timeout) is fully tested, but the Touch Switch timeout uses the debounce logic from DG-ILT-07 and needs its own test.

The requirement is not required for Design Validation Complete (MS-D), the Touch Switch test sets are all assigned to Pre-Series Release (MS-E).

Hannes

---

**From:** Olivia Schulz (olivia.schulz@nova-ev.example)
**To:** Hannes Patel, Anna Kim
**Cc:** Felix Kim
**Date:** 2026-07-21 08:30
**Subject:** RE: REQ-ILT-0090 has no test set

Hannes, Anna,

Agreed that it needs its own test set. Proposal:

**Decision: A test set for REQ-ILT-0090 with at least two test cases, "Nominal operation" and "Boundary values" for the timeout limits, is created and assigned to Pre-Series Release (MS-E), executed by Vehicle Integration Test.** Rationale: RTP-01 requires a test set, RTP-06 requires at least two test cases, and MS-E is the first milestone where Touch Switch results are needed. Based on RTP-01 and DG-ILT-03. Status: Proposed, to be confirmed at the next readiness review. Affects REQ-ILT-0090 and the Touch Switch. Owner: Hannes Patel, test planning with Felix Kim.

Felix, can you check bench availability for the Touch Switch fixture in Q4?

Olivia

---

**From:** Felix Kim (felix.kim@nova-ev.example)
**To:** Olivia Schulz
**Cc:** Hannes Patel, Anna Kim
**Date:** 2026-07-21 11:15
**Subject:** RE: REQ-ILT-0090 has no test set

Olivia,

The Touch Switch fixture is free from November. I will hold two days in the week of 2026-11-16 for the new test set. Please create the test set in the tool and link it to REQ-ILT-0090 so that it shows up in the MS-E planning.

Felix

---

**From:** Anna Kim (anna.kim@nova-ev.example)
**To:** Olivia Schulz, Hannes Patel, Felix Kim
**Date:** 2026-07-21 13:02
**Subject:** RE: REQ-ILT-0090 has no test set

Thank you all. I will keep REQ-ILT-0090 on the RTP-01 report until the test set exists in the tool, and I will bring the decision to the MS-D readiness review on 2026-09-15 for confirmation.

Anna
