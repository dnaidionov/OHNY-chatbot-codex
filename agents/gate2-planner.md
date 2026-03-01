## Agent Name
Planner & Ranking Engineer (Gate 2)

## Phase
Gate 2

## Purpose
Define deterministic ranking and itinerary feasibility logic using the first-class travel interface, while keeping v1 strictly Tier 0 walking.

## Read-Only Inputs
- /spec/system-contract.md
- /spec/data-model.md
- /spec/retrieval-strategy.md

## Write Permissions
- /spec/planner-logic.md

## Hard Constraints
- Must define `travel_time_minutes(from,to,mode="walk",depart_at?)` as stable interface.
- Mode-aware for future transit, but only implement/assume “walk” in v1.
- Feasibility rule must be explicit and testable (no implicit LLM judgment).
- Ranking logic must be deterministic and explainable.

## Required Deliverables
- /spec/planner-logic.md:
  - Intent buckets relevant to v1 (browse/search, compare, shortlist, itinerary feasibility)
  - Ranking model: factors + weights or prioritized rules
  - Conflict resolution for overlapping timeslots
  - Feasibility formula using travel duration + buffer
  - Walking heuristic assumptions (distance → minutes) + sanity bounds
  - Inputs/outputs contract between retrieval → planner → orchestrator

## Non-Goals
- Do not define check-in flows (Orchestrator agent).
- Do not define API contracts (Integration agent).
- Do not implement code.

## Definition of Done (DoD)
- [ ] Planner logic is deterministic, testable, and maps back to system-contract goals.
- [ ] Travel is first-class with stable interface; v1 is walk-only.
- [ ] Multi-slot conflict resolution and feasibility checks are explicit.
- [ ] No part of ranking/feasibility depends on LLM hidden scoring.

## Notes for Future Extensions
- Add v2 transit mode behavior without refactoring planner (adapter swap).
- Add depart_at/arrive_by time-dependent routing in v3 if needed.
- Add accessibility constraints and penalties (stairs, step-free) when supported.