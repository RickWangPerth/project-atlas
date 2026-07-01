# Design Principles

## Documentation First

Atlas should explain its intent before it hides behavior inside code. Important
workflow, architecture, and data model decisions should be written down in
Markdown.

## Deterministic By Default

For the same input, Atlas should produce the same output. Ordering, formatting,
and filenames should be predictable so generated documentation can be reviewed
in version control.

## Modular Boundaries

Each module should do one job:

- extractors collect technical metadata
- parsers normalize metadata
- generators render artifacts
- enrichment layers add optional human or AI context

## Markdown Preferred

Markdown is the primary documentation format because it is easy to review,
version, diff, and publish.

## Human Knowledge And Technical Metadata Are Different

Database structure can describe what exists. Business knowledge explains what it
means. Atlas should support both without mixing their source of truth.

## AI As Enrichment, Not Foundation

AI may later help suggest descriptions, summaries, and glossary links. The core
pipeline must still work without AI services.

## Examples Must Not Become Product Logic

The Turtle example should validate Atlas, not define Atlas. Any assumptions
specific to Turtle belong under `examples/turtle`.
