# Email Thread: Escalation of DEF-1114 Gate Driver Board

<p class="meta">Document type: Email thread (exported) · Subject: Escalation DEF-1114 (DEP-02) · Participants: Fatima Kim, David Horvath, Katrin Larsen, Emre Hassan, Kenji Wagner · Period: 2026-09-02</p>

---

**From:** Fatima Kim (fatima.kim@nova-ev.example)
**To:** David Horvath, Katrin Larsen
**Cc:** Emre Hassan, Kenji Wagner
**Date:** 2026-09-02 08:20
**Subject:** Escalation DEF-1114 (DEP-02)

Hi David, hi Katrin,

I am escalating DEF-1114 (Gate Driver Board: wrong error code reported) under the Defect Escalation Policy, rule DEP-02. The defect has been Open since 2026-05-23, that is more than 100 days, and it is Critical.

Facts from the test side: I executed test case TC-03679 (Fault injection, test set TS-EDU-0152) on 2026-05-22. A provoked desaturation fault on the Gate Driver Board (CMP-EDU-06) was reported with the error code of a gate undervoltage fault. TS-EDU-0152 verifies REQ-EDU-0117 (Gate Driver Board: Engage the park lock) and REQ-EDU-0005 (Gate Driver Board: Control field weakening) and is required for Design Validation Complete (MS-D, 2026-10-16). Under DEP-03 this defect alone blocks the milestone.

Emre, I am copying you as program manager as the policy requires.

Fatima

---

**From:** David Horvath (david.horvath@nova-ev.example)
**To:** Fatima Kim, Katrin Larsen
**Cc:** Emre Hassan, Kenji Wagner
**Date:** 2026-09-02 10:05
**Subject:** RE: Escalation DEF-1114 (DEP-02)

Fatima,

Escalation acknowledged, and it is justified. Status from our side: the root cause is in the supplier firmware of the isolation driver IC, which maps the desaturation fault to the wrong code in its fault register. It is not in our firmware, which is why the fix took so long, we spent June proving that. The supplier has a corrected firmware and offers replacement samples.

Katrin, can you confirm the sample delivery date?

David

---

**From:** Katrin Larsen (katrin.larsen@nova-ev.example)
**To:** David Horvath, Fatima Kim
**Cc:** Emre Hassan, Kenji Wagner
**Date:** 2026-09-02 11:48
**Subject:** RE: Escalation DEF-1114 (DEP-02)

David, Fatima,

The supplier confirmed delivery of eight replacement Gate Driver Boards with the corrected firmware on 2026-09-24. Per best practice BP-GDB-05 a supplier firmware change is a change to the component and requires re-execution of all fault injection test cases, not just TC-03679. TS-EDU-0152 has three test cases, so the full test set is re-executed anyway.

Katrin

---

**From:** Kenji Wagner (kenji.wagner@nova-ev.example)
**To:** David Horvath, Katrin Larsen, Fatima Kim
**Cc:** Emre Hassan
**Date:** 2026-09-02 13:30
**Subject:** RE: Escalation DEF-1114 (DEP-02)

All,

From Functional Safety: a wrong error code on a desaturation fault is a violation of DG-BMS-06 in spirit and of ISO26262-6-9.4.3 in verification terms, and it must stay Critical. No downgrade to Major. The retest must include the coverage evidence for the fault reporting firmware per ISO26262-6-9.4.2.

Kenji

---

**From:** Emre Hassan (emre.hassan@nova-ev.example)
**To:** David Horvath, Katrin Larsen, Fatima Kim, Kenji Wagner
**Date:** 2026-09-02 15:10
**Subject:** RE: Escalation DEF-1114 (DEP-02)

Thank you all, this is clear.

**Decision: Replacement Gate Driver Board samples with corrected supplier firmware are ordered, and TS-EDU-0152 is fully re-executed on the HIL bench in the week of 2026-09-28, with Fatima Kim as test engineer and David Horvath as defect owner.** Rationale: the root cause is confirmed to be supplier firmware, a fix is available, and the defect blocks MS-D. Based on DEP-02, DEP-06 and BP-GDB-05. Status: Approved. Affects DEF-1114, REQ-EDU-0117, REQ-EDU-0005 and the Gate Driver Board.

I will put DEF-1114 on the agenda of the MS-D readiness review on 2026-09-15 as the first item.

Emre
