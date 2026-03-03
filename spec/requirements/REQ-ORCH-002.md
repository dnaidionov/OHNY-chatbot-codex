# REQ-ORCH-002: Ask only the minimum clarifying questions needed
**Status:** Proposed
**Priority:** P0
**Owner:** Conversation Orchestrator
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/success-metrics.md
**Depends On:** REQ-ORCH-001
**Validated By:** TBD

## Description
The orchestrator must ask only the minimum clarifying questions needed to continue the current planning or check-in flow, and once enough information is available it should respond with recommendation-first, concise output rather than extra preamble.

## Rationale
Low-friction interaction is a core Gate 1 product goal and cost guardrail.

## Acceptance Criteria
- Given a request that can proceed with existing context, when the orchestrator responds, then it does not ask an unnecessary clarification question.
- Given a request missing information required to continue safely, when the orchestrator responds, then it asks only for the missing information needed for the next step.
- Given a planning flow has enough information to answer, when the recommendation is returned, then the response leads with the recommendation content and keeps rationale brief by default.
- Given a `near me` planning request without usable geolocation, when the orchestrator needs a fallback, then it asks for a neighborhood, landmark, or address fragment rather than stopping.
- Given a planning flow under burst conditions, when optional refinements are not required, then the orchestrator may skip them in favor of a usable answer.

## Non-Goals
- Exhaustively collecting every possible user preference before responding.
- Asking follow-up questions solely to enrich narrative detail.
- Prefacing recommendation answers with unnecessary explanation.

## Notes
- Check-in field collection is further constrained by check-in-specific requirements.
