# Data Sources

## Related assumptions
- /Users/Dmitry_Naidionov/Projects/OHNY-chatbot-codex/spec/assumptions.md


## Primary Dataset
Source file: `ohny-list-wellformed.json` (local example data).

## Event Record Fields
- `id` (int)
- `title` (string)
- `link` (string)
- `featured_image` (object)
- `address` (list of strings)
- `location` (object)
- `dates` (list of objects)
- `reservation` (bool)
- `ticketed_sessions` (dict keyed by date or empty list)
- `sold_out` (bool)
- `lottery` (bool)
- `children_welcome` (bool)
- `virtual` (bool)
- `wheelchair_accessible` (bool)
- `canceled` (bool)
- `terms` (object)

## Location Fields
- `address`
- `city`
- `zip`
- `lat`
- `lng`

## Dates Fields
- `date` (string label)
- `start` (string time)
- `end` (string time)

## Terms Taxonomy Groups
- `borough`
- `neighborhood`
- `format`
- `virtual`
- `access`
- `attendance`

## Featured Image Fields
- `thumbnail`
- `medium`
- `large`
- `caption`
- `alt`

## Normalization Notes
- `ticketed_sessions` can be a dictionary keyed by date or an empty list.
- `dates` can include empty strings and need cleaning for scheduling.
- `address` is a list and may include notes or instructions.
- Terms arrays may be empty.

## Freshness and Update Cadence
- Dataset appears to represent a yearly snapshot.
- MVP assumes periodic refresh rather than real-time updates.

## Open questions
- What is the intended update cadence for the event dataset?
- Are there additional OHNY data sources beyond the event list?