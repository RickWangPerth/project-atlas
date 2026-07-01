# Reflex, UDW, And WAMEX Research Review

## Summary

Reflex, UDW, and WAMEX are closely related examples of a document-to-knowledge
pipeline.

They are relevant to Atlas because they demonstrate a practical pattern for
turning document collections into structured outputs that can be retrieved,
reasoned over, and improved through reflection.

The shared pattern is:

```text
documents -> perception -> extraction -> structured knowledge -> retrieval / reasoning / reflection
```

This is highly aligned with Atlas' long-term direction, but the product centre is
different.

These systems are primarily document-centric. Atlas should become
organization-centric.

## What The Systems Do

### Reflex

Reflex focuses on academic papers.

It turns a research corpus into:

- structured tables
- a knowledge graph
- a thought graph for classifying and reasoning over papers
- retrieval and question answering over the extracted structure
- reflection loops that expose gaps and trigger schema evolution

The strongest idea is not merely extraction. It is the combination of schema,
knowledge graph, and thought graph to make a corpus analyzable.

### WAMEX

WAMEX applies the same architecture to mineral exploration reports.

It shows that the approach can work on domain-specific, messy, historical, and
scanned reports.

Important lessons for Atlas:

- domain metadata matters before deep extraction
- old scanned PDFs make OCR and layout recovery the bottleneck
- maps and timelines are useful first-class views
- domain schemas must reflect real business questions, not generic document fields

### UDW

UDW is the bring-your-own-documents workbench.

It applies the same pipeline to arbitrary PDFs and user-defined schemas.

Important lessons for Atlas:

- user-defined schemas are powerful
- every document type needs a matching route
- a thought graph can expose schema mismatch quickly
- reflection is useful when documents fall through the wrong processing path

## Concepts Worth Borrowing

### 1. Schema-guided extraction

The systems do not simply ask an LLM to extract everything.

They define a schema first, then use the schema to guide extraction.

Atlas should adopt this principle when it later adds AI-assisted extraction:

```text
business glossary / ontology -> schema -> extraction -> evidence-linked output
```

### 2. Multiple structured outputs

The systems produce three complementary shapes:

- tables
- knowledge graphs
- thought graphs

This is useful because one representation is not enough.

For Atlas, the equivalent future shapes may be:

- technical metadata tables
- business glossary entries
- ontology graphs
- workflow graphs
- decision graphs
- evidence records

### 3. Thought graph

The thought graph is the most interesting concept.

It turns a set of questions into a routing and reasoning structure. Every
document can be walked through the same decision tree, and the aggregate result
shows where the corpus lands.

Atlas should adapt this idea into a business decision graph.

Example future Atlas shape:

```text
business process -> decision point -> validation rule -> action -> outcome -> evidence
```

### 4. Reflection loop

The reflection loop is a strong product pattern:

```text
run extraction -> inspect aggregate -> discover gap -> evolve schema -> re-run
```

This maps directly to Atlas' future knowledge lifecycle.

Atlas should eventually support schema evolution and knowledge repair rather
than treating extraction as a one-shot operation.

### 5. Evidence-linked cells

The examples emphasize that users should not trust extracted cells blindly.
Highlighted values can be traced back to the source document.

Atlas should preserve this principle strongly.

A future Atlas knowledge record should point back to:

- source file
- source section
- source page or line range where possible
- extraction method
- reviewer
- confidence
- version

## Where Atlas Is Different

### 1. Atlas is organization-centric, not document-centric

The reviewed systems start from documents.

Atlas should start from organizational knowledge needs.

For the Turtle case study, the most important objects are not only documents.
They include:

- observations
- data entry records
- validation rules
- processing batches
- exports
- incidents
- people and roles
- business definitions
- operational workflows

Documents are evidence sources, not the whole system.

### 2. Atlas needs business governance

The reviewed systems show extraction and utilization very well, but they do not
fully address long-term governance.

Atlas should explicitly model:

- owner
- steward
- reviewer
- status
- approval
- version
- evidence
- change history
- lifecycle stage

### 3. Atlas should preserve living knowledge

A one-time corpus extraction is not enough for long-running organizational
systems.

Atlas should support knowledge that evolves over years:

```text
new source -> new evidence -> human review -> knowledge update -> versioned output
```

### 4. Atlas must remain deterministic first

The reviewed systems are advanced and AI-heavy.

Atlas MVP should not copy that complexity too early.

The Sprint 0 direction remains correct:

```text
extract -> normalize -> generate
```

AI enrichment, thought graphs, GraphRAG, and schema evolution should remain
future layers until the metadata and documentation foundation is trustworthy.

## Candidate Atlas Roadmap Influence

### MVP

Keep the current deterministic documentation-first scope:

- SQL Server metadata extraction
- normalized metadata model
- Markdown dictionary generation
- DBML generation
- Mermaid diagram generation
- Turtle example case study

### Next Layer

Add business knowledge foundations:

- business glossary
- concept definitions
- evidence links
- manual review status
- source registry

### Later Layer

Add knowledge engineering capabilities:

- ontology model
- schema-guided extraction
- workflow graph
- decision graph
- human-reviewed knowledge repair
- schema evolution loop

### Downstream Layer

Use governed knowledge for retrieval and reasoning:

- graph-based retrieval
- question answering over metadata and glossary
- impact analysis
- operational decision support

## Risks If Atlas Copies Too Much

- The MVP becomes too broad.
- The project turns into another AI demo instead of a reliable toolkit.
- Deterministic metadata work becomes mixed with uncertain AI extraction.
- Turtle-specific workflows leak into the generic core.
- Governance gets delayed behind more visually impressive features.

## Recommendation

Atlas should treat Reflex, UDW, and WAMEX as high-value references, not direct
blueprints.

Adopt:

- schema-first thinking
- multiple structured outputs
- evidence-linked extraction
- thought graph as a future decision-graph pattern
- reflection as a future schema-evolution loop

Do not copy yet:

- full AI extraction pipeline
- end-to-end document QA product shape
- domain-specific assumptions
- complex graph retrieval before the metadata foundation is stable

The key product distinction should remain:

```text
Existing systems: unstructured documents -> structured knowledge
Atlas: organizational knowledge -> governed, versioned, living knowledge system
```
