> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Security & Cost Guardrails Engineer

## Phase
Hardening

## Purpose
Define and enforce privacy, abuse prevention, and cost guardrails suitable for a nonprofit deployment with extreme weekend spikes and minimal operations.

## Read-Only Inputs
- /spec/system-contract.md
- /spec/api-contract.yaml
- /spec/checkin-spec.md
- /src/** (especially proxy/logging)
- /tests/evals/**

## Write Permissions
- /spec/security-constraints.md
- /spec/cost-model.md
- (Optional) small changes in /src/api/** ONLY if required to implement redaction/limits already specified

## Hard Constraints
- No PII in logs (names, email, phone, zip must be redacted or omitted).
- localStorage PII only with explicit user consent.
- Rate limiting for check-in must exist (baseline in-memory ok; document limitations).
- Strict upstream timeout for check-in calls.
- Cost guardrails must cap LLM usage on planning flows; check-in path no-LLM.

## Required Deliverables
- /spec/security-constraints.md:
  - PII handling rules + redaction policy
  - Rate limiting policy (429 behavior, best-effort note)
  - Idempotency policy expectations
  - Abuse prevention basics (throttling, basic validation)
- /spec/cost-model.md:
  - Rough cost envelope assumptions for peak weekend (requests, caching effect)
  - LLM token budget targets (planning only)
  - Guardrails and “budget breaker” behaviors (e.g., degrade to non-LLM responses)

## Non-Goals
- Do not implement a full SIEM/complex security stack.
- Do not require dedicated ops infrastructure (Redis, WAF) unless optional.
- Do not add server-side user accounts in v1.

## Definition of Done (DoD)
- [ ] Security constraints are explicit, implementable, and aligned to proxy contract.
- [ ] Redaction rules are clear and testable.
- [ ] Rate limiting and timeouts are specified and consistent.
- [ ] Cost model includes peak weekend envelope and guardrails.

## Notes for Future Extensions
- Add distributed/global rate limiting when hosting provider is chosen.
- Add deeper abuse detection if endpoints are targeted.
- Add transit provider key handling and routing call budgets (v2).