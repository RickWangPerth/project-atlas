# Architecture

Atlas is a modular knowledge governance pipeline. Each stage has one
responsibility and communicates through explicit data contracts.

## High-Level Pipeline

Atlas V3 governs Knowledge Candidates before they become Knowledge Packs.

```text
Knowledge Candidate
  -> Candidate Validation
  -> Review Workflow
  -> Approval / Rejection / Repair Request
  -> Versioned Knowledge Pack
  -> Publication Manifest
  -> Audit Trail
```

Atlas still supports deterministic database documentation, but database metadata
is now one candidate source rather than the whole product boundary.

## Candidate Sources

```text
Athena Compiler
  -> candidates from static knowledge

Athena Knowledge Harvest
  -> candidates from lessons, decisions, patterns, bugs, PRs, meetings, reflection

Manual Governance Input
  -> reviewer notes, repair notes, approval records
```

## Core Modules

### Candidate Intake

Candidate Intake accepts pre-governance artifacts from Athena or manual review
workflows.

Initial candidate types:

- concept;
- glossary term;
- rule;
- relationship;
- workflow note;
- lesson;
- decision;
- pattern;
- caveat;
- repair note;
- database metadata item.

Rules:

- Intake does not approve knowledge.
- Intake must preserve source, provenance, confidence, and uncertainty.
- Intake should validate structure before review.
- Intake should reject credentials, secrets, or unsafe runtime-only data.

### Candidate Validation

Candidate Validation checks whether a candidate is reviewable.

Validation should check:

- required metadata exists;
- evidence or source context is present;
- candidate type is supported;
- lifecycle state is valid;
- destination package or concept is declared when applicable;
- duplicate or conflicting candidates are flagged.

### Review Workflow

Review Workflow records human decisions.

Possible outcomes:

```text
approve
reject
request-repair
needs-more-evidence
duplicate
stale
```

Rules:

- Review decisions must be auditable.
- Approval should record reviewer, timestamp, rationale, and candidate version.
- Rejection should preserve the candidate record and reason.
- Repair requests should be append-only where possible.

### Knowledge Pack Builder

The Knowledge Pack Builder turns approved candidates into governed package
content.

Rules:

- Builder consumes only approved candidates.
- Builder does not connect to source systems directly.
- Builder must produce deterministic output for the same approved candidate set.
- Builder should preserve evidence links and review metadata.

### Publication Manifest

The Publication Manifest records what was released.

It should include:

- package id;
- package version;
- approved candidate ids;
- reviewer ids or names;
- source references;
- changelog;
- deprecation notes;
- compatibility notes for runtimes.

### Audit Trail

The Audit Trail records governance history.

It should preserve:

- candidate creation;
- validation results;
- review comments;
- approval decisions;
- repair history;
- version changes;
- publication events;
- deprecation and retirement events.

## Database Documentation Path

Atlas still has a database metadata path for the Turtle case study and similar
systems.

```text
Database
  -> Extractor
  -> Raw Metadata Snapshot
  -> Normalized Metadata Model
  -> Documentation Candidate
  -> Review
  -> Approved Knowledge Pack / Documentation Artifacts
```

### Extractors

Extractors connect to a database or read exported metadata files. They produce
structured technical facts such as schemas, tables, columns, data types, primary
keys, foreign keys, indexes, and comments.

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

The normalized model converts source-specific metadata into stable Atlas
concepts.

Initial concepts:

- database;
- schema;
- table;
- column;
- data type;
- nullable flag;
- primary key;
- foreign key;
- index;
- relationship;
- source comment or description.

Rules:

- Generators consume only the normalized model and optional knowledge overlays.
- The model should be easy to validate in tests.
- The model should not contain Turtle-specific fields.

### Business Knowledge Overlay

Business knowledge captures human meaning that is not guaranteed to exist in the
database schema.

Examples:

- business glossary terms;
- domain definitions;
- stewardship notes;
- known caveats;
- examples of valid values;
- policy or operational context.

Rules:

- Business knowledge is separate from technical metadata.
- Missing business knowledge must not block deterministic technical output.
- Future AI enrichment may suggest business knowledge, but humans should be able
  to review and edit it as Markdown.

### Generators

Generators convert normalized metadata and approved overlays into output
artifacts.

Planned MVP generators:

- Markdown data dictionary;
- DBML schema output;
- Mermaid relationship diagrams.

Rules:

- Generators do not connect to databases.
- Generators do not mutate the normalized model.
- Generators must produce deterministic output for the same input.
- Generator templates should be simple and reviewable.

## Continuous Knowledge Governance

Atlas should support a continuous loop:

```text
Candidate
  -> Review
  -> Approve
  -> Knowledge Pack
  -> Runtime Use
  -> Feedback / Bug / Lesson / Decision
  -> New Candidate
```

## Planned Package Shape

```text
atlas/
  cli/          Future command-line entry points
  candidate/    Candidate intake, validation, and schema contracts
  review/       Review workflow and decision records
  pack/         Knowledge Pack builder and publication manifest
  audit/        Audit trail and changelog helpers
  extractor/    Database metadata extraction interfaces and implementations
  parser/       Conversion from raw snapshots to normalized metadata
  generator/    Markdown, DBML, and Mermaid generators
  exporters/    File output helpers
  enrich/       Future AI and human knowledge overlay support
```

The current Sprint 0 task does not implement these modules. The directory names
reserve the intended boundaries.

## Boundary Rules

- Atlas reviews and governs; Athena compiles and harvests.
- Knowledge Candidates are not trusted runtime assets until approved.
- Turtle-specific logic belongs only in `examples/turtle`.
- Extractors must not render documentation.
- Generators must not connect to databases.
- Technical metadata must stay separate from business knowledge.
- Deterministic outputs come before AI-assisted outputs.
- No candidate should be published directly to runtime without governance.