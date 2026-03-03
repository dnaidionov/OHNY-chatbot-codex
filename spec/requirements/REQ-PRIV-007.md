# REQ-PRIV-007: Confirm reuse of saved local check-in info
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-PRIV-001
**Validated By:** TBD

## Description
When saved check-in information exists on the device, the system must confirm that it is about to use that information and offer the user a path to switch or forget it.

## Rationale
Gate 1 requires explicit user awareness before reusing saved local check-in data.

## Acceptance Criteria
- Given saved local check-in information exists, when a check-in flow is about to reuse it, then the system states that saved info will be used.
- Given saved info reuse is proposed, when the user is shown the reuse notice, then options to switch or forget the saved info are available.
- Given the user declines reuse, when the flow continues, then the system falls back to collecting or updating the necessary fields.

## Non-Goals
- Reusing saved data silently.
- Forcing the user to delete saved data in order to edit one field.

## Notes
- Seasonal validity is handled separately.
