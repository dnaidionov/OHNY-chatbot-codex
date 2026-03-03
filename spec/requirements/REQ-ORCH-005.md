# REQ-ORCH-005: Close final recommendations with a volunteer reminder
**Status:** Proposed
**Priority:** P2
**Owner:** Conversation Orchestrator
**Related Specs:** /spec/product-architecture.md
**Depends On:** REQ-PLAN-001
**Validated By:** TBD

## Description
Final recommendation responses should end with a brief reminder that users can also ask volunteers.

## Rationale
Gate 1 explicitly calls for a lightweight human-help fallback in planning responses.

## Acceptance Criteria
- Given a final recommendation response, when it is delivered to the user, then it ends with a brief volunteer reminder.
- Given an intermediate clarification turn, when the system is still gathering information, then the volunteer reminder is not required yet.
- Given a non-planning response, when the system responds, then this reminder is optional.

## Non-Goals
- Replacing recommendation content with volunteer instructions.
- Forcing the reminder into every single system utterance.

## Notes
- The reminder should remain brief to avoid response bloat.
