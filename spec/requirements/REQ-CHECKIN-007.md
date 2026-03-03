# REQ-CHECKIN-007: Handle off-weekend check-in attempts explicitly
**Status:** Proposed
**Priority:** P1
**Owner:** Check-In Flow
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** REQ-PROXY-004
**Validated By:** TBD

## Description
If a user attempts check-in outside OHNY weekend, the system should warn before final confirmation, still allow a confirmed submission attempt, and explain event-window unavailability if the submission fails.

## Rationale
Gate 1 requires honest behavior around likely upstream downtime outside the active event window.

## Acceptance Criteria
- Given a check-in attempt occurs outside OHNY weekend, when the user reaches final confirmation, then the system warns that submission may fail.
- Given the user confirms an off-weekend attempt, when submission is requested, then the system still attempts the check-in.
- Given an off-weekend submission fails, when the user is notified, then the failure message explains that the upstream check-in service may be unavailable because the event window is inactive.

## Non-Goals
- Blocking all off-weekend attempts automatically.
- Reporting off-weekend submission failure as success.

## Notes
- This is a conditional behavior tied to event-window context.
