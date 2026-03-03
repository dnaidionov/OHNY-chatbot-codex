# REQ-CHECKIN-005: Require explicit final confirmation before submission
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Flow
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-CHECKIN-003
**Validated By:** TBD

## Description
Every check-in must end with an explicit final confirmation step that shows the resolved site and the required submitted fields before the proxy submits.

## Rationale
Gate 1 requires a deterministic handoff to the proxy and a visible confirmation point for the user.

## Acceptance Criteria
- Given any check-in flow is ready to submit, when the final confirmation is shown, then the resolved site is displayed.
- Given final confirmation is shown, when the user reviews it, then all required submitted fields are visible.
- Given the user has not explicitly confirmed the final confirmation step, when the system is ready to submit, then submission does not proceed.

## Non-Goals
- Background auto-submission.
- Hiding required submission data from the user before submit.

## Notes
- Saved-info notice requirements are defined separately.
