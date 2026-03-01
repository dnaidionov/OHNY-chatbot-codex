> This task inherits and MUST follow `/agents/_preamble.md`.

## Agent Name
Data & Retrieval Engineer (Gate 2)

## Phase
Gate 2

## Purpose
Define canonical data model and retrieval strategy that supports planning, multiple time slots, robust site lookup for check-in, and deterministic confidence scoring.

## Read-Only Inputs
- /spec/product-architecture.md
- /spec/system-contract.md
- /spec/checkin-spec.md
- Any sample data files if present

## Write Permissions
- /spec/data-model.md
- /spec/retrieval-strategy.md
- (Optional) /src/retrieval/README.md (design notes only)

## Hard Constraints
- Must represent multiple time slots per event (EventInstance/Timeslot).
- Must support site/venue resolution for check-in with deterministic confidence scoring.
- Must support nearest-site queries using lat/lng (no routing API needed).
- Must not require server-side user profiles.

## Required Deliverables
- /spec/data-model.md:
  - Entities: Event, Venue/Site, EventInstance, Location, Tags/Attributes
  - Normalized identifiers and required fields (lat/lng where applicable)
  - Fields required for check-in site selection
- /spec/retrieval-strategy.md:
  - Query types: keyword, semantic (if planned), filters, nearest
  - Confidence scoring approach for site resolution + ambiguity detection
  - Guidance on returning candidates for orchestrator disambiguation
  - Performance notes: caching opportunities for read-heavy lookups

## Non-Goals
- Do not define ranking weights or itinerary feasibility (Planner agent).
- Do not define conversation flows or copy (Orchestrator agent).
- Do not define API proxy contract (Integration agent).

## Definition of Done (DoD)
- [ ] Data model supports planning + check-in without missing required primitives.
- [ ] Retrieval strategy includes explicit confidence/ambiguity guidance usable by orchestrator.
- [ ] Nearest-site query behavior defined and deterministic.
- [ ] Multiple time slots are first-class in the model.

## Notes for Future Extensions
- Add data freshness rules and incremental updates if Airtable sync evolves.
- Add richer geo indexing and optional external vector DB adapter if needed.
- Add venue aliases and multilingual names if required.