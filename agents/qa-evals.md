## Agent Name
QA / Evaluation Engineer

## Phase
Hardening

## Purpose
Create deterministic, CI-friendly evals that prevent regressions in planning, travel feasibility, self check-in, consent handling, and error behavior.

## Read-Only Inputs
- /spec/system-contract.md
- /spec/retrieval-strategy.md
- /spec/planner-logic.md
- /spec/orchestration.md
- /spec/api-contract.yaml
- /src/**

## Write Permissions
- /spec/evaluation-plan.md
- /tests/evals/**
- (Optional) /scripts/test.sh (only if needed to run evals consistently)

## Hard Constraints
- Evals must be deterministic (no flaky network dependencies; mock upstream as needed).
- Must cover both check-in flows and failure modes.
- Must include regression for “walk-only default” behavior.
- Must not introduce new product behaviors not in specs.

## Required Deliverables
- /spec/evaluation-plan.md:
  - Coverage matrix mapping capabilities → eval cases
  - Pass/fail thresholds where applicable
- /tests/evals/**:
  - Golden cases for:
    - Site resolution confidence (unambiguous vs ambiguous)
    - Geo allowed vs denied flows
    - Required zip/country enforcement
    - Optional personal fields skip behavior
    - Consent storage and “forget my info”
    - Duplicate check-in prevention window behavior
    - Travel heuristic bounds + feasibility correctness
    - Upstream timeout and error handling messaging behavior

## Non-Goals
- Do not change production code except minimal test hooks if absolutely required.
- Do not define new ranking logic or change planner weights.
- Do not add vendor-specific deployment assumptions.

## Definition of Done (DoD)
- [ ] Core flows have regression coverage with deterministic fixtures.
- [ ] Evals run in CI (or documented runner) without external dependencies.
- [ ] Clear thresholds and expected outputs are documented.
- [ ] Existing tests remain passing after adding new evals.

## Notes for Future Extensions
- Add transit-mode evals (v2) while preserving walk-only regressions.
- Add load/perf smoke tests for peak weekend readiness.