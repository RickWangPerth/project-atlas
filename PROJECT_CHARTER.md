# Project Charter

## Vision

Transform Databases into Human Knowledge.

Atlas exists to help teams understand the systems they already run by turning
database structure into clear, deterministic documentation and reusable
knowledge artifacts.

## Mission

Atlas will extract database metadata, normalize it into a stable internal
model, and generate Markdown-first documentation that can be reviewed, versioned,
and improved over time.

## Goals

- Build a deterministic metadata pipeline before adding AI features.
- Keep extractors, models, generators, and enrichment as separate modules.
- Produce useful Markdown documentation as the primary output.
- Support DBML and Mermaid as portable secondary outputs.
- Make example case studies useful without letting them shape core logic.
- Prepare for an open-source contribution model with clear issues, tests, and
  design notes.

## Non-Goals

- Atlas will not write to source databases.
- Atlas will not generate documentation directly from extractor code.
- Atlas will not require AI services for MVP output.
- Atlas will not hardcode Turtle-specific rules into core modules.
- Atlas will not treat business definitions as database metadata.

## First Case Study

The first case study is the Turtle example under `examples/turtle`.

That example is a proving ground for the Atlas workflow, not a special case in
the product architecture. Any Turtle-specific metadata exports, notes,
dictionaries, or generated diagrams must stay inside `examples/turtle`.

## Success Criteria For Sprint 0

- The project has a serious, coherent documentation baseline.
- The architecture describes clear module responsibilities.
- The MVP roadmap is small enough to implement incrementally.
- Backlog items use stable Atlas issue IDs.
- Future implementation work has clear quality expectations.
