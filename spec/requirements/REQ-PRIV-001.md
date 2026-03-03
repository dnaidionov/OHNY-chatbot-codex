# REQ-PRIV-001: Require explicit device-only save consent
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** None
**Validated By:** TBD

## Description
The system must ask for explicit opt-in before saving check-in information on the device, and the prompt must clearly state that the data is stored on this device only rather than in a server-side profile.

## Rationale
Gate 1 keeps personalization local and requires informed consent for device persistence.

## Acceptance Criteria
- Given the system wants to save check-in information locally, when it prompts the user, then the prompt requires explicit opt-in.
- Given the save prompt is shown, when the user reads it, then it states that the data is stored on this device only.
- Given the initial save prompt is shown, when the user reviews it, then it mentions the ability to later use `forget my info`.

## Non-Goals
- Implied consent from mere product usage.
- Presenting local save as a server-backed account feature.

## Notes
- Consent durability is covered separately.
