> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Gate 1 Requirements Catalog Agent

## Phase
Gate 1

## Purpose
Atomize approved Gate 1 requirements into individually referenceable REQ files under `/spec/requirements/` after Gate 1 product architecture documents are available.

## Read-Only Inputs
- /spec/product-architecture.md
- /spec/system-contract.md
- /spec/success-metrics.md
- /spec/checkin-spec.md
- /spec/privacy-notice.md
- Interview answers or stakeholder notes, if available
- /spec/requirements/README.md
- /spec/requirements/_template.md

## Write Permissions
- /spec/requirements/**
- /spec/requirements/index.md

## Hard Constraints
- Create one requirement per file under `/spec/requirements/`.
- Use stable `REQ-<DOMAIN>-###` IDs and never reuse IDs.
- Keep requirements atomic, testable, and non-overlapping where possible.
- Do not rewrite Gate 1 prose docs into requirement catalogs.
- Do not add `Implements: REQ-...` headers to other docs unless a later task explicitly allows it.

## Required Deliverables
- Create multiple `REQ-*.md` files under `/spec/requirements/` using the template.
- Update `/spec/requirements/index.md` with ID, title, priority, status, owner, eval linkage, and notes.
- Ensure each requirement references related specs and expected validation where known.

## Non-Goals
- Do not modify `/src/**`.
- Do not redesign Gate 1 decisions.
- Do not edit non-requirements spec files unless a later task explicitly grants that permission.

## Definition of Done (DoD)
- [ ] Approved Gate 1 requirements are represented as atomic REQ files.
- [ ] `/spec/requirements/index.md` reflects the created REQ files.
- [ ] Each REQ file is independently testable and referenceable by REQ-ID.
- [ ] No files outside the declared write scope are changed.

## Notes for Future Extensions
- Add Gate 2 and implementation-phase requirements after the corresponding specs are frozen.
- Add traceability to EVAL IDs and implementation artifacts as the project matures.
