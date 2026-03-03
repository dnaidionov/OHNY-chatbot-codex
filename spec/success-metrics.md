# Success Metrics

## Implements Requirements
- REQ-PLAN-002
- REQ-CHECKIN-004
- REQ-PROXY-004
- REQ-PRIV-004
- REQ-NFR-001
- REQ-NFR-002
- REQ-NFR-003
- REQ-OPS-001
- REQ-OPS-002

## Purpose
Capture the primary measures for product quality, check-in success, planner utility, operational resilience, and cost discipline for v1.

## Primary Product Metric
- The v1 north-star metric must be check-in completion rate for users who start a check-in flow.
- This metric should be segmented by:
  - named-site versus unnamed check-in
  - geo-available versus geo-denied
  - saved-info reuse versus manual entry
  - in-event-window versus outside-event-window attempts

## Planning Metrics
- Planning success rate: percent of planning requests that produce at least one relevant recommendation set.
- Time to first recommendation: time from user request to first recommendation payload.
- Clarification burden: average number of follow-up questions before the first recommendation.
- Feasible-plan rate: percent of recommendation sets that include at least one option labeled feasible within walking assumptions.
- Aspirational-label correctness should be tracked qualitatively in evaluation so infeasible options are not misrepresented as workable plans.

## Retrieval Metrics
- Confident site resolution rate: percent of check-in and lookup requests resolved to one clear site or a short disambiguation list.
- Ambiguity recovery rate: percent of ambiguous matches that successfully convert to a user-confirmed site.
- No-match recovery rate: percent of no-confident-match cases that recover after a follow-up hint.
- Geo-to-site confirmation rate: percent of unnamed geo-based check-ins that convert from proposed site to confirmed site.

## Check-In Metrics
- Check-in completion rate must remain the top-level product metric.
- First-attempt check-in success rate should be tracked separately from retry success rate.
- Upstream failure rate should be measured distinctly from product-abandonment rate.
- Saved-profile reuse rate should track how often a returning user completes check-in using consented device-local info.
- Daily party-size reconfirmation completion rate should confirm whether the extra daily step creates material drop-off.
- Off-weekend warning acknowledgment rate should measure whether users proceed after the warning.

## Privacy And Trust Metrics
- Local-save opt-in rate should measure acceptance of device-only persistence.
- `Forget my info` completion rate should measure whether deletion is discoverable and effective.
- Planning-preference reset usage should be measured separately from check-in info deletion.
- Geolocation grant rate on first load should be tracked alongside first-day and second-ask denial rates.
- Privacy metrics must be collected in aggregate form only and must not depend on server-side personal profiles.

## Operational Metrics
- P95 turn latency for planning and check-in flows
- Rate-limit trigger rate during OHNY peak traffic
- Cache hit rate for public site data
- Burst survival metric: percent of peak-window requests that receive a usable response rather than timing out
- Upstream OHNY API availability as observed by the proxy

## Quality Guardrails
- The system must not report check-in success unless the upstream API confirms it.
- The system must keep the no-LLM check-in path intact; check-in success must not depend on live LLM availability for site resolution.
- The system should keep recommendation flows concise by default, with recommendation-first responses and short rationale.
- The system should maintain clear feasible-versus-aspirational labeling in planner outputs.

## Cost Guardrails
- Check-in requests must avoid LLM dependency in the submission path to keep cost and reliability predictable.
- Public site data should be served from cached or precomputed sources whenever possible.
- The system should minimize unnecessary repeated clarifications to reduce model usage.
- Under burst conditions, the system should reduce optional explanation depth before allowing expensive conversational expansion.
- v1 must avoid introducing persistent server-side profile infrastructure solely for personalization.
