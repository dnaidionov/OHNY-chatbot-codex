# Agentic SDLC Workflow

This repository uses a contract-driven AI agent workflow with two approval gates.

## Gates

### Gate 1 – Product Architecture Freeze
Artifacts:
- /spec/product-architecture.md
- /spec/system-contract.md
- /spec/success-metrics.md
- /spec/checkin-spec.md
- /spec/privacy-notice.md

Gate 1 must be approved/merged before any Gate 2 work is accepted.

### Gate 2 – Intelligence + Interface Freeze
Artifacts:
- /spec/data-model.md
- /spec/retrieval-strategy.md
- /spec/planner-logic.md
- /spec/orchestration.md
- /spec/api-contract.yaml

Gate 2 must be approved/merged before implementation.

## Post Gate 2
Implementation and hardening:
- /src/** (implementation)
- /tests/evals/** (evals)
- /spec/security-constraints.md (security/privacy)
- /spec/cost-model.md (cost)
- /spec/deployment.md and /spec/runbook.md (ops)

Narrative:
- /case-study/**

## File Ownership Rules (to avoid collisions)
- Only the Integration/API agent edits: /spec/api-contract.yaml
- Only the Security/Cost agent edits: /spec/security-constraints.md and /spec/cost-model.md
- Only the Ops/Release agent edits: /spec/deployment.md and /spec/runbook.md
- If another agent needs changes in those files, it must raise a PR comment/issue, not edit them.

## Parallelization Rule
Never run two agents that modify the same files at the same time.

## Architectural Principles
- Travel is first-class; v1 is Tier 0 walking only.
- Self check-in uses a thin backend proxy; no secrets in the browser.
- No LLM calls in the check-in path (site resolution is retrieval-driven).
- Deployment is provider-agnostic: serverless OR single container.
- Personalization is localStorage-based with explicit user consent and “forget” support.