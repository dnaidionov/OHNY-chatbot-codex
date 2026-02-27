# Conversation Flows

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## High-Level Intent Routing
- Discover events
- Build itinerary
- Get routing guidance
- Learn trivia or history
- Navigate yearlong events
- Find OHNY resources

## Example Flow: Weekend Discovery to Itinerary
1. User asks for events by time and location.
2. Assistant returns ranked list with key constraints.
3. Assistant asks if the user wants an itinerary.
4. User chooses two or more events.
5. Assistant proposes order, time windows, and travel notes.

## Example Flow: Accessibility Filter
1. User asks for wheelchair accessible events.
2. Assistant confirms if virtual is acceptable.
3. Assistant returns list and highlights accessibility details.

## Example Flow: Yearlong Navigation
1. User asks for events in November.
2. Assistant clarifies date range if needed.
3. Assistant lists events and offers filters.

## Fallbacks and Clarifications
- If date is missing, ask for weekend day or time window.
- If location is broad, ask borough or neighborhood preference.
- If data is missing, acknowledge and provide the closest available info.

## Open questions
- Should itinerary creation require explicit confirmation every time?
- What tone should the assistant use for fallback prompts: concise or conversational?