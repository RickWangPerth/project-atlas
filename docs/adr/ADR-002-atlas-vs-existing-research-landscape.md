# ADR-002: Atlas In The Existing Research Landscape

## Status

Accepted for Sprint 0.

## Context

Atlas is being designed in a landscape where many strong systems already exist
for document understanding, information extraction, knowledge graph construction,
and retrieval-augmented generation.

Relevant adjacent systems and ideas include:

- Reflex
- UDW
- WAMEX
- DocSpiral
- GraphRAG
- LightRAG
- NotebookLM-style document QA
- General document parsing and OCR pipelines

These systems are valuable references. They show that the pipeline from
unstructured documents to structured tables, knowledge graphs, and grounded
question answering is increasingly practical.

However, Atlas should not become another generic document parser, GraphRAG demo,
or knowledge graph extractor.

Atlas exists to solve a slightly different problem: how to turn technical and
business knowledge into a governed, versioned, reviewable, and continuously
maintained organizational knowledge system.

## Decision

Atlas will position itself above raw extraction and retrieval.

Atlas will use ideas from existing research systems, especially:

- schema-guided extraction
- evidence-linked structured output
- human review
- iterative schema improvement
- graph-based knowledge representation
- retrieval and reasoning over structured knowledge

But Atlas will extend these ideas toward organizational knowledge governance.

The primary product direction is:

```text
metadata -> documentation -> glossary -> ontology -> evidence -> review -> governance
```

The MVP remains deterministic and documentation-first, as defined in ADR-001.
AI-assisted extraction, GraphRAG, and reflection loops are future capabilities,
not mandatory Sprint 0 functionality.

## Positioning

Atlas is not:

- a general-purpose OCR product
- a generic PDF-to-knowledge-graph system
- a replacement for GraphRAG
- a NotebookLM clone
- a one-shot document QA tool

Atlas is:

- a metadata and documentation toolkit
- a business glossary and ontology foundation
- a system for preserving technical and business knowledge
- a future governance layer for evidence, ownership, review, and versioning
- a way to turn tacit organizational knowledge into explicit, maintainable knowledge

## Comparison

| Capability | Reflex / UDW / WAMEX | GraphRAG-style systems | Atlas |
| --- | --- | --- | --- |
| Document parsing | Strong | Usually external | Planned / optional |
| Schema-guided extraction | Strong | Partial | Planned |
| Tables from documents | Strong | Partial | Optional |
| Knowledge graph construction | Strong | Strong | Planned |
| Grounded retrieval | Strong | Strong | Future |
| Thought graph / reasoning route | Strong | Limited | Future |
| Business glossary | Limited | Limited | Core |
| Technical metadata dictionary | Limited | Limited | Core |
| Business process modelling | Limited | Limited | Planned |
| Evidence and provenance lifecycle | Partial | Partial | Core direction |
| Human review | Partial / strong in some systems | Partial | Core direction |
| Governance and ownership | Limited | Limited | Core direction |
| Long-term living knowledge | Limited | Limited | Core direction |

## Implications For Atlas

Atlas should borrow from the research landscape, but remain disciplined about
scope.

For the MVP, Atlas should prioritize:

1. deterministic metadata extraction
2. normalized metadata modelling
3. Markdown documentation generation
4. DBML generation
5. Mermaid relationship diagrams
6. clear separation between technical metadata and business knowledge
7. a Turtle example that validates the workflow without hard-coding the product

For future phases, Atlas should explore:

1. business glossary generation
2. ontology modelling
3. evidence-linked knowledge records
4. human-reviewed knowledge repair
5. workflow and decision graph modelling
6. schema evolution and reflection loops
7. GraphRAG as a downstream consumer of governed knowledge

## Consequences

Positive:

- Atlas has a clear position instead of competing directly with broad document AI systems.
- The MVP can stay small, deterministic, and testable.
- Future AI features can be added as enrichment layers rather than core dependencies.
- Research reviews become a durable project asset.

Tradeoffs:

- Atlas will initially look less impressive than end-to-end AI demos.
- Some advanced capabilities, such as GraphRAG and thought graphs, are deferred.
- The project must maintain a strict boundary between current MVP scope and future research ambitions.

## Guardrails

- Do not make AI extraction mandatory for the MVP.
- Do not make Turtle-specific business logic part of the generic Atlas core.
- Do not treat retrieval as the final product; retrieval is a consumer of governed knowledge.
- Do not add knowledge graph complexity before the metadata and documentation foundation is stable.
- Keep external research reviews under `docs/research/` and architecture decisions under `docs/adr/`.
