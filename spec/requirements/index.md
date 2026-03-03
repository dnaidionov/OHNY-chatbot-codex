# Requirements Index

This index tracks the current atomic requirements catalog and its status.

| ID | Title | Priority | Status (Proposed/Approved/Implemented/Deprecated) | Owner (Agent/Role) | Linked EVAL IDs | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| REQ-CHECKIN-001 | Support retrieval-driven named-site check-in | P0 | Proposed | Check-In Flow | TBD | Primary named-site entry flow. |
| REQ-CHECKIN-002 | Support unnamed geolocation-first check-in | P0 | Proposed | Check-In Flow | TBD | Falls back when geo is denied or weak. |
| REQ-CHECKIN-003 | Collect only missing required submission fields | P0 | Proposed | Check-In Flow | TBD | Low-friction field collection. |
| REQ-CHECKIN-004 | Reconfirm party size on the first check-in of each day after day one | P1 | Proposed | Check-In Flow | TBD | Daily variation safeguard. |
| REQ-CHECKIN-005 | Require explicit final confirmation before submission | P0 | Proposed | Check-In Flow | TBD | Shows site and required fields. |
| REQ-CHECKIN-006 | Confirm submission values in English | P0 | Proposed | Check-In Flow | TBD | Multilingual chat with English submission values. |
| REQ-CHECKIN-007 | Handle off-weekend check-in attempts explicitly | P1 | Proposed | Check-In Flow | TBD | Warning plus honest failure messaging. |
| REQ-NFR-001 | Keep normal interactions to a few seconds for the large majority of turns | P1 | Proposed | Platform Performance | TBD | Fast interactions over verbosity. |
| REQ-NFR-002 | Degrade gracefully under burst traffic | P0 | Proposed | Platform Performance | TBD | Preserve core flows first. |
| REQ-NFR-003 | Cache or precompute public site data for core flows | P0 | Proposed | Platform Performance | TBD | Supports retrieval and planning scale. |
| REQ-NFR-004 | Preserve product behavior across serverless and single-container deployment | P0 | Proposed | Platform Architecture | TBD | No long-lived state in request path. |
| REQ-NFR-005 | Prefer graceful availability during OHNY weekend | P1 | Proposed | Platform Operations | TBD | Degraded service over collapse when safe. |
| REQ-OPS-001 | Track the primary check-in completion metric with required segments | P1 | Proposed | Product Analytics | TBD | North-star metric instrumentation. |
| REQ-OPS-002 | Collect aggregate planning, retrieval, privacy, and operational guardrail metrics | P1 | Proposed | Product Analytics | TBD | Aggregate-only analytics scope. |
| REQ-ORCH-001 | Classify requests into supported flow types | P0 | Proposed | Conversation Orchestrator | TBD | Planning, retrieval, check-in, settings, unsupported. |
| REQ-ORCH-002 | Ask only the minimum clarifying questions needed | P0 | Proposed | Conversation Orchestrator | TBD | Minimizes friction and model use. |
| REQ-ORCH-003 | Render an onboarding greeting with example prompts | P1 | Proposed | Chat UI | TBD | Initial greeting, intro, and 3 to 5 prompts. |
| REQ-ORCH-004 | Redirect unsupported requests to the closest supported action | P0 | Proposed | Conversation Orchestrator | TBD | Explicit limitation with recovery path. |
| REQ-ORCH-005 | Close final recommendations with a volunteer reminder | P2 | Proposed | Conversation Orchestrator | TBD | Brief planning-only reminder. |
| REQ-ORCH-006 | Support multilingual conversation rendering | P0 | Proposed | Chat UI | TBD | Multilingual chat outside submission values. |
| REQ-PLAN-001 | Generate walking-only recommendation sets | P0 | Proposed | Planner Service | TBD | Uses retrieval plus user constraints. |
| REQ-PLAN-002 | Label recommendation feasibility explicitly | P0 | Proposed | Planner Service | TBD | Feasible, over-window, or aspirational. |
| REQ-PLAN-003 | Rank planning results by interest fit with visible time tradeoffs | P1 | Proposed | Planner Service | TBD | Avoids misleading default itineraries. |
| REQ-PRIV-001 | Require explicit device-only save consent | P0 | Proposed | Privacy And UX | TBD | Local-save opt-in with device-only wording. |
| REQ-PRIV-002 | Keep local save consent in effect until revoked or materially changed | P1 | Proposed | Privacy And UX | TBD | Durable consent model. |
| REQ-PRIV-003 | Limit local persistence to useful low-risk data | P0 | Proposed | Privacy And UX | TBD | Excludes sensitive or unnecessary fields. |
| REQ-PRIV-004 | Prohibit server-side personal profiles in v1 | P0 | Proposed | Privacy And UX | TBD | Hard v1 privacy boundary. |
| REQ-PRIV-005 | Support forgetting local check-in and profile data | P0 | Proposed | Privacy And UX | TBD | `forget my info` and settings control. |
| REQ-PRIV-006 | Keep planning-preference reset separate from profile deletion | P0 | Proposed | Privacy And UX | TBD | Independent local controls. |
| REQ-PRIV-007 | Confirm reuse of saved local check-in info | P0 | Proposed | Privacy And UX | TBD | Reuse notice with switch or forget path. |
| REQ-PRIV-008 | Revalidate prior-season saved check-in info before reuse | P1 | Proposed | Privacy And UX | TBD | Seasonal validity check. |
| REQ-PRIV-009 | Govern geolocation prompting and denial memory | P0 | Proposed | Privacy And UX | TBD | Optional geo with bounded re-asks. |
| REQ-PRIV-010 | Minimize location data sent to the server during check-in | P1 | Proposed | Privacy And UX | TBD | Send only needed location-related data. |
| REQ-PROXY-001 | Forward validated check-ins through a thin backend proxy | P0 | Proposed | Check-In Proxy | TBD | Validates then forwards upstream. |
| REQ-PROXY-002 | Enforce idempotent check-in submission | P0 | Proposed | Check-In Proxy | TBD | Prevents accidental duplicates. |
| REQ-PROXY-003 | Apply baseline rate limiting with a retry path | P0 | Proposed | Check-In Proxy | TBD | Temporary-limit response required. |
| REQ-PROXY-004 | Propagate upstream failures without false success | P0 | Proposed | Check-In Proxy | TBD | Never imply success without confirmation. |
| REQ-RETR-001 | Resolve OHNY sites from curated data | P0 | Proposed | Retrieval Service | TBD | Canonical site resolution source. |
| REQ-RETR-002 | Require explicit disambiguation for ambiguous site matches | P0 | Proposed | Retrieval Service | TBD | No guessing on multiple matches. |
| REQ-RETR-003 | Recover from no confident site match with bounded candidates | P0 | Proposed | Retrieval Service | TBD | Show up to 5 candidates and ask for hint. |
| REQ-RETR-004 | Provide nearby candidates for location-based flows | P1 | Proposed | Retrieval Service | TBD | Supports `near me` and unnamed check-in. |
| REQ-TRAVEL-001 | Expose a mode-aware travel evaluation contract | P1 | Proposed | Travel Interface | TBD | Stable interface for future providers. |
| REQ-TRAVEL-002 | Restrict v1 travel evaluation to walking | P0 | Proposed | Planner Service | TBD | External maps for non-walking. |
