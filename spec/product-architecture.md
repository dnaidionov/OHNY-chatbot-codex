# Product Architecture

## Implements Requirements
- REQ-PLAN-001
- REQ-PLAN-002
- REQ-PLAN-003
- REQ-RETR-001
- REQ-RETR-004
- REQ-TRAVEL-001
- REQ-TRAVEL-002
- REQ-ORCH-001
- REQ-ORCH-002
- REQ-ORCH-003
- REQ-ORCH-004
- REQ-ORCH-005
- REQ-ORCH-006
- REQ-CHECKIN-001
- REQ-CHECKIN-002
- REQ-CHECKIN-005
- REQ-PROXY-001
- REQ-PROXY-002
- REQ-PROXY-003
- REQ-PROXY-004
- REQ-PRIV-001
- REQ-PRIV-003
- REQ-PRIV-004
- REQ-PRIV-005
- REQ-PRIV-006
- REQ-PRIV-010
- REQ-NFR-002
- REQ-NFR-003
- REQ-NFR-004

## Purpose
Define the end-to-end product shape for the OHNY chatbot, including system boundaries, travel constraints, privacy posture, and peak-load behavior for v1.

## Product Goals
- The product must help users discover OHNY sites and complete self check-in with low friction during bursty OHNY traffic.
- The product must lock v1 travel to Tier 0 walking only while keeping the travel interface mode-aware for future paid transit providers.
- The product must keep check-in deterministic and retrieval-driven; the check-in path must not depend on LLM calls for site resolution.
- The product must support multilingual conversation, with check-in field values collected or confirmed in English before submission.
- The product must support optional device geolocation and degrade gracefully when permission is denied or accuracy is insufficient.
- The product must keep v1 personalization local to the browser; no server-side user profile may be introduced in v1.

## Locked V1 Scope
- v1 must support conversational planning, site discovery, and self check-in via a thin backend proxy to an existing OHNY API.
- v1 must start with a short greeting, a brief product introduction, and 3 to 5 example prompts spanning planning and check-in.
- v1 must align with the visual language and interaction tone of `ohny.org`, while allowing chat-specific UX adaptations.
- v1 must present walking-only guidance explicitly and should redirect users to an external maps application for non-walking directions or travel times.
- v1 should end final recommendation responses with a brief reminder that users can also ask volunteers.
- v1 must not introduce server-side accounts, server-side preference storage, or detailed transit routing.

## Component Diagram
Text component diagram:

1. `Chat UI`
   - Must render the multilingual conversation, greeting, example prompts, planning outputs, consent prompts, and confirmation steps.
   - Must store only consented local profile and preference data in browser `localStorage`.
   - Must surface settings/options for `forget my info` and resetting planning preferences.

2. `Conversation Orchestrator`
   - Must classify user intent into planning, retrieval, check-in, settings/privacy, or unsupported requests.
   - Must ask at most the minimum clarifying questions needed to continue.
   - Must keep unsupported requests explicit and redirect to the closest supported action.

3. `Retrieval Layer`
   - Must resolve OHNY sites, aliases, and nearby candidates from curated OHNY data.
   - Must support single-match resolution, short-list disambiguation, and fallback hint gathering.
   - Must remain the source of truth for check-in site resolution.

4. `Planner Layer`
   - Must produce walking-only recommendation sets using retrieval outputs plus user constraints.
   - Must separate feasible recommendations from aspirational ones that likely require non-walking travel.
   - Must optimize primarily for interest fit, while still labeling whether options fit the user's stated time window.

5. `Travel Interface`
   - Must be mode-aware at the interface level even though v1 enables only `walking`.
   - Must expose feasibility and travel-time semantics that the planner can consume.
   - Should allow a future paid transit provider to plug into the same contract in v2.

6. `Check-In Proxy`
   - Must be a thin backend service that forwards validated check-in requests to the existing OHNY API.
   - Must not store server-side user profiles in v1.
   - Must enforce idempotency, baseline rate limiting, and clear error propagation.

7. `Operational Controls`
   - Must provide baseline caching for public site data and baseline rate limiting for burst protection.
   - Must support deployment either as serverless functions or as a single container without long-lived stateful services in the request path.

## Separation Of Responsibilities
- Retrieval must own site matching, alias resolution, and disambiguation candidates.
- Planner must own recommendation construction, interest fit, walking-feasibility evaluation, and aspirational labeling.
- Orchestrator must own dialogue policy, clarification order, consent prompting, and fallback selection.
- Check-in proxy must own submission forwarding, idempotency handling, rate limiting, and upstream-failure signaling.
- The UI must own local persistence prompts, settings affordances, and user-facing wording for privacy and consent.

## Travel Contract
### Interface Requirements
- The travel interface must accept: origin context, destination site, travel mode, and optional user constraints relevant to route feasibility.
- The travel interface must return at minimum: mode used, travel feasibility classification, estimated travel time, and a confidence/quality indicator suitable for planner decisions.
- v1 must only invoke the interface with `walking`.
- Planner outputs must distinguish:
  - feasible within the stated walking/time assumptions
  - strong interest match that may exceed the stated window
  - aspirational options that likely require non-walking travel

### Feasibility Usage
- The planner must use travel feasibility to label recommendations, not merely to decorate them.
- Interest fit may outrank strict time-window fit in final ranking, but the response must visibly distinguish feasible and possibly-over-window options.
- The planner should avoid presenting infeasible options as default workable itinerary steps.

## Check-In Architecture
- The check-in flow must support two primary entry points:
  - named-site check-in: `check me in at <site>`
  - unnamed check-in: `check me in`
- Named-site check-in must resolve the site through retrieval and must never silently guess when multiple plausible matches exist.
- Unnamed check-in must use geolocation first when available, then require user confirmation of the matched site.
- If geolocation is denied, unavailable, or too imprecise, the flow must fall back to retrieval-driven prompts for site name, address fragment, neighborhood, or landmark.
- Final submission must always require an explicit confirmation step showing the resolved site and required submitted fields.

## Local Data Architecture
- v1 personalization must remain browser-local only.
- The system must request explicit opt-in before saving check-in information on the device.
- The saved local profile may include user-entered repeat-use check-in fields and saved accessibility preferences after consent.
- The system must exclude highly sensitive free-form inputs and fields not useful for future check-ins from local persistence.
- The system should remember planning preferences such as interests and accessibility preferences on-device.
- The system must separate:
  - check-in info deletion
  - planning preference reset

## Peak Load And Scaling Notes
- Public OHNY site data should be cached or precomputed so planning and site resolution do not require expensive recomputation on every request.
- The system must apply baseline rate limiting at the edge and/or proxy to keep upstream pressure bounded.
- Under burst traffic, the system must preserve core planning and check-in flows by reducing non-essential conversational richness before allowing severe latency growth.
- Degradation may include shorter explanations, fewer optional refinements, and reduced secondary recommendation commentary.
- The architecture must avoid dependencies on long-lived in-memory session state so that serverless and single-container deployments remain viable.

## Hosting Constraints
- The deployment model must work in either serverless or single-container form without changing product behavior.
- The request path must not depend on a persistent database for v1 user profiles.
- The system should tolerate upstream OHNY API unavailability without masking failures as successes.

## Future Extensions
- v2 should integrate a paid transit provider through the same travel interface.
- v2 may integrate with an OHNY user profile for preferences or identity, but only with explicit user confirmation.
- v2 may add richer anonymized aggregate analytics without introducing server-side personal profiles.
