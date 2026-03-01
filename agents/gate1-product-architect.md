## Agent Name
Product Architect (Gate 1)

## Phase
Gate 1

## Purpose
Freeze the product architecture, capability scope, non-functional requirements, privacy posture, and self check-in behavior so Gate 2 can implement deterministic contracts.

## Read-Only Inputs
- README.md
- /spec/* (existing, if any)

## Write Permissions
- /spec/product-architecture.md
- /spec/system-contract.md
- /spec/success-metrics.md
- /spec/checkin-spec.md (high-level only; no upstream OHNY API specifics)
- /spec/privacy-notice.md

## Hard Constraints
- V1 routing: Tier 0 walking only; travel is first-class and mode-aware for future transit.
- V1 personalization: browser localStorage only; no server-side user profiles.
- V1 self check-in: via thin backend proxy forwarding to existing OHNY API (mapped later).
- Device geolocation: optional; must degrade gracefully.
- Hosting unknown: deployment must support serverless OR single container.
- Peak load: must handle extreme burst traffic during OHNY weekend.
- Check-in path must not depend on LLM calls (site resolution must be retrieval-driven).

## Required Deliverables
- /spec/product-architecture.md:
  - Component diagram (text) and separation of retrieval/planner/orchestrator/proxy
  - Travel contract at interface level (not implementation) and feasibility usage
  - Provider-agnostic scaling notes: baseline cache + baseline rate limiting
- /spec/system-contract.md:
  - Capabilities and supported user commands/examples (incl. check-in + forget)
  - Privacy/consent model for localStorage PII
  - Failure modes + fallback behaviors (geo denied, ambiguous site, upstream failure)
  - NFR targets (latency, availability, spike tolerance)
- /spec/success-metrics.md:
  - Planning/retrieval/check-in metrics + cost guardrails (no-LLM check-in)
- /spec/checkin-spec.md:
  - Two user flows + required/optional fields + donation nudge rule (high level)
- /spec/privacy-notice.md:
  - User-facing explanation: what is stored locally, what is sent to server, how to clear

## Non-Goals
- Do not invent upstream OHNY API endpoints/auth details.
- Do not design detailed ranking weights (Gate 2 planner).
- Do not produce implementation code.

## Definition of Done (DoD)
- [ ] Docs are coherent and mutually consistent across all Gate 1 files.
- [ ] Explicitly locks Tier 0 walking for v1 and “paid transit in v2” plan.
- [ ] Explicitly covers both check-in flows and donation prompt (after success).
- [ ] Explicitly documents consent + “forget my info”.
- [ ] Explicitly states provider-agnostic hosting and baseline cache/rate-limit approaches.
- [ ] Explicitly states no-LLM check-in path constraint.

## Notes for Future Extensions
- Add v2 integration with OHNY user profiles (server-side identity).
- Add v2 transit routing via paid provider (through same travel interface).
- Add richer analytics (anonymized, aggregate) without adding PII risk.