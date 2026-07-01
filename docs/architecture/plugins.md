# Plugins

Atlas should support extension points without overbuilding the first MVP.

## Initial Plugin Boundary

The first practical plugin boundary is the database extractor.

Each extractor should be responsible for one source family, such as SQL Server.
It should produce a raw metadata snapshot that can be normalized by Atlas.

## Future Extension Points

Potential future plugin types:

- database extractors
- metadata importers for exported files
- documentation generators
- business knowledge importers
- AI enrichment providers

These should be added only when the core interfaces are proven by the MVP.

## Rules

- Plugins must not bypass the normalized metadata model.
- Extractor plugins must not render documentation.
- Generator plugins must not connect to databases.
- Plugins must declare their inputs and outputs clearly.
- Example-specific plugins should live with the example until they are proven
  generic.
