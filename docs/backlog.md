# Backlog

The initial backlog defines the MVP path. Items are intentionally small and
documentation-first so the project can evolve through reviewable increments.

## ATLAS-001 Project bootstrap

Establish the repository baseline.

Acceptance criteria:

- README explains the vision, MVP scope, and repository layout.
- Architecture documentation defines extractor, model, generator, and
  enrichment boundaries.
- Roadmap lists the MVP work in implementation order.
- Development guidance describes expected tests and quality checks.
- Turtle is documented as an example only.

## ATLAS-002 SQL Server metadata extractor

Build the first database metadata extractor.

Acceptance criteria:

- Extractor reads SQL Server metadata without rendering documentation.
- Raw snapshot includes schemas, tables, columns, data types, nullability,
  primary keys, foreign keys, and required index metadata.
- Credentials are never serialized into snapshots or logs.
- Unit tests cover mapping of representative SQL Server metadata rows.

## ATLAS-003 Normalized metadata model

Define the stable Atlas metadata contract.

Acceptance criteria:

- Model represents database, schema, table, column, key, index, and
  relationship concepts.
- Model can be validated from fixture data.
- Model serialization is deterministic.
- No Turtle-specific fields are present in the core model.

## ATLAS-004 Markdown dictionary generator

Generate Markdown data dictionaries from normalized metadata.

Acceptance criteria:

- Generator consumes normalized metadata, not a database connection.
- Output includes database, schema, table, column, key, and relationship
  sections.
- Output ordering is deterministic.
- Tests compare generated Markdown against approved fixtures.

## ATLAS-005 DBML generator

Generate DBML from normalized metadata.

Acceptance criteria:

- Generator emits tables, columns, keys, and references.
- Output is deterministic.
- Generator does not connect to databases.
- Tests cover representative relationships and nullable columns.

## ATLAS-006 Mermaid relationship generator

Generate Mermaid relationship diagrams from normalized metadata.

Acceptance criteria:

- Generator emits valid Mermaid entity relationship diagrams.
- Node and edge ordering is deterministic.
- Diagram output can be embedded in Markdown.
- Tests cover one-to-many and optional relationships.

## ATLAS-007 Turtle example case study

Use the Turtle example to prove the MVP workflow.

Acceptance criteria:

- Example inputs live under `examples/turtle/metadata`.
- Example generated Markdown lives under `examples/turtle/dictionary`.
- Example generated diagrams live under `examples/turtle/diagrams`.
- No Turtle-specific logic is added to core Atlas modules.
