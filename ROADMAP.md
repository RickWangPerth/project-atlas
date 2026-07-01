# Roadmap

This roadmap keeps the MVP narrow: extract metadata, normalize it, and generate
reviewable documentation artifacts.

## Sprint 0: Bootstrap

### ATLAS-001 Project bootstrap

Goal: establish a serious open-source repository baseline before production
code starts.

Deliverables:

- project charter
- architecture plan
- MVP roadmap
- contributor and development guidance
- initial backlog
- Turtle example boundaries

Status: in progress.

## MVP Phase 1: Deterministic Metadata Pipeline

### ATLAS-002 SQL Server metadata extractor

Goal: read SQL Server system metadata and produce a raw metadata snapshot.

Initial scope:

- schemas
- tables
- columns
- data types
- nullability
- primary keys
- foreign keys
- indexes where needed for documentation

Out of scope:

- documentation rendering
- business glossary inference
- database write operations

### ATLAS-003 Normalized metadata model

Goal: define the stable Atlas model consumed by all generators.

Initial scope:

- Python data structures or schemas for database, schema, table, column, key,
  index, and relationship concepts
- validation rules
- deterministic serialization
- test fixtures based on small synthetic examples

## MVP Phase 2: Documentation Generators

### ATLAS-004 Markdown dictionary generator

Goal: generate Markdown-first data dictionaries from normalized metadata.

Initial scope:

- database overview
- schema and table pages
- column tables
- key and relationship summaries
- deterministic ordering

### ATLAS-005 DBML generator

Goal: generate DBML from normalized metadata for schema review and compatible
tooling.

Initial scope:

- tables
- columns
- primary keys
- foreign key references
- source comments when available

### ATLAS-006 Mermaid relationship generator

Goal: generate Mermaid diagrams that explain table relationships.

Initial scope:

- entity relationship diagrams
- deterministic node and edge ordering
- diagram files that can be embedded in Markdown

## MVP Phase 3: Example Case Study

### ATLAS-007 Turtle example case study

Goal: prove the end-to-end MVP workflow with the Turtle example while keeping
core Atlas generic.

Initial scope:

- example metadata input under `examples/turtle/metadata`
- generated dictionary under `examples/turtle/dictionary`
- generated diagrams under `examples/turtle/diagrams`
- notes that explain what the example demonstrates

Out of scope:

- Turtle-specific branches inside core extractors, parsers, or generators
- production deployment
- AI-generated business knowledge as a required step

## Later Opportunities

- additional database extractors
- richer business glossary workflows
- AI-assisted description suggestions
- documentation site generation
- incremental change reports
- plugin packaging
