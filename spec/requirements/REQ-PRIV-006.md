# REQ-PRIV-006: Keep planning-preference reset separate from profile deletion
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** None
**Validated By:** TBD

## Description
Resetting saved planning preferences must be a separate user control from deleting saved check-in or profile data.

## Rationale
Gate 1 explicitly separates planning personalization from check-in identity reuse.

## Acceptance Criteria
- Given the user wants to clear planning preferences only, when they use the relevant control, then saved check-in/profile data remains untouched.
- Given the user deletes saved check-in/profile data, when the action completes, then planning preferences are not implicitly reset by that action.
- Given settings or chat affordances are reviewed, when deletion options are presented, then the two actions are distinct.

## Non-Goals
- Forcing users to wipe all local personalization at once.
- Hiding one action behind the other.

## Notes
- This separation should remain visible in both chat and settings affordances.
