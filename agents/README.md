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

---

## Global PR Execution Contract (Mandatory for All Agents)

Before executing any agent task file in this directory, the agent MUST:

1) Read and follow `/agents/_preamble.md` in full.
2) Respect file write scope defined in the task file.
3) Work via Pull Request only (never push directly to `main`).
4) Stop and report if required changes fall outside the defined write scope.

### Execution Protocol

When running an agent in Codex:

- Start from latest `main`.
- Create a new branch:
  - `agent/<agent-name>/<short-topic>`
- Execute the task file exactly as written.
- Open a Pull Request with:
  - Summary of changes
  - List of modified files
  - Checklist showing how the Definition of Done (DoD) was satisfied

If the agent believes:
- A spec must change outside its scope
- A dependency is missing
- A design contradiction exists

The agent must:
- Leave a PR comment explaining the issue
- Halt further changes
- Await direction

### Scope Discipline

Each agent owns specific files.
No agent may modify files outside its declared “Write Permissions.”

If cross-file changes are needed:
- Raise a follow-up task
- Do not silently edit

This preserves:
- Reproducibility
- Parallel safety
- Clean review boundaries
- Gate integrity

---

## Why This Matters

This repository is structured to support:
- Deterministic AI agent collaboration
- Explicit architecture gates
- Minimal human oversight
- High-confidence iteration

Violating PR discipline undermines the entire workflow.