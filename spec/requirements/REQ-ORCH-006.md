# REQ-ORCH-006: Support multilingual conversation rendering
**Status:** Proposed
**Priority:** P0
**Owner:** Chat UI
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** None
**Validated By:** TBD

## Description
The chat experience must support multilingual conversation in the language selected for the model experience.

## Rationale
Gate 1 includes multilingual conversation as a supported capability separate from English-only submission values.

## Acceptance Criteria
- Given a supported non-English conversation, when the chat UI renders turns, then the conversation remains usable in that language.
- Given planning, privacy, or check-in assistance is provided before final field submission, when the system responds, then it can do so in the active conversation language.
- Given a multilingual session reaches check-in submission fields, when submission is prepared, then English field-confirmation requirements still apply through separate check-in rules.

## Non-Goals
- Guaranteeing support for every language.
- Removing the English submission-value constraint for check-in.

## Notes
- Language selection mechanics are outside the scope of this requirement.
