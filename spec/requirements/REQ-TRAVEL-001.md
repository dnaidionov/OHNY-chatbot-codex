# REQ-TRAVEL-001: Expose a mode-aware travel evaluation contract
**Status:** Proposed
**Priority:** P1
**Owner:** Travel Interface
**Related Specs:** /spec/product-architecture.md
**Depends On:** None
**Validated By:** TBD

## Description
The travel interface must accept origin context, destination site, travel mode, and optional feasibility constraints, and must return mode used, feasibility classification, estimated travel time, and a quality indicator.

## Rationale
Gate 1 fixes walking-only behavior for v1 but preserves a stable contract for future travel providers.

## Acceptance Criteria
- Given a planner travel request, when the interface is called, then the request shape includes origin context, destination, and travel mode.
- Given a successful travel evaluation, when the interface responds, then the response includes mode used, feasibility classification, travel time estimate, and a quality indicator.
- Given planner consumption of travel output, when recommendations are labeled, then the planner can use the returned feasibility semantics directly.

## Non-Goals
- Choosing a specific external provider in Gate 1.
- Defining fare calculations.

## Notes
- Provider integration remains a later-phase concern.
