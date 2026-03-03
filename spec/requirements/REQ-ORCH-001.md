# REQ-ORCH-001: Classify requests into supported flow types
**Status:** Proposed
**Priority:** P0
**Owner:** Conversation Orchestrator
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** None
**Validated By:** TBD

## Description
The conversation orchestrator must classify user requests into planning, retrieval, check-in, settings/privacy, or unsupported flows.

## Rationale
Gate 1 depends on deterministic routing across distinct product capabilities.

## Acceptance Criteria
- Given a new user turn, when the orchestrator processes it, then it assigns the turn to one supported flow type or marks it unsupported.
- Given a privacy or settings request, when it is classified, then it is not routed into planning or check-in handling by default.
- Given an unsupported request, when classification completes, then unsupported handling is invoked explicitly.

## Non-Goals
- Defining model internals for intent classification.
- Supporting arbitrary new capabilities beyond Gate 1.

## Notes
- Classification accuracy is evaluated separately from specific downstream behaviors.
