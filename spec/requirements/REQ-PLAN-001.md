# REQ-PLAN-001: Generate walking-only recommendation sets
**Status:** Proposed
**Priority:** P0
**Owner:** Planner Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** REQ-RETR-001, REQ-TRAVEL-002
**Validated By:** TBD

## Description
The planner must generate recommendation sets using OHNY retrieval results, user constraints, and walking-only travel assumptions in v1.

## Rationale
Gate 1 defines conversational planning as an in-scope v1 capability and locks travel to walking only.

## Acceptance Criteria
- Given a planning request with at least one resolved candidate site, when the planner responds, then the response contains at least one recommendation set derived from retrieval data.
- Given a planning request with user constraints such as time or interests, when recommendations are generated, then those constraints are incorporated into the recommendation set.
- Given v1 planning execution, when the planner requests travel evaluation, then it uses walking mode only.

## Non-Goals
- Calculating non-walking itineraries.
- Returning street-by-street navigation.

## Notes
- Recommendation wording remains a separate orchestration concern.
