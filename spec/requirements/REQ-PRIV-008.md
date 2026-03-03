# REQ-PRIV-008: Revalidate prior-season saved check-in info before reuse
**Status:** Proposed
**Priority:** P1
**Owner:** Privacy And UX
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** REQ-PRIV-007
**Validated By:** TBD

## Description
At the start of a new OHNY season, if saved check-in information from a prior season still exists, the system should ask whether that information is still valid before reusing it.

## Rationale
Gate 1 treats season boundaries as a reasonable trigger for reuse revalidation.

## Acceptance Criteria
- Given a new OHNY season begins and prior-season saved check-in data exists, when a user starts a check-in flow, then the system asks whether the saved info is still valid before reuse.
- Given the user confirms the prior-season data is still valid, when check-in continues, then eligible saved data may be reused.
- Given the user says the prior-season data is no longer valid, when the flow continues, then the system does not reuse stale fields without fresh confirmation or replacement.

## Non-Goals
- Deleting prior-season data automatically without asking.
- Revalidating data on every check-in within the same season solely for seasonal reasons.

## Notes
- This is a `should` requirement from Gate 1 and is therefore P1.
