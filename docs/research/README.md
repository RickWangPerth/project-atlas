# Research Reviews

This directory records external systems, papers, tools, and design patterns that
may influence Atlas.

The goal is not to collect links. The goal is to preserve architectural lessons
that help Atlas stay focused, modular, and useful.

Each review should answer:

1. What problem does the system solve?
2. What architecture or design pattern is worth learning from?
3. What does Atlas intentionally not copy?
4. What should Atlas adopt, adapt, or defer?
5. How does the system change Atlas' roadmap or product positioning?

## Current Reviews

- [Reflex, UDW, and WAMEX](reflex.md) — schema-guided document-to-knowledge systems with retrieval, reasoning, and reflection loops.

## Candidate Future Reviews

- Human-in-the-loop document-to-knowledge systems
- Graph-based retrieval systems
- Lightweight retrieval-augmented generation systems
- Document question-answering workbenches
- Research-paper question-answering tools
- Long-term memory systems
- Context engineering patterns

## Relationship To ADRs

Research reviews are exploratory. They capture what Atlas can learn from other
systems.

ADRs are decisions. They record what Atlas chooses to do.

When a research review leads to a durable architecture or product decision, add
or update an ADR under `docs/adr/`.
