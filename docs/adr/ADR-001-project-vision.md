# ADR-001: Project Vision And MVP Shape

## Status

Accepted for Sprint 0.

## Context

Project Atlas needs a clear starting shape before production code is added. The
project vision is broad, but the MVP must remain narrow enough to implement and
test.

The first example case study is Turtle, but Atlas must remain a generic
metadata and documentation toolkit.

## Decision

Atlas will start as a deterministic, documentation-first pipeline:

```text
extract -> normalize -> generate
```

The MVP will focus on:

- SQL Server metadata extraction
- normalized metadata modeling
- Markdown dictionary generation
- DBML generation
- Mermaid relationship diagram generation
- Turtle example case study

AI enrichment is acknowledged as a future capability, but it is not part of the
required MVP pipeline.

## Consequences

Positive:

- The first implementation can be tested with small fixtures.
- Generators can be developed without database access.
- Database-specific behavior is isolated in extractors.
- Turtle can validate the workflow without becoming product logic.

Tradeoffs:

- AI-assisted knowledge generation is deferred.
- Documentation hosting is deferred.
- The first MVP may feel modest, but it should be easier to trust and extend.

## Guardrails

- Extractors do not render documentation.
- Generators do not connect to databases.
- Business knowledge remains separate from technical metadata.
- Turtle-specific logic remains under `examples/turtle`.
