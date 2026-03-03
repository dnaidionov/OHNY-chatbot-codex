# REQ-CHECKIN-003: Collect only missing required submission fields
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Flow
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** None
**Validated By:** TBD

## Description
Check-in must collect required submission fields incrementally and ask only for items that are still missing.

## Rationale
Gate 1 emphasizes low-friction check-in and minimal clarification burden.

## Acceptance Criteria
- Given some required submission fields are already available from the current conversation or consented device data, when check-in proceeds, then those fields are not re-requested unnecessarily.
- Given a required field is missing, when the flow reaches that need, then the system asks specifically for that missing field.
- Given a missing field is provided, when the flow resumes, then the next prompt targets the next unresolved requirement rather than restarting collection.

## Non-Goals
- Collecting optional information before required fields are complete.
- Asking the user to re-enter data already available and still valid.

## Notes
- Upstream field schema details can evolve without changing this behavioral requirement.
