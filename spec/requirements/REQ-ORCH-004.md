# REQ-ORCH-004: Redirect unsupported requests to the closest supported action
**Status:** Proposed
**Priority:** P0
**Owner:** Conversation Orchestrator
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** REQ-ORCH-001
**Validated By:** TBD

## Description
When a request is outside Gate 1 scope, the system must state the limitation explicitly and redirect the user to the closest supported action.

## Rationale
Gate 1 must stay explicit about its boundaries without ending the conversation abruptly.

## Acceptance Criteria
- Given an unsupported request, when the system responds, then it clearly states that the request is outside current support.
- Given an unsupported request adjacent to a supported capability, when the system responds, then it suggests a related supported action.
- Given a request for non-walking routing, when the redirect is produced, then it preserves walking-only guidance and external maps guidance.

## Non-Goals
- Pretending unsupported functionality exists.
- Ending the conversation without a recovery path.

## Notes
- Transit-routing redirects are a key example of this behavior.
