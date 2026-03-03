# Check-In Spec

## Implements Requirements
- REQ-RETR-002
- REQ-RETR-003
- REQ-CHECKIN-001
- REQ-CHECKIN-002
- REQ-CHECKIN-003
- REQ-CHECKIN-004
- REQ-CHECKIN-005
- REQ-CHECKIN-006
- REQ-CHECKIN-007
- REQ-PROXY-001
- REQ-PROXY-002
- REQ-PROXY-003
- REQ-PROXY-004
- REQ-PRIV-001
- REQ-PRIV-002
- REQ-PRIV-005
- REQ-PRIV-006
- REQ-PRIV-007
- REQ-PRIV-008
- REQ-PRIV-009
- REQ-PRIV-010

## Purpose
Define the user-facing and backend-facing behavior for OHNY self check-in at a high level, without locking upstream OHNY API specifics.

## Core Rules
- The check-in path must be retrieval-driven and must not depend on LLM calls for site resolution at submission time.
- The product must support multilingual conversation, but check-in field values must be entered or confirmed in English before submission.
- Every check-in must end with an explicit final confirmation step before the proxy submits.
- The system must never claim success unless the upstream OHNY API confirms success.
- The donation prompt must appear only after confirmed success and must remain optional.

## Required Submission Fields
The exact upstream field schema will be mapped later, but Gate 1 locks these high-level rules:
- A resolved OHNY site is required.
- Any upstream-required identity/contact/party fields are required when missing from device-saved data.
- Party size should be re-confirmed on the first check-in of each day after day one because it may vary day to day.
- Check-in field values must be in English at submission time.

## Optional Inputs
- Device geolocation, when the user allows it
- Accessibility preferences when relevant to saved profile or planning context
- Device-saved repeat-use check-in info, when the user has opted in
- Off-weekend acknowledgment when the user attempts check-in outside OHNY weekend

## Flow 1: `check me in at <site>`
1. The system must resolve the requested site through retrieval.
2. If multiple plausible matches exist, the system must show a short list and require the user to choose.
3. If no confident match exists, the system must:
   - say that it could not confidently identify the site
   - show about 3 to 5 likely or geographically close candidates, never more than 5
   - ask for another hint such as an address fragment or landmark
4. The system must collect only the missing required submission fields.
5. If saved info exists on the device, the system must confirm that it is about to use that saved info and allow the user to switch or forget it.
6. The system must present a final confirmation showing the resolved site and all required submitted fields.
7. After confirmation, the proxy must submit an idempotent request to the OHNY API.

## Flow 2: `check me in`
1. The system must use geolocation first when available.
2. The system must present the matched nearby site and ask the user to confirm it.
3. If geolocation suggests one site but the user’s typed intent points to another, the system must ask the user to confirm which is correct.
4. If geolocation is denied, unavailable, or too imprecise, the system must fall back to retrieval-driven prompts for:
   - site name
   - address fragment
   - nearby landmark
5. The system must collect only the missing required submission fields.
6. The system must present the same explicit final confirmation before submission.
7. After confirmation, the proxy must submit an idempotent request to the OHNY API.

## Consent And Save Rules
- The system must ask for explicit opt-in before saving check-in information on the device.
- The opt-in prompt must explain that the data is saved on this device only.
- The initial save prompt should mention that the user can later say `forget my info`.
- One-time save consent must remain in effect until revoked or materially changed.
- At the start of a new OHNY season, if prior saved check-in data still exists, the system should ask whether it is still valid before reusing it.

## Geolocation Rules
- The product must ask for geolocation on first page load and briefly explain the benefit.
- If denied, the system must continue without blocking planning or check-in.
- If location is requested again later, the system must explain why it would materially help the current task.
- If a second location ask is denied on the same day, the system must not ask again that day.
- The next day may allow a future re-ask; the next OHNY season should reset the denial memory for first-load prompting.

## Off-Weekend Behavior
- If a user attempts check-in outside OHNY weekend, the system must warn the user before final confirmation that the attempt may fail.
- The system should still attempt the submission if the user confirms.
- If the submission fails outside OHNY weekend, the system should explain that the upstream check-in API may be unavailable because the event window is not active.

## Idempotency And Abuse Controls
- The proxy must apply idempotency safeguards so the same user action is not recorded multiple times accidentally.
- The proxy must apply baseline rate limiting.
- If rate limiting engages, the user must receive a clear temporary-limit message and a retry path.
- The flow should avoid unnecessary friction such as login or CAPTCHA by default.

## Required User-Facing Controls
- `Forget my info` must clear locally stored check-in/profile data on that device.
- The product must expose this control in settings/options and support it via chat commands.
- Planning-preference reset must be a separate control from check-in info deletion.

## Error States
- Ambiguous site: require user choice from a short list.
- No confident match: show likely candidates and ask for another hint.
- Missing required field: ask only for the missing field and resume.
- Upstream failure: clearly state that check-in was not completed and offer retry.
- Rate limit response: clearly state the temporary limit and invite retry.
- Geo denied/unavailable: continue with named-site or location-hint fallback.
