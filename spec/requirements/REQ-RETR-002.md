# REQ-RETR-002: Require explicit disambiguation for ambiguous site matches
**Status:** Proposed
**Priority:** P0
**Owner:** Retrieval Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-RETR-001
**Validated By:** TBD

## Description
When retrieval finds multiple plausible site matches, the system must present a short disambiguation list and require user selection instead of guessing.

## Rationale
Wrong site resolution breaks both trust and check-in correctness.

## Acceptance Criteria
- Given a query with multiple plausible matches, when retrieval returns candidates, then the user sees a short choice list rather than an auto-selected site.
- Given an ambiguous match, when the user has not yet selected a candidate, then the system does not submit or confirm a specific site as resolved.
- Given a user selection from the disambiguation list, when the flow resumes, then the selected site becomes the resolved site.

## Non-Goals
- Auto-selecting the top-ranked ambiguous match.
- Showing an unbounded candidate list.

## Notes
- Short-list size is intentionally left flexible except where other specs cap fallback candidates.
