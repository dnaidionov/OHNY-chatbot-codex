# REQ-CHECKIN-001: Support retrieval-driven named-site check-in
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Flow
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-RETR-001, REQ-RETR-002, REQ-RETR-003
**Validated By:** TBD

## Description
The system must support a named-site check-in flow initiated by `check me in at <site>` and resolve the site through retrieval before submission.

## Rationale
Named-site check-in is one of the two primary Gate 1 check-in entry points.

## Acceptance Criteria
- Given a user says `check me in at <site>`, when the flow starts, then the system enters named-site check-in handling.
- Given a named-site check-in, when site resolution occurs, then retrieval is used before any submission step.
- Given site resolution is not yet confident or confirmed, when the flow is still active, then submission does not proceed.

## Non-Goals
- Skipping site resolution for named-site check-in.
- Requiring device geolocation before a named-site flow can continue.

## Notes
- Ambiguity and no-match recovery are governed by retrieval requirements.
