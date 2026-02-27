# Ranking and Routing

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## Ranking Inputs
- User constraints: date, time window, borough, neighborhood, accessibility, virtual.
- Availability constraints: `sold_out`, `lottery`, `reservation`, `canceled`.
- Relevance signals: terms taxonomy, format, and proximity to user preference.

## Ranking Rules
- Exclude canceled events unless user explicitly asks.
- Down-rank sold-out events and mark them clearly.
- Up-rank events that match all explicit constraints.
- Tie-break by proximity and schedule fit.

## Scheduling Constraints
- Use `dates` and `ticketed_sessions` if available.
- If `ticketed_sessions` is empty, rely on `dates` strings.
- Avoid overlapping event windows when building itineraries.

## Routing Guidance
- Provide approximate travel guidance based on borough and neighborhood proximity.
- If lat/lng exists, use it for more precise routing estimates.
- Flag uncertainty when times or locations are missing.

## Conflict Handling
- If time windows conflict, propose alternative ordering or ask user to pick.
- If travel time is likely too long, suggest closer alternatives.

## Open questions
- Should sold-out events be excluded entirely or remain visible with warnings?
- How aggressive should time-window conflict resolution be in MVP?