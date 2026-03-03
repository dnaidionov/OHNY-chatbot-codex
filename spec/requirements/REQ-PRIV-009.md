# REQ-PRIV-009: Govern geolocation prompting and denial memory
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md, /spec/privacy-notice.md
**Depends On:** None
**Validated By:** TBD

## Description
The product must ask for geolocation on first page load with a brief benefit explanation, continue working when denied, explain the value of later re-asks, suppress a third ask after two same-day denials, and allow a new ask on a later day or season reset.

## Rationale
Gate 1 treats geolocation as optional but useful, with bounded prompting to avoid harassment.

## Acceptance Criteria
- Given first page load, when the geolocation prompt appears, then it briefly explains the benefit for `near me` recommendations or unnamed check-in.
- Given geolocation is denied, when the user continues using planning or check-in, then the product still works through non-location fallbacks.
- Given geolocation has been denied twice on the same day, when another same-day ask would otherwise occur, then the product does not ask again that day.
- Given geolocation is requested again after an earlier denial on a later task, when the re-ask is shown, then it explains why location would materially help the current task.
- Given a later day or new OHNY season begins, when geolocation prompting is evaluated, then the product may ask again.

## Non-Goals
- Requiring geolocation for core product use.
- Re-asking repeatedly without explanation.

## Notes
- Accuracy thresholds for "too imprecise" are intentionally left open in Gate 1.
