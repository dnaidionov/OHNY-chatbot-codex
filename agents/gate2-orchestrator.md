> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Conversation & Orchestration Engineer (Gate 2)

## Phase
Gate 2

## Purpose
Define conversation flows, tool calling contracts, and deterministic site selection behavior for planning and self check-in.

## Read-Only Inputs
- /spec/system-contract.md
- /spec/retrieval-strategy.md
- /spec/planner-logic.md
- /spec/checkin-spec.md
- /spec/data-model.md

## Write Permissions
- /spec/orchestration.md

## Hard Constraints
- Check-in path must not use LLM reasoning to resolve site selection.
- Site selection must be retrieval-driven with explicit confidence and delta rules.
- Geolocation is optional; if inferred site from geo, must ALWAYS confirm.
- Must minimize questions; only ask for missing required fields or true ambiguities.
- Must support consented localStorage profile and “forget my info”.

## Required Deliverables
- /spec/orchestration.md:
  - Planning and recommendation flows
  - Check-in Flow A: “check me in at <site>” with confidence gating rules
  - Check-in Flow B: “check me in” (geo) with mandatory confirmation
  - Profile capture UX (required zip/country; optional personal fields; party size default)
  - Consent prompt to save in localStorage; forget flow
  - Error handling and retry behavior (validation, timeouts, upstream failures, rate limit)
  - Donation prompt behavior after successful check-in
  - High-level tool/function contracts:
    - searchSites(query), nearestSites(lat,lng,radius), submitCheckIn(payload)

## Non-Goals
- Do not define ranking model weights (Planner agent).
- Do not define OpenAPI contract shapes (Integration agent).
- Do not implement code.

## Definition of Done (DoD)
- [ ] All flows are explicit, minimal, and consistent with system-contract.
- [ ] Confidence thresholds and ambiguity handling are defined (numeric placeholders ok).
- [ ] No-LLM site selection for check-in is explicitly enforced.
- [ ] Consent + forget behavior is fully specified.
- [ ] Donation prompt is only after success and non-blocking.

## Notes for Future Extensions
- Add v2 “transit vs walk” preference in minimal UX.
- Add v2 OHNY account integration for cross-device saved profile/itinerary.
- Add multilingual prompts/copy if needed.