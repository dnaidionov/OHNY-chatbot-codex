# System Contract

Atomic requirements are defined as individual files under `/spec/requirements/` and referenced by REQ-ID.

## Implements Requirements
- REQ-PLAN-001
- REQ-PLAN-002
- REQ-PLAN-003
- REQ-RETR-001
- REQ-RETR-002
- REQ-RETR-003
- REQ-RETR-004
- REQ-TRAVEL-002
- REQ-ORCH-001
- REQ-ORCH-002
- REQ-ORCH-003
- REQ-ORCH-004
- REQ-ORCH-006
- REQ-CHECKIN-001
- REQ-CHECKIN-002
- REQ-CHECKIN-003
- REQ-CHECKIN-004
- REQ-CHECKIN-005
- REQ-CHECKIN-007
- REQ-PROXY-001
- REQ-PROXY-003
- REQ-PROXY-004
- REQ-PRIV-001
- REQ-PRIV-002
- REQ-PRIV-003
- REQ-PRIV-004
- REQ-PRIV-006
- REQ-PRIV-007
- REQ-PRIV-008
- REQ-PRIV-009
- REQ-PRIV-010
- REQ-NFR-001
- REQ-NFR-002
- REQ-NFR-003
- REQ-NFR-004
- REQ-NFR-005

## Purpose
Describe system boundaries, supported capabilities, privacy/consent behavior, failure handling, and non-functional targets for the OHNY chatbot.

## Actors And Boundaries
- `User`: asks for recommendations, site information, check-in, deletion, and preference changes.
- `Chat UI`: renders the conversation, prompts for permission, stores consented local data, and exposes settings/options.
- `Conversation Orchestrator`: selects the appropriate flow and asks minimal clarifying questions.
- `Retrieval Service`: resolves OHNY sites and candidate matches from curated public data.
- `Planner Service`: generates walking-only plans and recommendation sets.
- `Check-In Proxy`: validates and forwards check-in requests to the existing OHNY API.
- `Existing OHNY API`: receives check-in submissions; endpoint and auth details are intentionally out of scope for Gate 1.

## Supported Capabilities
The system must support:
- multilingual conversation in the language determined by the model experience
- English confirmation of check-in field values before submission
- greeting plus 3 to 5 example prompts on initial load
- planning and recommendation requests
- site lookup and disambiguation
- check-in by named site
- check-in by current location
- `forget my info` for locally saved check-in/profile data
- separate reset of saved planning preferences
- explicit handling of unsupported requests with a redirect to the closest supported action

## Supported User Commands And Examples
- Planning:
  - `What should I see near SoHo?`
  - `I have two hours and like architecture.`
  - `Find a few places near me.`
- Check-in:
  - `Check me in at the Woolworth Building.`
  - `Check me in.`
  - `Use my saved info.`
- Privacy/settings:
  - `Forget my info.`
  - `Reset my planning preferences.`
  - `Do you remember my accessibility needs?`
- Unsupported-but-redirected:
  - Requests for transit routing should produce walking-only recommendations plus a suggestion to use an external maps app for non-walking directions.

## Command Semantics
- The system must ask for geolocation on first page load and briefly explain the benefit.
- If geolocation is denied, the system must continue normally.
- If geolocation is denied a second time on the same day, the system must not ask again that day.
- The next day and the next OHNY season may reset the location-denial memory and allow a new ask.
- The first check-in of each day after day one should re-confirm party size.
- At the start of a new OHNY season, the system should say that saved info from the prior season still exists and ask whether it is still valid.
- When saved info exists on a device, the system must confirm that it is about to use that saved info and offer a path to switch or forget it.

## Module Responsibilities
- UI must own:
  - multilingual rendering
  - styling aligned to `ohny.org`
  - greeting and example prompts
  - local consent prompts and settings affordances
- Orchestrator must own:
  - intent routing
  - clarification policy
  - unsupported-request redirection
  - explicit confirmation steps
- Retrieval must own:
  - site matching
  - ambiguity handling
  - nearby candidate generation
- Planner must own:
  - walking-only recommendation generation
  - interest fit
  - feasible versus aspirational labeling
- Proxy must own:
  - validation of required submission fields
  - idempotency
  - rate limiting
  - forwarding to the upstream OHNY API

## Privacy And Consent Model
- The system must not create server-side user profiles in v1.
- The system must ask for explicit opt-in before saving check-in information on the device.
- The opt-in prompt must clearly say that the information is saved on this device only, not in a server-side profile.
- The initial save prompt should mention that the user can later use `forget my info`.
- One-time device consent should remain valid until revoked or materially changed.
- Check-in/profile deletion and planning-preference reset must be separate controls.
- The system may remember planning interests, accessibility preferences, and lightweight convenience settings on-device.
- The system may remember user-entered repeat-use check-in fields on-device after consent.
- The system must not persist highly sensitive free-form notes by default.

## Check-In Contract
- Check-in site resolution must be retrieval-driven.
- The check-in path must not rely on an LLM call to resolve the site at submission time.
- Required fields must be collected incrementally; the system must ask only for missing required items.
- If multiple plausible site matches exist, the system must present a short choice list and require user selection.
- If no confident site match exists, the system must say so, offer up to 5 likely or geographically close candidates, and ask for another hint.
- The final confirmation step must show:
  - resolved site
  - all required submitted fields
  - saved-info usage notice when relevant
- Donation prompting must happen only after confirmed successful check-in and must remain optional.

## Failure Modes And Fallback Behaviors
### Geolocation Denied Or Unavailable
- The system must continue with named-site or location-hint prompts.
- For `near me` planning, the system must ask for a neighborhood, landmark, or address fragment.

### Ambiguous Site
- The system must not guess.
- The system must show a short disambiguation list and ask the user to choose.

### Conflict Between Typed Intent And Geolocation
- The system must ask the user to confirm which site is correct.

### Upstream OHNY API Slow Or Down
- The system must fail clearly and must not imply a successful check-in when none occurred.
- The system should offer a retry path.
- If the attempt occurs outside OHNY weekend and submission fails, the system should inform the user that the upstream check-in API may be unavailable because it is outside the event window.

### Rate Limiting Or Burst Protection Triggered
- The system must return a clear temporary-limit response and invite a short retry.
- The system must not silently drop the request or fake success.

### Unsupported Requests
- The system must state the limitation and redirect to the closest supported action.

## External Dependencies
- Curated OHNY public site/event data for retrieval and planning
- Existing OHNY check-in API reached through the thin proxy
- Device geolocation APIs when permitted by the user
- External maps applications for non-walking travel directions outside v1 scope

## Non-Functional Requirements
- The system must prioritize fast interactions over verbose responses under load.
- The system should target a response time of a few seconds for the large majority of planning and check-in turns during normal operation.
- The system must preserve core planning and check-in flows under extreme OHNY burst traffic by trimming non-essential conversational richness first.
- The system must support deployment as serverless functions or as a single container without changing product semantics.
- The system must provide baseline caching of public site data and baseline rate limiting.
- The system should be highly available during OHNY weekend, with graceful degradation preferred over hard failure whenever core flows can still proceed safely.
