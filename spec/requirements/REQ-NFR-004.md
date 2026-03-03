# REQ-NFR-004: Preserve product behavior across serverless and single-container deployment
**Status:** Proposed
**Priority:** P0
**Owner:** Platform Architecture
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** None
**Validated By:** TBD

## Description
The product must support deployment as serverless functions or as a single container without changing product behavior, and the request path must not depend on long-lived stateful services or a persistent database for v1 user profiles.

## Rationale
Gate 1 locks in deployment portability and stateless request-path assumptions.

## Acceptance Criteria
- Given a serverless deployment, when the product is exercised, then Gate 1 behavior matches the defined contract.
- Given a single-container deployment, when the product is exercised, then Gate 1 behavior matches the defined contract.
- Given the request path is reviewed, when dependencies are enumerated, then it does not require long-lived in-memory session state or a persistent v1 user-profile database to function.

## Non-Goals
- Choosing the final hosting vendor.
- Prohibiting all caching or ephemeral state.

## Notes
- This requirement is about behavior portability, not build tooling.
