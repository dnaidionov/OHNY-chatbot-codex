# MVP Scope

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## In Scope
- Weekend event discovery by theme, borough, neighborhood, format, and accessibility.
- Schedule assembly for a day or weekend using event time windows.
- Routing guidance between selected events using travel-time estimates and constraints.
- Trivia and history snippets tied to places or neighborhoods.
- Yearlong event navigation that mirrors weekend discovery but without schedule optimization.
- Site and resources info such as tickets, policies, volunteer info, and FAQs (as available in the dataset or linked resources).
- Clear handling of reservation, ticketed sessions, lottery, sold-out, and canceled events.

## Supported Inputs
- Natural language questions, multi-constraint requests, and follow-up clarifications.
- Filters: date, time window, borough, neighborhood, wheelchair accessibility, virtual, children welcome, sold-out status.

## Supported Outputs
- Ranked lists of events with short reasoning.
- Proposed itineraries with time order and travel notes.
- Event detail summaries including dates, location, access constraints, and links.

## Out of Scope
- Payments, ticket purchasing, or reservations.
- Real-time transit integrations.
- Personalized accounts, saved favorites, or login.

## Open questions
- Should the MVP prioritize itinerary-building or general discovery when both are requested?
- Are there specific “official resources” that must be treated as authoritative above others?