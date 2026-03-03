# REQ-PLAN-003: Rank planning results by interest fit with visible time tradeoffs
**Status:** Proposed
**Priority:** P1
**Owner:** Planner Service
**Related Specs:** /spec/product-architecture.md, /spec/success-metrics.md
**Depends On:** REQ-PLAN-002
**Validated By:** TBD

## Description
The planner must prioritize interest fit in ranking while still making time-window tradeoffs visible to the user.

## Rationale
Gate 1 favors compelling recommendations over rigid filtering, but not at the cost of misleading the user.

## Acceptance Criteria
- Given multiple candidate recommendations, when the planner ranks them, then interest fit may outrank strict time-window fit.
- Given a top-ranked recommendation that may exceed the user's time window, when it is shown, then the over-window risk is visible in the response.
- Given a clearly infeasible option, when the planner assembles default workable steps, then that option is not presented as the default itinerary.

## Non-Goals
- Enforcing strict shortest-time ranking.
- Personalizing ranking from a server-side profile.

## Notes
- This requirement covers ranking policy, not conversation phrasing.
