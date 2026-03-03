# REQ-CHECKIN-006: Confirm submission values in English
**Status:** Proposed
**Priority:** P0
**Owner:** Check-In Flow
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/checkin-spec.md
**Depends On:** None
**Validated By:** TBD

## Description
The product must support multilingual conversation, but check-in field values must be entered or confirmed in English before submission.

## Rationale
Gate 1 separates conversational language support from submission-language constraints.

## Acceptance Criteria
- Given a non-English conversation, when the user reaches check-in field confirmation, then the flow still requires the submitted field values to be in English.
- Given a check-in field value is not yet suitable for English submission, when the system is preparing to submit, then it asks for entry or confirmation in English.
- Given English field confirmation is complete, when final confirmation is shown, then submission may proceed.

## Non-Goals
- Restricting the entire chat experience to English only.
- Defining machine-translation implementation details.

## Notes
- This applies to submission values, not general conversational phrasing.
