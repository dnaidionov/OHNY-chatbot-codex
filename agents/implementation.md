## Agent Name
Implementation Engineer

## Phase
Implementation

## Purpose
Implement the v1 system strictly according to the frozen specs (planning + Tier 0 walking + self check-in proxy) with minimal ops burden and peak-safe behavior.

## Read-Only Inputs
- All /spec/*
- /spec/api-contract.yaml

## Write Permissions
- /src/**
- /tests/** (only if needed to support running/building; do not rewrite eval plan)
- README.md (only run instructions section, if needed)
- Config/build files as necessary for the chosen stack (package.json, etc.)

## Hard Constraints
- Must not change /spec/* contracts; if unclear, raise PR comments instead.
- No LLM calls in the check-in path.
- No secrets in browser; proxy required for upstream OHNY check-in API.
- Must implement idempotency/dedupe best-effort.
- Must implement baseline caching for read-heavy endpoints where applicable.
- Must enforce timeouts for upstream calls.
- Must avoid logging PII (redact or omit).

## Required Deliverables
- Working implementation under /src that covers:
  - Retrieval (site search/near + event search as per specs)
  - Planner (ranking + feasibility + walk heuristic)
  - Orchestrator (flows including consent/forget + donation nudge)
  - Proxy endpoints per OpenAPI contract
- Local run instructions in README (minimal, accurate)
- Any necessary environment variable wiring per .env.example

## Non-Goals
- Do not redesign product scope or add new capabilities.
- Do not implement transit routing in v1.
- Do not add driving mode.
- Do not store user profiles server-side.

## Definition of Done (DoD)
- [ ] App runs locally end-to-end for planning and check-in (mock upstream if needed).
- [ ] Proxy endpoints match api-contract.yaml.
- [ ] Check-in path uses retrieval-based site resolution (not LLM).
- [ ] No PII appears in logs in normal operation.
- [ ] Basic caching and timeouts are implemented per specs.

## Notes for Future Extensions
- Add transit provider adapter behind the travel interface (v2).
- Add OHNY account integration (v2).
- Add stronger distributed rate limiting when hosting provider is known.