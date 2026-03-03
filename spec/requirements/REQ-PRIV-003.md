# REQ-PRIV-003: Limit local persistence to useful low-risk data
**Status:** Proposed
**Priority:** P0
**Owner:** Privacy And UX
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/privacy-notice.md
**Depends On:** REQ-PRIV-001
**Validated By:** TBD

## Description
After consent, local persistence may include repeat-use check-in fields, interests, accessibility preferences, and lightweight convenience settings, but must exclude highly sensitive free-form notes and data not useful for future check-ins or planning.

## Rationale
Gate 1 allows helpful local reuse while constraining privacy risk and scope creep.

## Acceptance Criteria
- Given local save consent has been granted, when eligible data is stored, then repeat-use check-in fields may be included.
- Given planning preferences such as interests or accessibility preferences are saved, when they are persisted, then they are stored locally rather than as a server-side profile.
- Given a highly sensitive free-form note or otherwise unnecessary field, when persistence is evaluated, then it is excluded from default local storage.

## Non-Goals
- Persisting arbitrary chat history by default.
- Expanding local storage to data with no future planning or check-in value.

## Notes
- Exact field lists can evolve within this scope constraint.
