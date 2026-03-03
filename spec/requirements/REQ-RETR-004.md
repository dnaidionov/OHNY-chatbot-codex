# REQ-RETR-004: Provide nearby candidates for location-based flows
**Status:** Proposed
**Priority:** P1
**Owner:** Retrieval Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-RETR-001
**Validated By:** TBD

## Description
The retrieval layer must support nearby-candidate generation from location context so unnamed check-in and `near me` planning can propose site options.

## Rationale
Gate 1 includes geolocation-assisted discovery and unnamed check-in.

## Acceptance Criteria
- Given usable location context, when retrieval is asked for nearby sites, then it returns candidates suitable for user confirmation.
- Given an unnamed check-in flow with location access, when nearby candidates are evaluated, then the flow can propose a matched nearby site.
- Given `near me` planning without a directly named site, when location context is available, then nearby retrieval can seed planning recommendations.

## Non-Goals
- Continuous live tracking.
- Precise turn-by-turn routing.

## Notes
- Location context may come from device geolocation or user-provided location hints.
