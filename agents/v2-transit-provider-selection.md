# V2 – Transit Provider Selection Agent

## Agent Name
Transit Provider Selection Analyst (v2)

## Phase
V2 Preparation (before implementing Transit Routing Agent)

## Purpose
Evaluate and recommend a transit routing provider suitable for:
- Small nonprofit budget
- Minimal operational overhead
- High burst load during OHNY weekend
- Strong reliability under real-world NYC transit conditions

Produce a clear, defensible decision with tradeoffs documented.

## Read-Only Inputs
- /spec/product-architecture.md
- /spec/planner-logic.md
- /spec/system-contract.md
- /spec/cost-model.md
- /spec/security-constraints.md
- /agents/v2-transit-routing.md

## Write Permissions
- /spec/transit-provider-evaluation.md
- /spec/cost-model.md (transit section only)
- /case-study/design-decisions.md (append transit decision rationale)

## Hard Constraints
1. Must assume:
   - Hosting provider is unknown.
   - No dedicated DevOps team.
   - OHNY Weekend spike traffic significantly higher than baseline.
2. Must favor:
   - Low operational complexity.
   - Predictable cost.
   - Reliable SLA.
3. Must avoid:
   - Self-hosted GTFS routing stacks unless strongly justified.
   - Solutions requiring ongoing manual data updates.
4. Must consider privacy implications of sending venue lat/lng (no user PII beyond what is required).

## Required Evaluation Criteria

For each candidate provider (minimum 3 options):
- Pricing model (per request / per MAU / per route)
- Estimated monthly + peak cost during OHNY Weekend (rough scenario modeling)
- SLA / reliability track record
- Ease of server-side integration
- Transit support quality (NYC coverage)
- Rate limiting characteristics
- Ease of fallback behavior
- Vendor lock-in risk
- Operational burden

Include at least:
- One major paid API provider
- One alternative paid provider
- One “free / open-source” option with realistic operational assessment

## Required Deliverables

### 1) Comparison Table
Clear matrix comparing:
- Cost
- Reliability
- Operational burden
- Fit for OHNY constraints

### 2) Scenario Modeling
- Estimate requests per user during peak weekend
- Estimate total routing calls under reasonable traffic assumptions
- Translate into cost range

### 3) Recommendation
Provide:
- Primary recommended provider
- Backup provider
- Conditions under which to switch

### 4) Integration Notes
Short technical note describing:
- How the provider would integrate with existing proxy pattern
- Any changes required in /spec/api-contract.yaml
- Any cost guardrails needed (caching, batching, etc.)

## Non-Goals
- Do not implement anything.
- Do not modify planner logic.
- Do not introduce driving mode.
- Do not assume arrive-by timetable precision (unless part of provider core behavior).
- Do not claim measured reliability unless sourced/validated.

## Definition of Done (DoD)
- [ ] At least 3 provider options evaluated
- [ ] Cost scenario for peak weekend estimated with explicit assumptions
- [ ] Clear primary recommendation with justification + backup documented
- [ ] Risks documented
- [ ] Design-decisions.md updated with rationale
- [ ] Cost-model.md updated (transit section).
