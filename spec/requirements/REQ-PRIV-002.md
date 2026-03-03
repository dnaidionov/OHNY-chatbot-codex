# REQ-PRIV-002: Keep local save consent in effect until revoked or materially changed
**Status:** Proposed
**Priority:** P1
**Owner:** Privacy And UX
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** REQ-PRIV-001
**Validated By:** TBD

## Description
Once granted, device-local save consent should remain in effect until the user revokes it or the saved-data terms materially change.

## Rationale
Gate 1 calls for one-time device consent rather than repeated prompts on every reuse.

## Acceptance Criteria
- Given a user has granted device-local save consent, when a later check-in reuses eligible saved data, then the system does not require a fresh save-consent prompt solely because time has passed.
- Given the user revokes consent, when future save opportunities arise, then the system asks again before saving.
- Given the product materially changes what local data will be stored, when the new scope first applies, then the system requests renewed consent.

## Non-Goals
- Locking consent forever after a single approval.
- Treating unrelated UI wording tweaks as a material consent change.

## Notes
- Reuse confirmation remains a separate user-facing requirement.
