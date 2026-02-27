# Acceptance Criteria

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## Discovery
- The assistant can filter events by borough, neighborhood, accessibility, virtual, and children welcome.
- Results include title, date range or time window, and access constraints.
- Users can ask follow-up filters without restarting the search.

## Scheduling
- The assistant can suggest a feasible order of events for a given day.
- Suggestions avoid obvious conflicts in time windows.
- The assistant flags sold-out or lottery-only events clearly.

## Routing
- The assistant provides travel guidance between consecutive events.
- If travel time is uncertain, the assistant states assumptions or asks for clarification.

## Trivia and History
- Each event summary can include a short historical or architectural fact.
- The assistant avoids making unverifiable claims and uses safe phrasing.

## Yearlong Navigation
- The assistant can return upcoming or recent events outside OHNY weekend.
- Users can ask for future events by month or season.

## Resources
- The assistant can summarize OHNY policies such as reservations or ticketing.
- The assistant can direct users to OHNY site resources when needed.

## Open questions
- What is the minimum acceptable success rate for schedule feasibility?
- Should we require explicit user confirmation before delivering a final itinerary?