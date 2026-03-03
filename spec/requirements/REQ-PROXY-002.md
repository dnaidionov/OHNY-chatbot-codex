# REQ-PROXY-002: Enforce idempotent check-in submission
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Proxy
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-PROXY-001
**Validated By:** TBD

## Description
The proxy must apply idempotency safeguards so the same user action is not recorded multiple times accidentally.

## Rationale
Duplicate submissions are a core failure mode for check-in systems under bursty or retry-heavy conditions.

## Acceptance Criteria
- Given the same check-in action is retried without material change, when the proxy handles it, then duplicate upstream records are prevented.
- Given a user retries after an ambiguous client-side timeout, when idempotency safeguards are applied, then the proxy does not create duplicate check-ins for the same action.
- Given idempotency handling occurs, when the proxy responds, then the user-facing outcome remains consistent with the single intended submission.

## Non-Goals
- Guaranteeing idempotency across unrelated check-in attempts.
- Exposing internal idempotency token design in the spec.

## Notes
- Implementation details can vary as long as duplicate accidental submission is prevented.
