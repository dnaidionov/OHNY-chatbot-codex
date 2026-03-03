# REQ-PROXY-004: Propagate upstream failures without false success
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Proxy
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md, /spec/success-metrics.md
**Depends On:** REQ-PROXY-001
**Validated By:** TBD

## Description
The system must not report check-in success unless the upstream OHNY API confirms success, and upstream failures must be surfaced clearly with a retry path when safe.

## Rationale
Gate 1 treats truthful completion reporting as a quality guardrail and trust requirement.

## Acceptance Criteria
- Given the upstream OHNY API confirms success, when the response is returned, then the user may be told that check-in succeeded.
- Given the upstream OHNY API fails, times out, or is unavailable, when the user is notified, then the system clearly states that check-in was not completed.
- Given an upstream failure that may succeed on retry, when the failure is surfaced, then the user is offered a retry path.

## Non-Goals
- Masking upstream errors as completed check-ins.
- Guaranteeing upstream availability.

## Notes
- Off-weekend failure messaging is covered by a separate check-in requirement.
