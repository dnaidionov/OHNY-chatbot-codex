# Atomic Requirements System

Atomic requirements live in this directory as one Markdown file per requirement.
Each requirement is independently referenceable by `REQ-ID` and should not be duplicated verbatim across higher-level specs.

## Domains
- `PLAN`: planning and itinerary rules
- `RETR`: retrieval and ranking inputs
- `TRAVEL`: travel and routing behavior
- `ORCH`: orchestration and conversation flows
- `CHECKIN`: self check-in behavior
- `PROXY`: backend proxy and integration behavior
- `PRIV`: privacy, consent, and data handling
- `NFR`: non-functional requirements
- `OPS`: operational and release requirements

## File Naming
- One file per requirement: `/spec/requirements/REQ-<DOMAIN>-###.md`
- Examples:
  - `REQ-CHECKIN-001.md`
  - `REQ-TRAVEL-001.md`
  - `REQ-PRIV-002.md`

## ID Stability Rules
- Never reuse a `REQ-ID`.
- If a requirement is no longer active, mark it `Deprecated` instead of deleting it.
- Keep the file path stable after publication.

## Referencing Rules
- Other specs should reference requirements by ID instead of duplicating requirement prose.
- Use concise references such as `Implements: REQ-CHECKIN-001` or `Related REQs: REQ-PRIV-002, REQ-NFR-001`.
- Eval IDs should map back to REQ IDs, for example: `EVAL-CHECKIN-001 validates REQ-CHECKIN-001`.

## Ownership Rules
- The Requirements Catalog agent is responsible for creating and updating atomic REQ files unless another task explicitly grants `/spec/requirements/**` write access.
- Other agents should reference REQ IDs when applicable but must not edit REQ files unless their task file explicitly permits it.
