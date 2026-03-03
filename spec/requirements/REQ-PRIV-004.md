# REQ-PRIV-004: Prohibit server-side personal profiles in v1
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/privacy-notice.md, /spec/success-metrics.md
**Depends On:** None
**Validated By:** TBD

## Description
v1 must not create a server-side personal profile for preferences, saved check-in data, or personalization.

## Rationale
This is a hard Gate 1 privacy and architecture boundary.

## Acceptance Criteria
- Given a v1 personalization or check-in reuse feature, when its storage location is defined, then it does not require a server-side personal profile.
- Given a returning user reuses saved information, when that information is loaded, then it originates from the current device rather than a server profile.
- Given a v1 architecture review, when persistence dependencies are examined, then no server-side personal profile store is present for this purpose.

## Non-Goals
- Preventing all server communication.
- Defining v2 profile behavior.

## Notes
- Thin proxy submission remains allowed.
