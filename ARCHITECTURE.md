# Architecture

Atlas is a modular metadata pipeline. Each stage has one responsibility and
communicates through explicit data contracts.

## High-Level Pipeline

```text
Database
  -> Extractor
  -> Raw Metadata Snapshot
  -> Normalized Metadata Model
  -> Optional Business Knowledge Overlay
  -> Generators
  -> Documentation Artifacts
```

## Core Modules

### Extractors

Extractors connect to a database or read exported metadata files. They produce
structured technical facts such as schemas, tables, columns, data types,
primary keys, foreign keys, indexes, and comments.

Rules:

- Extractors do not render documentation.
- Extractors do not apply business interpretation.
- Extractors should be database-specific behind a common interface.
- The first planned extractor is SQL Server.

### Raw Metadata Snapshot

The raw snapshot preserves source-system facts as faithfully as possible. It is
useful for debugging extractor behavior and for comparing source changes over
time.

Rules:

- Raw snapshots should be deterministic and serializable.
- Raw snapshots should not include credentials or connection secrets.
- Raw snapshots should stay separate from generated documentation.

### Normalized Metadata Model

The normalized model is the central Atlas contract. It converts source-specific
metadata into stable Atlas concepts.

Initial concepts:

- database
- schema
- table
- column
- data type
- nullable flag
- primary key
- foreign key
- index
- relationship
- source comment or description

Rules:

- Generators consume only the normalized model and optional knowledge overlays.
- The model should be easy to validate in tests.
- The model should not contain Turtle-specific fields.

### Business Knowledge Overlay

Business knowledge captures human meaning that is not guaranteed to exist in
the database schema.

Examples:

- business glossary terms
- domain definitions
- stewardship notes
- known caveats
- examples of valid values
- policy or operational context

Rules:

- Business knowledge is separate from technical metadata.
- Missing business knowledge must not block deterministic technical output.
- Future AI enrichment may suggest business knowledge, but humans should be
  able to review and edit it as Markdown.

### Generators

Generators convert normalized metadata into output artifacts.

Planned MVP generators:

- Markdown data dictionary
- DBML schema output
- Mermaid relationship diagrams

Rules:

- Generators do not connect to databases.
- Generators do not mutate the normalized model.
- Generators must produce deterministic output for the same input.
- Generator templates should be simple and reviewable.

### Future AI Enrichment

AI enrichment is a later layer that may suggest descriptions, glossary links,
relationship explanations, and documentation improvements.

Rules:

- AI output must be optional.
- AI output must be reviewable.
- AI output must not replace deterministic extraction and generation.
- AI prompts and generated suggestions should be versionable where practical.

## Planned Package Shape

```text
atlas/
  cli/          Future command-line entry points
  extractor/    Database metadata extraction interfaces and implementations
  parser/       Conversion from raw snapshots to normalized metadata
  generator/    Markdown, DBML, and Mermaid generators
  exporters/    File output helpers
  enrich/       Future AI and human knowledge overlay support
```

The current Sprint 0 task does not implement these modules. The directory names
reserve the intended boundaries.

## Boundary Rules

- Turtle-specific logic belongs only in `examples/turtle`.
- Extractors must not render documentation.
- Generators must not connect to databases.
- Technical metadata must stay separate from business knowledge.
- Deterministic outputs come before AI-assisted outputs.
