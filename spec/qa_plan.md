# QA Plan

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## Test Categories
- Discovery filters
- Scheduling and conflict detection
- Routing guidance
- Trivia/history responses
- Yearlong navigation
- Resource info retrieval

## Test Fixtures Based on JSON
- Events with `reservation: true` and `sold_out: true`.
- Events with `children_welcome: true` and `wheelchair_accessible: true`.
- Events with `virtual: true` and no physical address.
- Events with empty `dates` strings.
- Events with `ticketed_sessions` dictionary keyed by date.

## Example Scenarios
- Weekend search for Manhattan Saturday afternoon with accessibility.
- Build itinerary with two events in different boroughs and check for travel warnings.
- Request trivia for an event with minimal terms metadata.
- Filter for non-sold-out events only.

## Regression Checklist
- All filters return at least one result when data exists.
- Itinerary output orders events chronologically.
- Sold-out and lottery events are flagged.

## Open questions
- What is the acceptable tolerance for time-window overlap in schedules?
- Should QA include manual reviews of trivia accuracy?