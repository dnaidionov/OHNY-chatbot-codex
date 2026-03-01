> This task inherits and MUST follow `/agents/_preamble.md`.

# V2 – Transit Routing Agent

## Agent Name
Transit Routing Engineer (v2)

## Phase
V2 Extension (post-v1, after Gate 2 is frozen)

## Purpose
Add public transit travel-time and route summaries as a plug-in behind the existing `travel_time_minutes()` interface, without refactoring planner logic. Maintain provider-agnostic deployment and preserve v1 walking behavior.

## Read-Only Inputs
- /spec/planner-logic.md
- /spec/orchestration.md
- /spec/api-contract.yaml
- /spec/security-constraints.md
- /spec/cost-model.md
- /spec/deployment.md
- /spec/runbook.md
- /src/** (especially travel/planner/orchestrator/proxy modules)
- /tests/evals/**

## Write Permissions
- /spec/planner-logic.md (ONLY sections related to travel modes and interface; do not change ranking philosophy)
- /spec/orchestration.md (ONLY sections related to user choice of travel mode and copy; keep minimal)
- /spec/api-contract.yaml (ONLY if new proxy endpoints are needed for routing)
- /spec/cost-model.md (transit provider cost estimates)
- /spec/security-constraints.md (API key handling + privacy implications)
- /src/** (ONLY modules directly related to travel provider integration and mode selection)
- /tests/evals/** (add transit evals; do not remove existing tests)

## Hard Constraints
1) Backward compatibility:
   - v1 walking must behave exactly as before by default.
   - Existing planner feasibility logic must not be rewritten; only extend mode options.
2) Provider-agnostic:
   - Do not hardcode a single vendor in architecture. Implement a provider adapter interface.
   - Support at least one paid provider in practice (configured by env vars), but keep code structured to swap providers.
3) Privacy & security:
   - No API keys in the browser.
   - Transit calls must go through backend proxy (or server-side execution) with strict redaction of PII.
4) Performance:
   - Routing calls must have timeouts and must degrade gracefully to walking estimates if provider fails.
   - Avoid excessive per-turn routing calls; add caching where safe.
5) UX minimalism:
   - Do not introduce new multi-step dialogs. Add mode choice only when itinerary feasibility/routing matters.

## Required Deliverables

### A) Spec updates
- Update `/spec/planner-logic.md`:
  - Extend `travel_time_minutes(from,to,mode,depart_at?)` to support `mode="transit"`
  - Define output fields for transit:
    - duration_min
    - confidence
    - provider
    - (optional) route_summary: walking_legs_min, transit_legs, transfers_count
  - Define fallback behavior:
    - If transit provider unavailable -> use walk heuristic or “unknown” with user messaging guidance
  - Define caching rules at a high level (TTL, keying by from/to/mode and coarse time bucket if depart_at is used later)

- Update `/spec/orchestration.md`:
  - Add a single preference:
    - “Prefer walking only” (default true in v1) evolves into “Travel mode: walk or transit”
  - Define when to ask:
    - Ask only when user is building an itinerary or asking “how do I get there / can I make both”
  - Define copy for:
    - enabling transit
    - fallback to walking if transit fails

- Update `/spec/cost-model.md`:
  - Add estimated routing call volume assumptions and cost controls
  - Add per-request routing budget constraints (caps, caching assumptions)

- Update `/spec/security-constraints.md`:
  - Provider key storage in server env
  - Rate limiting for routing endpoint(s)
  - Logging redaction requirements (no raw addresses beyond venues; never log user PII)

### B) API / Proxy contract (only if needed)
- If the architecture uses a dedicated routing endpoint, update `/spec/api-contract.yaml` to include:
  - GET /api/routing/time?from_lat=&from_lng=&to_lat=&to_lng=&mode=transit
  - Response: TravelTime object (duration + route_summary)
- If routing is handled internally server-side without exposing an endpoint, document rationale and do NOT add a new API surface.

### C) Implementation
- Add a provider adapter interface, e.g.:
  - `TransitProvider.getTravelTime(from,to,options) -> TravelTime`
- Implement at least one paid provider behind env config (keys server-side).
- Add resilient behavior:
  - timeouts
  - retries (small and bounded)
  - circuit breaker behavior (optional)
  - caching (in-memory baseline + optional external adapter)

### D) Tests / evals
Add new eval cases:
- “Transit enabled itinerary becomes feasible where walking is not”
- “Provider failure falls back to walking estimate and user is informed”
- “Mode preference persisted (localStorage) and respected”
- “No regression for walk-only behavior”

## Non-Goals
- No arrive-by/depart-at timetable accuracy in v2 (unless explicitly requested later)
- No multi-modal optimization beyond mode selection (walk vs transit)
- No driving mode
- No GTFS self-hosting (avoid ops burden)
- No route step-by-step turn instructions beyond a short summary unless provider returns it reliably

## Definition of Done (DoD)
- [ ] Planner supports `mode="transit"` without refactoring existing feasibility logic
- [ ] Default remains walk-only; transit is opt-in or preference-based
- [ ] Transit provider integrated with server-side secrets and strict timeouts
- [ ] Graceful fallback to walking when transit is unavailable
- [ ] Caching implemented (baseline in-memory) to reduce routing calls
- [ ] New evals added; all existing evals still pass
- [ ] Cost-model updated with routing volume + caps
- [ ] Security constraints updated (keys, rate limits, redaction)

## Notes for Future Extensions
- Add depart_at/arrive_by support and time-dependent routing (v3)
- Add “avoid stairs / accessible routing” if provider supports it
- Add “bike” mode if needed (but keep driving out unless explicitly desired)