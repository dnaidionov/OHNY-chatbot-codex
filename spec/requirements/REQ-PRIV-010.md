# REQ-PRIV-010: Minimize location data sent to the server during check-in
**Status:** Proposed
**Priority:** P1
**Owner:** Privacy And UX
**Related Specs:** /spec/privacy-notice.md
**Depends On:** REQ-CHECKIN-002, REQ-PROXY-001
**Validated By:** TBD

## Description
When location access is used to identify a site for check-in, the system should send only the location-derived result or the minimum location-related information needed for that check-in flow.

## Rationale
Gate 1 allows geolocation-assisted check-in while constraining unnecessary location data transmission.

## Acceptance Criteria
- Given geolocation is used to identify a check-in site, when the submission-related request is prepared, then it omits extraneous location data not needed for that flow.
- Given a location-derived site has already been resolved, when the proxy payload is assembled, then the system may send the resolved result instead of raw location details when that is sufficient.
- Given a privacy review of location handling, when transmitted fields are inspected, then only the minimum location-related information needed for the check-in flow is included.

## Non-Goals
- Prohibiting all location-derived data from reaching the server.
- Defining the exact upstream field schema.

## Notes
- This is a `should` requirement from the privacy notice and is therefore P1.
