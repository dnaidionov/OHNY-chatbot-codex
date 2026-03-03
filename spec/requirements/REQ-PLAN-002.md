# REQ-PLAN-002: Label recommendation feasibility explicitly
**Status:** Proposed
**Priority:** P0
**Owner:** Planner Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/success-metrics.md
**Depends On:** REQ-TRAVEL-001
**Validated By:** TBD

## Description
Planner outputs must visibly label whether recommendations are feasible within stated walking assumptions, likely exceed the stated window, or are aspirational options that likely require non-walking travel.

## Rationale
Gate 1 requires users to distinguish workable plans from high-interest but less feasible options.

## Acceptance Criteria
- Given a recommendation set, when it is rendered for the user, then each recommendation is labeled with one of the allowed feasibility states.
- Given a recommendation that exceeds the user's stated time window but is still relevant, when it is returned, then it is not presented as fully feasible.
- Given an option that likely requires non-walking travel, when it is shown, then it is labeled aspirational rather than workable by default.

## Non-Goals
- Optimizing exact walking routes.
- Hiding less feasible options entirely.

## Notes
- Qualitative evaluation should verify label correctness.
