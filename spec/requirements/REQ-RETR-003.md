# REQ-RETR-003: Recover from no confident site match with bounded candidates
**Status:** Proposed
**Priority:** P0
**Owner:** Retrieval Service
**Related Specs:** /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** REQ-RETR-001
**Validated By:** TBD

## Description
If retrieval cannot produce a confident site match, the system must say so, show a bounded list of likely or nearby candidates, and ask for another hint.

## Rationale
Gate 1 requires graceful recovery from partial user input without silently inventing a match.

## Acceptance Criteria
- Given no confident site match, when the system responds, then it explicitly states that the site could not be identified confidently.
- Given no confident site match, when fallback candidates are shown, then the list contains no more than 5 candidates.
- Given fallback candidates have been shown, when the flow continues, then the user is prompted for another hint such as a landmark, neighborhood, or address fragment.

## Non-Goals
- Declaring success without a confident or confirmed match.
- Returning more than 5 fallback candidates.

## Notes
- This applies to both named-site and geolocation fallback flows.
