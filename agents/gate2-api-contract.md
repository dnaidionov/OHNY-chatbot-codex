> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Integration Lead (Gate 2)

## Phase
Gate 2

## Purpose
Define a provider-agnostic thin backend proxy contract for check-in and site lookup that protects secrets, supports peak load, and returns consistent errors.

## Read-Only Inputs
- /spec/system-contract.md
- /spec/checkin-spec.md
- /spec/orchestration.md
- /spec/data-model.md
- /spec/retrieval-strategy.md

## Write Permissions
- /spec/api-contract.yaml
- /spec/security-constraints.md (proxy/PII/rate-limit/timeout sections only)
- /spec/deployment.md (proxy sections only)

## Hard Constraints
- No secrets in browser; proxy is only upstream caller.
- Check-in path must not include LLM calls.
- Strict upstream timeout must be defined.
- Rate limiting must be defined (baseline in-memory best-effort + optional external adapter).
- Idempotency/dedup must be defined (Idempotency-Key or checkin_attempt_id).
- Error model must be consistent across endpoints.

## Required Deliverables
- /spec/api-contract.yaml (valid OpenAPI 3.x) defining:
  - POST /api/checkin
  - GET /api/sites/search?q=
  - GET /api/sites/near?lat=&lng=&radius_m=
  - Schemas: CheckInRequest, CheckInResponse, ApiError, SiteCandidate, SiteListResponse
  - Examples for success and error responses
- /spec/security-constraints.md updates documenting:
  - PII redaction requirements (logs)
  - Rate limit behavior and expected responses (429)
  - Idempotency handling expectations
- /spec/deployment.md proxy notes:
  - Works in serverless OR single container
  - Env var requirements (placeholders)

## Non-Goals
- Do not invent exact upstream OHNY API endpoints/auth; describe upstream mapping as TBD.
- Do not implement proxy code.
- Do not define planner ranking or conversation copy.

## Definition of Done (DoD)
- [ ] OpenAPI spec validates logically (complete paths/components and consistent error shapes).
- [ ] Idempotency and dedupe behavior is explicitly documented.
- [ ] Timeout and rate limiting behavior are explicitly documented.
- [ ] Browser-facing contract is minimal and aligned to orchestration needs.
- [ ] Upstream mapping clearly marked TBD with required integration info listed.

## Notes for Future Extensions
- Add /api/routing/time endpoint for v2 transit routing if needed.
- Add external cache/ratelimit adapter guidance once hosting provider is selected.
- Add stronger abuse detection if public endpoints are targeted.