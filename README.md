# Project Atlas

> Transform Databases into Human Knowledge.

Project Atlas is a documentation-first toolkit for turning database metadata
into human-readable, reviewable knowledge assets.

Atlas starts with deterministic extraction and generation:

- database metadata extraction
- a normalized metadata model
- Markdown data dictionary generation
- DBML generation
- Mermaid relationship diagrams
- optional future AI enrichment

The project is currently in Sprint 0. The repository is being shaped before
production code is added.

## Why Atlas Exists

Databases often contain the most reliable description of an organization's
systems, but that knowledge is locked inside schemas, constraints, naming
patterns, and scattered tribal context.

Atlas aims to make that knowledge visible without coupling documentation to any
single database, customer, or example dataset.

## MVP Scope

The first useful version should support this workflow:

1. Extract technical metadata from SQL Server.
2. Normalize it into an Atlas metadata model.
3. Generate a Markdown data dictionary.
4. Generate DBML for schema review and external tooling.
5. Generate Mermaid diagrams for relationships.
6. Demonstrate the workflow with the Turtle example under `examples/turtle`.

Out of scope for the MVP:

- production AI enrichment
- live documentation hosting
- database write operations
- hardcoded Turtle-specific behavior in core Atlas modules
- generator code that connects directly to databases

## Repository Layout

```text
atlas/                  Future Python package modules
docs/                   Architecture, concepts, ADRs, and planning
docs/backlog.md         Initial MVP backlog
examples/turtle/        Example case study only; no core logic lives here
tests/                  Future pytest test suite
templates/              Future deterministic output templates
README.md               Project overview
PROJECT_CHARTER.md      Project goals, scope, and principles
ARCHITECTURE.md         System architecture plan
ROADMAP.md              MVP roadmap
JOBLOG.md               Work log
```

## Architecture Principles

- Extractors read database metadata and produce structured facts.
- The normalized metadata model is the contract between extractors and
  generators.
- Generators render documentation artifacts from normalized metadata only.
- Business knowledge is stored separately from technical metadata.
- AI enrichment is an optional future layer, not part of the deterministic
  MVP pipeline.

## Development Status

No production implementation is expected yet. Sprint 0 is focused on project
shape, documentation quality, and a clean MVP plan.

When implementation begins, the intended Python workflow is:

```bash
uv run --extra dev pytest
uv run --extra dev mypy src
uv run --extra dev ruff check .
```

These commands are targets for the upcoming implementation phase, not a claim
that the full Python package already exists.
