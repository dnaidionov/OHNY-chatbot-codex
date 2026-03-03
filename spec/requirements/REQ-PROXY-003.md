# REQ-PROXY-003: Apply baseline rate limiting with a retry path
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Proxy
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-PROXY-001
**Validated By:** TBD

## Description
The proxy must apply baseline rate limiting as the default burst-protection control, and when the limit is triggered, the user must receive a clear temporary-limit response with a retry path instead of being forced through login or CAPTCHA by default.

## Rationale
Gate 1 requires burst protection without silent failure or fake success.

## Acceptance Criteria
- Given request volume crosses the configured limit, when the proxy handles a check-in request, then it returns a temporary-limit response instead of forwarding blindly.
- Given rate limiting is triggered, when the user is informed, then the message clearly indicates the limit is temporary.
- Given a temporary-limit response is shown, when the user reads it, then a short retry path is provided.
- Given baseline abuse controls are active, when a typical over-limit case occurs, then the default response path does not introduce login or CAPTCHA requirements.

## Non-Goals
- Using CAPTCHA or login as the default abuse control.
- Silently dropping over-limit requests.

## Notes
- Exact rate thresholds are operationally defined later.
