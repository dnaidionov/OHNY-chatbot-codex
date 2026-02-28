# Check-In Spec

## Purpose
Define the user-facing and backend-facing behavior for self check-in at OHNY sites.

## Required Fields
- `site`
- `zip` or `country`

## Optional Fields
- `geolocation`
- `device_timestamp`
- `user_confirmation`
- `notes`
- `consent_state`
- `checkin_source`

## User Flow 1
### TODO "check me in at <site>"
- Resolve the requested site.
- Ask for missing `zip` or `country` if needed.
- Confirm consent and submit an idempotent check-in request.

## User Flow 2
### TODO "check me in"
- Use geolocation when available.
- Present the matched site for confirmation.
- Confirm consent and submit an idempotent check-in request.

## TODO Idempotency Rules

## TODO Consent Rules

## TODO Error States
