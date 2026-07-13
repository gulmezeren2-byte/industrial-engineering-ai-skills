# Data Contract

> One per data source. Version it with the analysis; when the source changes, the contract changes first.

**Source:** <!-- system, export path/query, owner -->
**Refresh cadence:** <!-- and what "as of" timestamp means -->
**Grain:** <!-- one row = ? -->

## Columns

| Column | Type | Meaning | Quality checks |
|--------|------|---------|----------------|
| | | | <!-- e.g. not null, unique, within range, matches reference list --> |

## Quality gate results (this delivery)

| Check | Result | Action taken |
|-------|--------|--------------|
| Duplicated rows | | kept / removed (count reported in output) |
| Missing calendar days | | |
| Impossible values | | |
| Rows outside period | | |

## Known issues and quirks

<!-- The tribal knowledge: "region codes changed in March", "returns appear as negative qty". This section is why the contract exists. -->
