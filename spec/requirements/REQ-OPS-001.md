# REQ-OPS-001: Track the primary check-in completion metric with required segments
**Status:** Proposed
**Priority:** P1
**Owner:** Product Analytics
**Related Specs:** /spec/success-metrics.md
**Depends On:** None
**Validated By:** TBD

## Description
The system should track check-in completion rate as the v1 north-star metric for users who start a check-in flow, segmented by named-site versus unnamed flow, geo-available versus geo-denied, saved-info reuse versus manual entry, and in-event-window versus outside-event-window attempts.

## Rationale
Gate 1 defines a specific product success metric and segment breakdown for evaluating the check-in experience.

## Acceptance Criteria
- Given a user starts a check-in flow, when analytics are recorded, then the attempt contributes to check-in completion-rate measurement.
- Given check-in completion analytics are reported, when segments are available, then named-site versus unnamed flow is distinguishable.
- Given check-in completion analytics are reported, when segments are available, then geo availability, saved-info reuse, and event-window context are distinguishable.

## Non-Goals
- Storing user-identifying server-side profiles to support analytics.
- Defining dashboard tooling in Gate 1.

## Notes
- Segmentation must still respect aggregate-only privacy constraints.
