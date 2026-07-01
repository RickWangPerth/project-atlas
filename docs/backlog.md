# Backlog

The initial backlog defines the MVP path. Items are intentionally small and
documentation-first so the project can evolve through reviewable increments.

## ATLAS-001 Project bootstrap

Establish the repository baseline.

Acceptance criteria:

- README explains the vision, MVP scope, and repository layout.
- Architecture documentation defines extractor, model, generator, and enrichment
  boundaries.
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

- Model represents database, schema, table, column, key, index, and relationship
  concepts.
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

## ATLAS-008 Knowledge Candidate schema

Define the pre-governance handoff contract between Athena and Atlas.

Acceptance criteria:

- Schema supports candidate id, type, title, claim, source, evidence,
  confidence, lifecycle state, destination, and reviewer notes.
- Schema supports static compilation candidates and living harvest candidates.
- Schema is serializable and deterministic.
- Candidate records are not treated as approved Knowledge Pack content.

## ATLAS-009 Knowledge Candidate Review workflow

Define and implement the first review workflow.

Acceptance criteria:

- Review outcomes include approve, reject, request-repair, needs-more-evidence,
  duplicate, and stale.
- Review records preserve reviewer, timestamp, rationale, candidate version or
  hash, and linked evidence.
- Approved candidates can be selected for Knowledge Pack assembly.
- Rejected candidates remain in the audit trail.

## ATLAS-010 Harvest Review Workflow

Support review of candidates produced by Knowledge Harvest skills.

Acceptance criteria:

- Review flow supports lessons, decisions, patterns, caveats, workflow notes, and
  repair notes.
- `/decision` candidates can be routed into ADR candidate review.
- Reviewers can mark harvested knowledge as uncertain without discarding it.
- Atlas preserves source event context where available.

## ATLAS-011 Continuous Knowledge Governance

Design the continuous loop from runtime feedback back into candidate review.

Acceptance criteria:

- Documentation describes the loop from Knowledge Pack use to feedback, bug,
  lesson, decision, or new candidate.
- Governance states include captured, candidate, reviewed, approved, published,
  deprecated, and retired.
- Stale knowledge and conflict handling are explicitly documented.
- No runtime feedback is published directly without review.