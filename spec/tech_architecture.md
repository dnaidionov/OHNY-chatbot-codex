# Tech Architecture

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## Overview
A conversational layer on top of OHNY event data that supports retrieval, filtering, and light planning.

## Components
- Data ingestion and normalization for OHNY event records.
- Retrieval layer for filtering and ranking.
- Conversation orchestrator for intent routing and follow-ups.
- Response composer for summaries, schedules, and resource info.
- Telemetry pipeline for analytics events.

## Data Flow
- User query → intent routing → retrieval and ranking → response composition → analytics logging.

## Storage
- Event data store (snapshot with periodic refresh).
- Taxonomy cache for borough, neighborhood, and format terms.

## Operational Considerations
- Version datasets by year to support yearlong navigation.
- Maintain consistent identifiers for event detail links.

## Open questions
- Do we need a separate taxonomy service or static config is enough for MVP?
- What is the preferred hosting environment for the data store?