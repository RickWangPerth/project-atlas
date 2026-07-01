# Project Atlas

> Govern knowledge like software.

Project Atlas is the **Knowledge Governance** layer for the Athena / Atlas / AIPL project family.

Atlas exists to make compiled knowledge reviewable, approvable, repairable, versioned, auditable, and safe to use by humans and AI agents.

## Core framing

Athena compiles knowledge.

Atlas governs knowledge.

AIPL or external agent platforms use knowledge at runtime.

```text
Sources / workflows / schemas / code / tacit knowledge
    ↓
Athena: Knowledge Compiler
    ↓
Draft Knowledge Pack
    ↓
Atlas: Knowledge Governance
    ↓
Reviewed / approved / versioned Knowledge Pack
    ↓
AIPL, OpenAI, Apple Intelligence, Claude, Codex, local agents, or other runtimes
```

## Why Atlas exists

AI agents are becoming more capable, but they still need trusted context. The hard enterprise question is not only whether AI can answer, but whether a team can prove:

- where the answer came from;
- who reviewed the knowledge;
- whether the knowledge is still current;
- what changed between versions;
- which claims are unsupported;
- whether a repair was approved;
- whether outdated knowledge has been retired.

Atlas turns knowledge from a passive document collection into a governed asset.

## Mission

Build a documentation-first governance system that can:

- review and approve Knowledge Packs;
- track evidence and provenance;
- manage knowledge lifecycle states;
- support human-reviewed repair workflows;
- run knowledge tests and quality checks;
- publish versioned knowledge releases;
- preserve an audit trail for high-value domains.

## Relationship to the original database documentation idea

Atlas started as a documentation-first toolkit for turning database metadata into human-readable, reviewable knowledge assets.

That remains an important use case.

The scope has now expanded from **database documentation** to **knowledge governance**. Database metadata is one source type. Knowledge Packs may also come from SOPs, policies, code, meeting notes, research notes, and tacit expert knowledge compiled by Athena.

## Project family

| Layer | Project | Status | Responsibility |
| --- | --- | --- | --- |
| Knowledge Acquisition | Athena | Active repo | Compile documents and tacit knowledge into structured, evidence-backed Knowledge Packs. |
| Knowledge Governance | Atlas | Active repo | Review, approve, repair, version, publish, and retire knowledge. |
| Knowledge Runtime | AIPL | Concept only | Deliver verified context and memory to AI agents at runtime. |

AIPL does not need a repository yet. It may later be implemented through OpenAI, Apple Intelligence, local personal AI computers, or another agent platform. Atlas should focus on making governed knowledge usable by any of those runtimes.

## MVP scope

The first useful version should support this workflow:

1. Accept a draft Knowledge Pack.
2. Validate package structure and manifest metadata.
3. Run basic knowledge tests.
4. Track review status.
5. Record human approval or requested changes.
6. Apply approved repair records in an append-only way.
7. Produce a versioned reviewed Knowledge Pack.

## Out of scope for the MVP

- general chatbot interface;
- background systems that change knowledge without approval;
- complex multi-tenant enterprise permissions;
- marketplace distribution;
- production AI enrichment as a required step;
- source database mutation;
- hardcoded Turtle-specific behavior in core modules.

## Repository layout

```text
atlas/                  Future Python package modules
docs/                   Architecture, concepts, governance notes, and planning
docs/backlog.md         Initial MVP backlog
examples/turtle/        Example case study only; no core logic lives here
tests/                  Future pytest test suite
templates/              Future deterministic output templates
README.md               Project overview
PROJECT_CHARTER.md      Project goals, scope, and principles
DESIGN_PRINCIPLES.md    Design principles
ARCHITECTURE.md         System architecture plan
ROADMAP.md              MVP roadmap
JOBLOG.md               Work log
```

## Architecture principles

- Governance is the product, not an afterthought.
- Every important claim should retain evidence and provenance.
- Human review and approval should be visible in the artifact history.
- Knowledge lifecycle should be explicit: draft, reviewed, approved, published, deprecated, retired.
- Knowledge tests should work like regression tests for important domain claims.
- Atlas should be agent-agnostic and model-agnostic.
- Examples validate Atlas; they must not become product logic.

## Development status

Sprint 0 is focused on project shape, documentation quality, and a clear governance MVP plan.

When implementation begins, the intended Python workflow is:

```bash
uv run --extra dev pytest
uv run --extra dev mypy src
uv run --extra dev ruff check .
```

These commands are targets for the upcoming implementation phase, not a claim that the full Python package already exists.
