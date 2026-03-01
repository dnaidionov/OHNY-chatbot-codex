# Merge Protocol

This repository uses a gate-based, contract-driven workflow. Merges to `main` are the control point that prevents drift and protects peak-weekend reliability.

## Core Principles

1) **PR-only to main**
- No direct pushes to `main`.

2) **Specs-first**
- If behavior changes require spec changes, do it as:
  - PR A: spec change (review/merge)
  - PR B: implementation change (review/merge)

3) **Gate integrity**
- Gate 1 and Gate 2 freezes are real. After a gate is merged, downstream work must conform unless a deliberate gate revision PR is created.

4) **Scope discipline**
- Each agent PR must modify only files within its declared write scope.
- If cross-scope changes are required, raise a follow-up PR/task. Do not silently edit.

5) **Peak safety over speed**
- For OHNY weekend readiness, correctness, timeouts, rate limiting, and PII safety take priority.

## When to Merge

### A) Scaffolding and Process PRs
Examples:
- `/agents/**`
- repo scaffolding
Merge when:
- Changes are strictly in intended paths
- No accidental deletions or unrelated edits

### B) Gate 1 PR (Product Architecture Freeze)
Merge when:
- Gate 1 files are coherent and mutually consistent:
  - `/spec/product-architecture.md`
  - `/spec/system-contract.md`
  - `/spec/success-metrics.md`
  - `/spec/checkin-spec.md`
  - `/spec/privacy-notice.md`
- Constraints are explicit:
  - Tier 0 walking only (v1)
  - localStorage personalization (consent + forget)
  - thin backend proxy for check-in
  - **no LLM in check-in path**
  - provider-agnostic deploy (serverless OR container)
  - peak-load orientation

### C) Gate 2 PRs (Intelligence + Interface Freeze)
Recommended merge order:
1) Data/Retrieval
2) Planner
3) Orchestration
4) API Contract

Merge each when:
- It does not contradict Gate 1
- Deterministic rules are explicit (confidence thresholds, feasibility formula)
- It stays within scope

After Gate 2 is merged, treat these as frozen:
- `/spec/data-model.md`
- `/spec/retrieval-strategy.md`
- `/spec/planner-logic.md`
- `/spec/orchestration.md`
- `/spec/api-contract.yaml`

### D) Implementation PRs
Merge when:
- Implementation conforms to frozen specs
- Core paths work end-to-end locally (or with mocks)
- Tests/evals pass (or there is a documented exception with follow-up)
- **No secrets in client**
- **No PII in logs**
- Check-in path is fast, has timeouts, and is no-LLM

Prefer splitting implementation into 2–3 PRs max if it’s too large to review.

### E) Hardening PRs (QA, Security/Cost, Ops)
Merge as soon as:
- They improve safety/reliability without breaking functionality
- CI/evals remain green (or are improved)

### F) Case Study PRs
Merge when:
- Claims match actual repo state
- Measured results are included only if they exist; otherwise mark TBD with methodology

## How to Merge

### Default merge method: **Squash and merge**
- Keeps `main` clean
- Easy rollback

Exceptions:
- Preserve commit history only if it meaningfully improves traceability (rare).

## PR Review Checklist (Fast)

1) **Scope check**
- Files changed match the agent’s write permissions.

2) **Contract check**
- No contradictions with Gate 1/Gate 2 specs.

3) **Security check**
- No secrets in client
- No PII in logs
- Proxy-only access to upstream OHNY API

4) **Performance check**
- Check-in path has strict timeouts
- Rate limiting exists (baseline OK)
- No LLM dependency in check-in path

5) **DoD check**
- PR description includes a DoD checklist and it’s satisfied.

6) **CI/evals check**
- CI passes
- Evals pass (or documented reason + follow-up task)

## Hard Merge Blockers (Do not merge)

- Any secret/API key in browser/client code
- Any PII (name/email/phone/zip) logged in plaintext
- Check-in path depends on LLM output for site resolution
- A PR silently changes specs and code together without explicit approval
- Massive unrelated changes mixed into a single PR without explanation

## Notes for OHNY Weekend Hotfixes

- Prefer small PRs with minimal blast radius.
- Keep check-in operational above all else.
- If upstream OHNY API is unstable: degrade gracefully and preserve user-entered data client-side.