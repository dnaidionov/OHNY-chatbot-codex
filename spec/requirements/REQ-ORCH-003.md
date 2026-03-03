# REQ-ORCH-003: Render an onboarding greeting with example prompts
**Status:** Proposed
**Priority:** P1
**Owner:** Chat UI
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** None
**Validated By:** TBD

## Description
On initial load, the chat experience must show a short greeting, a brief product introduction, and 3 to 5 example prompts spanning planning and check-in, while aligning its visual language and interaction tone with `ohny.org` with room for chat-specific adaptations.

## Rationale
Gate 1 defines first-load guidance as part of the locked v1 experience.

## Acceptance Criteria
- Given a first page load, when the chat UI renders, then a short greeting is visible.
- Given the initial experience, when example prompts are shown, then there are at least 3 and no more than 5 prompts.
- Given the example prompt set, when reviewed, then it includes both planning-oriented and check-in-oriented examples.
- Given the chat UI is reviewed against product guidance, when its presentation is assessed, then its visual language and interaction tone are recognizably aligned with `ohny.org` while remaining chat-appropriate.

## Non-Goals
- Showing an exhaustive feature tour.
- Requiring the user to select an example prompt before continuing.
- Duplicating the entire `ohny.org` interface inside the chat.

## Notes
- Chat-specific UX adaptations remain allowed.
