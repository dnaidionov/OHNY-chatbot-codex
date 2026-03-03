# REQ-NFR-005: Prefer graceful availability during OHNY weekend
**Status:** Proposed
**Priority:** P1
**Owner:** Platform Operations
**Related Specs:** /spec/system-contract.md
**Depends On:** REQ-NFR-002, REQ-PROXY-003
**Validated By:** TBD

## Description
During OHNY weekend, the system should favor graceful degradation over hard failure whenever core flows can still proceed safely.

## Rationale
The event window concentrates demand, making resilient partial service preferable to collapse.

## Acceptance Criteria
- Given OHNY weekend peak load, when all optional behavior cannot be sustained, then the system degrades optional behavior before failing core flows.
- Given a component issue affects non-critical enrichment only, when safe operation is still possible, then planning or check-in can continue in degraded form.
- Given a failure would make a core flow unsafe or misleading, when degradation is no longer sufficient, then the system fails clearly rather than pretending success.

## Non-Goals
- Guaranteeing zero failures during event weekend.
- Continuing unsafe or misleading check-in behavior just to stay online.

## Notes
- This is a resilience preference, not an absolute uptime guarantee.
