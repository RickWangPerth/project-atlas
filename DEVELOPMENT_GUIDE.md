# Development Guide

This guide describes how Atlas should be developed once production code starts.
Sprint 0 is documentation and planning only.

## Repository Conventions

- Keep project documentation in Markdown.
- Keep architectural decisions in `docs/adr`.
- Keep concept documentation in `docs/concepts`.
- Keep example-specific material under `examples/<name>`.
- Keep future Python package code under `atlas`.
- Keep future automated tests under `tests`.

## Module Boundaries

### Extractors

Extractors are responsible for reading metadata from a source.

They may:

- connect to a database
- read exported metadata files
- produce raw metadata snapshots

They must not:

- render Markdown, DBML, or Mermaid
- apply Turtle-specific logic
- infer business definitions
- log secrets or connection strings

### Parsers And Normalizers

Parsers convert raw source metadata into the Atlas normalized metadata model.

They may:

- map database-specific concepts into Atlas concepts
- validate required fields
- produce deterministic serialized model files

They must not:

- connect to databases
- render documentation
- mix business glossary content into technical metadata fields

### Generators

Generators render output artifacts from normalized metadata.

They may:

- generate Markdown data dictionaries
- generate DBML
- generate Mermaid diagrams
- read optional business knowledge overlays

They must not:

- connect to databases
- mutate source metadata
- depend on a specific example dataset

## Future Python Tooling

Atlas should be prepared for a small Python implementation using `uv`, `pytest`,
`mypy`, `ruff`, and a CLI entry point.

Target checks:

```bash
uv run --extra dev pytest
uv run --extra dev mypy src
uv run --extra dev ruff check .
```

Do not add production abstractions before the first extractor, model, and
generator contracts need them.

## Fixture Guidance

Prefer small synthetic fixtures for core tests. Real or domain-specific example
exports should stay under `examples/<name>` and must not contain secrets.

## Security Guidance

- Never commit credentials, tokens, private keys, or `.env` files.
- Never print database connection strings in logs.
- Keep raw metadata exports reviewable before committing them.
- Treat production configuration changes as explicit, reviewed work.
