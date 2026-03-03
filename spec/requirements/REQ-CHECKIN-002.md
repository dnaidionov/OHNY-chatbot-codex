# REQ-CHECKIN-002: Support unnamed geolocation-first check-in
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Flow
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-RETR-004, REQ-PRIV-008
**Validated By:** TBD

## Description
The system must support an unnamed `check me in` flow that uses geolocation first when available, requires confirmation of the matched site, and falls back to retrieval-driven hints when geolocation is denied, unavailable, or too imprecise.

## Rationale
Unnamed check-in is the second primary Gate 1 entry point and must still work without location permission.

## Acceptance Criteria
- Given a user says `check me in` and usable geolocation is available, when the flow proceeds, then the system proposes a nearby matched site and asks for confirmation.
- Given geolocation is denied, unavailable, or too imprecise, when unnamed check-in continues, then the user is asked for a site name, landmark, neighborhood, or address fragment instead.
- Given geolocation suggests one site but the user indicates another, when the conflict is detected, then the system asks which site is correct before continuing.

## Non-Goals
- Requiring location permission as a prerequisite for check-in.
- Auto-submitting a site match without user confirmation.

## Notes
- This requirement covers entry and fallback behavior, not submission semantics.
