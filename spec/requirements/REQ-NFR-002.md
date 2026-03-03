# REQ-NFR-002: Degrade gracefully under burst traffic
**Status:** Proposed
**Priority:** P0
**Owner:** Platform Performance
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/success-metrics.md
**Depends On:** None
**Validated By:** TBD

## Description
Under extreme OHNY burst traffic, the system must preserve core planning and check-in flows by reducing non-essential conversational richness before allowing severe latency growth or hard failure.

## Rationale
Gate 1 explicitly prefers graceful degradation over collapse during peak demand.

## Acceptance Criteria
- Given burst traffic conditions, when resource pressure rises, then core planning and check-in flows remain prioritized over optional conversational richness.
- Given burst degradation is activated, when responses are shortened, then optional refinements, secondary commentary, or extra explanation may be reduced first.
- Given burst traffic persists, when the system degrades, then usable responses are preserved where safe rather than timing out by default.

## Non-Goals
- Preserving every optional conversational flourish during peak load.
- Claiming success for flows that can no longer proceed safely.

## Notes
- This requirement complements rate limiting and caching controls.
