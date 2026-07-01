# Project Charter

## Vision

Govern knowledge like software.

Atlas exists to help teams turn compiled knowledge into trusted, reviewed, versioned, and auditable knowledge assets.

## Mission

Atlas will provide the governance layer for Knowledge Packs produced by Athena or other compilers.

It should help teams review, approve, test, repair, publish, deprecate, and retire knowledge over time.

## Core thesis

AI agents need more than documents. They need trusted knowledge with evidence, review status, lifecycle state, and version history.

Atlas is not a chatbot and not a model provider. It is a governance system for knowledge assets.

## Project family boundary

| Layer | Project | Responsibility |
| --- | --- | --- |
| Knowledge Acquisition | Athena | Compile source material into structured, evidence-backed Knowledge Packs. |
| Knowledge Governance | Atlas | Review, approve, repair, version, publish, and retire Knowledge Packs. |
| Knowledge Runtime | AIPL | Future concept for delivering verified context and memory to agents at runtime. |

AIPL should remain conceptual until Athena and Atlas prove the upstream artifacts and governance process.

## Goals

- Build a deterministic governance workflow before adding complex UI or agent features.
- Keep Knowledge Pack validation, review, repair, and release responsibilities separate.
- Preserve evidence and provenance for important claims.
- Support human approval gates for high-value knowledge.
- Produce reviewable Markdown-first governance artifacts.
- Make database documentation a strong use case without limiting Atlas to databases only.
- Prepare for future integration with OpenAI, Apple Intelligence, Claude, Codex, local agents, and other runtimes.

## Non-goals

- Atlas will not be a general chat product.
- Atlas will not replace Athena as the knowledge compiler.
- Atlas will not require AI services for MVP governance.
- Atlas will not change source systems as part of the MVP.
- Atlas will not hardcode Turtle-specific rules into core modules.
- Atlas will not implement AIPL until the runtime layer is better understood.

## First case study

The first case study remains the Turtle example under `examples/turtle`.

That example is a proving ground for the Atlas workflow, not a special case in the product architecture. Turtle-specific metadata exports, notes, dictionaries, rules, or generated diagrams must stay inside `examples/turtle`.

## Success criteria for Sprint 0

- The project has a serious, coherent documentation baseline.
- The architecture describes clear governance responsibilities.
- The MVP roadmap is small enough to implement incrementally.
- Backlog items use stable Atlas issue IDs.
- Future implementation work has clear quality expectations.
- Atlas is clearly positioned as the governance layer between Athena and future runtimes.
