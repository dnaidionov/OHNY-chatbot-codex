# REQ-TRAVEL-002: Restrict v1 travel evaluation to walking
**Status:** Proposed
**Priority:** P0
**Owner:** Planner Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** REQ-TRAVEL-001
**Validated By:** TBD

## Description
v1 must invoke the travel interface with walking only and must redirect users to an external maps application for non-walking directions or travel times.

## Rationale
Walking-only travel is a locked Gate 1 scope constraint.

## Acceptance Criteria
- Given any v1 planner travel evaluation, when the travel mode is set, then the mode is `walking`.
- Given a user asks for non-walking directions or travel time, when the system responds, then it states the walking-only limitation and points the user to an external maps app.
- Given a planning response includes travel framing, when options are described, then the guidance explicitly reflects walking-only assumptions.

## Non-Goals
- Generating transit, biking, or driving routes in v1.
- Embedding an external maps experience.

## Notes
- Future paid transit support should plug into the same contract without changing this v1 requirement.
