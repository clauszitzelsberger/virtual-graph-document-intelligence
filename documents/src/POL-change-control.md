# Change Control Policy

<p class="meta">Document type: Policy · Document ID: POL-CCP · Version 3.0 · Published 2025-03-01 · Owner: Change Management (Zain Kim) · Applies to: Nova EV program</p>

## Purpose

This policy defines how change requests are raised, assessed, decided and implemented in the Nova EV program. It is the reference for every decision the Change Control Board takes. Each rule has an identifier of the form CCP-nn so that decisions and meeting minutes can cite the rule they are based on.

## Definitions

A change request is a proposal to alter a baselined requirement, component or design. It is recorded in the change management tool with an identifier of the form CR-nnnn, a title, a description, a status, a cost estimate and the list of requirements it affects. Status values are Proposed, Approved, Implemented and Rejected.

## Rules

### CCP-01 Every change request affects at least one requirement

A change request that does not name at least one affected requirement is not accepted for assessment. The affected requirements define the impact scope: their components, their test sets and the milestones those test sets are required for.

### CCP-02 Every change request has one responsible person

The responsible person prepares the impact assessment and presents the change to the Change Control Board. The responsible person is either a change manager or an engineer of the affected system.

### CCP-03 Cost threshold for program management approval

A change request with an estimated cost above 250,000 EUR requires the approval of Program Management in addition to the Change Control Board. Example: CR-0008 (Remove redundant sensor of Speaker Array, 479,618.97 EUR) needed the approval of Hannes Singh before it could move to Approved.

### CCP-04 Regulatory changes are approved by default

A change request whose sole purpose is compliance with a changed regulation or standard is approved unless the Change Control Board identifies a safety risk. The board documents the rule of the standard on which the approval rests. CR-0001 (Raise insulation resistance threshold across HVB components) was approved under this rule with reference to R100-6.1.1.

### CCP-05 Approved changes invalidate verification

When a change request is approved, all test sets that verify an affected requirement have to be re-executed after implementation. Until the retest is passed, the affected requirement counts as not verified for milestone gates. Retest planning is the responsibility of the affected system's engineering team together with the test teams.

### CCP-06 Implementation deadline

An approved change request shall be implemented before the next milestone whose required test sets verify an affected requirement. If this is not possible, the Change Control Board decides whether the milestone is moved or the change is deferred.

### CCP-07 Rejection criteria

A change request is rejected when the benefit does not justify the cost, when it introduces a safety risk without mitigation, or when the same intent was rejected within the last twelve months. Rejections name the criterion. Examples: CR-0005 (Update communication matrix of Electric Motor) and CR-0007 (Remove redundant sensor of Motor Control Unit) were rejected on the cost criterion.

### CCP-08 Proposed changes expire

A change request that stays in status Proposed for more than 90 days without assessment is presented to the Change Control Board with a recommendation to reject. CR-0004 (Add diagnostic function of Telematics Control Unit, proposed 2026-07-26) reaches this limit on 2026-10-24.

### CCP-09 Change Control Board cadence and quorum

The Change Control Board meets every four weeks. Quorum is one change manager, one program manager, one functional safety engineer and the responsible person of each change on the agenda. Decisions are recorded in meeting minutes with the rule they are based on.

### CCP-10 Changes across several components

A change request that affects requirements of more than one component shall name a coordinating engineer and shall list the responsible person of every affected requirement. CR-0001 affects the Battery Management System, the Cell Module and the HV Junction Box; Katrin Jansen coordinates.

## Roles

Change managers: Zain Kim, Gabriel Hoffmann, Jakob Wagner, Ulla Wang, Stefan Andersen. Program Management representatives: Hannes Singh, Gabriel Becker. Functional Safety representatives: Kenji Wagner, Felix Singh.
