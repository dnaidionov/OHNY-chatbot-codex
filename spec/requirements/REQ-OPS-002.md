# REQ-OPS-002: Collect aggregate planning, retrieval, privacy, and operational guardrail metrics
**Status:** Proposed
**Priority:** P1
**Owner:** Product Analytics
**Related Specs:** /spec/success-metrics.md, /spec/privacy-notice.md
**Depends On:** None
**Validated By:** TBD

## Description
The system should collect aggregate-only metrics covering planning usefulness, retrieval recovery, check-in guardrails, privacy actions, and operational health without depending on server-side personal profiles or raw chat-linked PII.

## Rationale
Gate 1 defines a broad metric set but also constrains analytics privacy posture.

## Acceptance Criteria
- Given planning activity is measured, when analytics are reviewed, then planning success, time to first recommendation, clarification burden, and feasible-plan rate are available in aggregate.
- Given retrieval and check-in recovery behaviors are measured, when analytics are reviewed, then site-resolution, ambiguity recovery, no-match recovery, geo-to-site confirmation, first-attempt versus retry success, upstream failure rate, and saved-profile reuse are available in aggregate.
- Given privacy and operations are measured, when analytics are reviewed, then local-save opt-in, forget-my-info completion, planning reset usage, geolocation grant or denial behavior, latency, rate-limit triggers, cache hit rate, burst survival, and observed upstream availability are available in aggregate.
- Given analytics data is retained, when privacy posture is reviewed, then it does not depend on server-side personal profiles or raw chat-linked PII for those measurements.

## Non-Goals
- Tracking individualized behavior histories for personalization.
- Defining every downstream reporting workflow.

## Notes
- This requirement covers instrumentation scope, not evaluation thresholds.
