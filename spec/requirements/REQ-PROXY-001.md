# REQ-PROXY-001: Forward validated check-ins through a thin backend proxy
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Proxy
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-CHECKIN-005
**Validated By:** TBD

## Description
The backend must act as a thin proxy that validates required submission fields and forwards confirmed check-in requests to the existing OHNY API.

## Rationale
Gate 1 includes self check-in through the existing OHNY API without introducing a new thick backend workflow.

## Acceptance Criteria
- Given a check-in request reaches the proxy, when validation runs, then required submission fields are verified before forwarding.
- Given proxy validation succeeds, when the request is forwarded, then it is sent to the existing OHNY API rather than handled as a local completion.
- Given v1 proxy behavior is reviewed, when server responsibilities are examined, then no server-side personal profile storage is required for submission.

## Non-Goals
- Replacing the existing OHNY check-in API.
- Defining the upstream auth or endpoint contract in Gate 1.

## Notes
- Upstream protocol specifics remain out of scope for this requirement.
