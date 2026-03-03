# REQ-PRIV-005: Support forgetting local check-in and profile data
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** None
**Validated By:** TBD

## Description
The product must let users clear locally stored check-in and profile data on the device through both a settings/options control and the `forget my info` chat command.

## Rationale
Gate 1 requires revocable local persistence.

## Acceptance Criteria
- Given a user invokes `forget my info`, when the action completes, then locally stored check-in and profile data on that device is removed.
- Given the user prefers UI controls, when they open settings or options, then a local deletion control is available there.
- Given local check-in/profile data has been deleted, when a later check-in occurs, then previously deleted saved data is no longer reused automatically.

## Non-Goals
- Deleting server-side analytics aggregates.
- Combining this control with planning-preference reset.

## Notes
- This requirement covers deletion of saved check-in/profile data only.
