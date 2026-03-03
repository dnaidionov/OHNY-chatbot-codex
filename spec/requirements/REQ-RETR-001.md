# REQ-RETR-001: Resolve OHNY sites from curated data
**Status:** Proposed
**Priority:** P0
**Owner:** Retrieval Service
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md
**Depends On:** None
**Validated By:** TBD

## Description
The retrieval layer must resolve OHNY sites and aliases from curated OHNY data and act as the source of truth for site identity in planning and check-in flows.

## Rationale
Gate 1 depends on deterministic site matching rather than generative guessing.

## Acceptance Criteria
- Given a site query matching a known OHNY site name or alias, when retrieval runs, then it returns the canonical site identity.
- Given a planning or check-in flow, when a site needs to be resolved, then the system uses retrieval output rather than an LLM-generated site guess.
- Given curated OHNY data updates, when retrieval serves requests, then site resolution reflects that curated data set.

## Non-Goals
- Scraping arbitrary third-party content at request time.
- Inventing new sites that are not in curated OHNY data.

## Notes
- Candidate ranking policy is refined by other retrieval requirements.
