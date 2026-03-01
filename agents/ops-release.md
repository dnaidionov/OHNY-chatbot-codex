> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Ops / Release Engineer

## Phase
Hardening

## Purpose
Create a provider-agnostic deployment plan and runbook that a volunteer can operate during OHNY weekend with minimal intervention.

## Read-Only Inputs
- /src/**
- /spec/system-contract.md
- /spec/api-contract.yaml
- /spec/security-constraints.md
- /spec/cost-model.md

## Write Permissions
- /spec/deployment.md
- /spec/runbook.md
- /.github/workflows/ci.yml (make it real if placeholder)
- /scripts/bootstrap.sh, /scripts/test.sh (optional, if helpful)

## Hard Constraints
- Must support deployment as serverless OR as a single containerized Node service.
- Must include clear env var list (aligned to .env.example).
- Must include rollback steps.
- Must include weekend spike monitoring guidance.
- Must avoid provider-specific instructions unless labeled as example.

## Required Deliverables
- /spec/deployment.md:
  - Deployment modes (serverless vs container) and how to choose
  - Environment variables required
  - Caching and rate limiting operational notes
- /spec/runbook.md:
  - “Day of OHNY” checklist
  - Monitoring signals (latency, error rate, upstream failures, rate limits)
  - Incident handling steps (upstream down, overload, abuse)
  - Rollback procedure
- CI workflow that runs tests/evals on PRs and main.

## Non-Goals
- Do not require Kubernetes or complex infrastructure.
- Do not add vendor lock-in steps as mandatory.
- Do not invent OHNY upstream API operational policies; focus on our proxy behavior.

## Definition of Done (DoD)
- [ ] A volunteer can deploy and operate using only these docs.
- [ ] CI runs tests/evals consistently.
- [ ] Rollback and incident steps are clear and realistic.
- [ ] Spike readiness guidance is included.

## Notes for Future Extensions
- Add provider-specific deployment playbooks once hosting is selected.
- Add stronger observability integrations (Sentry, OpenTelemetry) if budget allows.