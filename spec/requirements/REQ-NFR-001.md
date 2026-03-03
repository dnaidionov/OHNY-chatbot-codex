# REQ-NFR-001: Keep normal interactions to a few seconds for the large majority of turns
**Status:** Proposed
**Priority:** P1
**Owner:** Platform Performance
**Related Specs:** /spec/system-contract.md, /spec/success-metrics.md
**Depends On:** None
**Validated By:** TBD

## Description
During normal operation, the system should target response times of a few seconds for the large majority of planning and check-in turns, with fast interaction favored over verbose output.

## Rationale
Gate 1 prioritizes low-friction user experience and operational practicality.

## Acceptance Criteria
- Given normal operating conditions, when planning turns are measured, then the large majority complete within a few seconds.
- Given normal operating conditions, when check-in turns are measured, then the large majority complete within a few seconds.
- Given a design tradeoff between extra verbosity and faster response, when normal-turn output is chosen, then the system favors the faster usable response.

## Non-Goals
- Guaranteeing identical latency for every request.
- Preferring longer explanations over responsiveness.

## Notes
- Precise SLO values can be added later without changing the core target.
