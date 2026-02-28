# OHNY Agentic Chatbot

This repository holds scaffolding for an agentic OHNY chatbot focused on planning, retrieval, orchestration, and self check-in.
The workflow is specs-first and uses staged approval gates before deeper implementation work begins.
Current contents are placeholders and planning artifacts only.

## Folder Structure
- `spec/`: product, system, data, API, evaluation, deployment, and check-in specifications.
- `src/`: future implementation areas for retrieval, planning, orchestration, API, and check-in.
- `tests/`: evaluation and test scaffolding.
- `case-study/`: portfolio and case-study documentation placeholders.
- `scripts/`: bootstrap, lint, and test entrypoints.
- `.github/workflows/`: CI workflow scaffolding.

## Approval Gates
- Gate 1: `product-architecture`, `system-contract`, `success-metrics`
- Gate 2: `data-model`, `retrieval-strategy`, `planner-logic`, `orchestration`, `api-contract`

## How To Run Tests
- Placeholder: run `./scripts/test.sh`
- Placeholder: CI will call the same script from GitHub Actions

## Status
- Scaffolding only
- No production implementation code yet
