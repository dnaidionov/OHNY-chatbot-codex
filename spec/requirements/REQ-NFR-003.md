# REQ-NFR-003: Cache or precompute public site data for core flows
**Status:** Proposed
**Priority:** P0
**Owner:** Platform Performance
**Related Specs:** /spec/product-architecture.md, /spec/system-contract.md, /spec/success-metrics.md
**Depends On:** None
**Validated By:** TBD

## Description
Public OHNY site data should be cached or precomputed so planning and site resolution do not require expensive recomputation on every request.

## Rationale
Gate 1 calls this out as a core scaling measure for bursty traffic.

## Acceptance Criteria
- Given planning or site-resolution requests repeat against the same public OHNY data, when the system serves them, then it does not require full recomputation every time.
- Given the system is reviewed for peak-load readiness, when data dependencies are examined, then public site data has a caching or precomputation strategy for core flows.
- Given operational metrics are collected, when cache effectiveness is measured, then cache-hit observability is available.

## Non-Goals
- Caching mutable personal profile data.
- Requiring a specific cache product or hosting model.

## Notes
- Curated public site data is the primary target of this requirement.
