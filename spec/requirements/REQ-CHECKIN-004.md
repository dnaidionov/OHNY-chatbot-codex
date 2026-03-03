# REQ-CHECKIN-004: Reconfirm party size on the first check-in of each day after day one
**Status:** Proposed
**Priority:** P1
**Owner:** Check-In Flow
**Related Specs:** /spec/system-contract.md, /spec/success-metrics.md, /spec/checkin-spec.md
**Depends On:** REQ-CHECKIN-003, REQ-PRIV-001
**Validated By:** TBD

## Description
When saved check-in data exists, the system should re-confirm party size on the first check-in of each day after day one before submission.

## Rationale
Party size is explicitly called out as a day-varying field that should not be reused blindly.

## Acceptance Criteria
- Given a returning user on the same day after an earlier check-in, when another check-in occurs, then party size does not need a special daily reconfirmation solely because data is saved.
- Given the first check-in of a new day after day one, when saved check-in data is reused, then the system asks the user to confirm or update party size before final submission.
- Given party size is updated during daily reconfirmation, when submission occurs, then the updated value is used.

## Non-Goals
- Reconfirming every saved field on every check-in.
- Inferring party size changes without user input.

## Notes
- This is a `should` requirement from Gate 1 and is therefore P1.
