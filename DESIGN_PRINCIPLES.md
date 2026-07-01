# Design Principles

## 1. Governance first

Atlas exists to govern knowledge. Extraction, enrichment, and runtime usage belong to adjacent layers unless explicitly scoped into Atlas.

## 2. Treat knowledge like software

Knowledge should be reviewed, tested, versioned, released, repaired, deprecated, and retired.

## 3. Evidence is mandatory for important claims

A governed claim should be able to answer:

- where it came from;
- what source supports it;
- who reviewed it;
- when it was last changed;
- whether it is still current.

## 4. Human approval remains visible

High-value knowledge should show whether it is draft, reviewed, approved, published, deprecated, or retired. Approval should not disappear into logs that users never see.

## 5. Deterministic by default

For the same input, Atlas should produce the same governance output. Ordering, formatting, and filenames should be predictable so generated artifacts can be reviewed in version control.

## 6. Markdown preferred

Markdown is the primary governance format because it is easy to review, version, diff, and publish.

## 7. Business knowledge and technical metadata are different

Database structure can describe what exists. Business knowledge explains what it means. Atlas should support both without mixing their source of truth.

## 8. Knowledge tests over vibes

Knowledge quality should be assessed with tests where possible: expected answers, required evidence, coverage checks, stale-knowledge checks, and consistency checks.

## 9. Agent-agnostic by default

Atlas should not depend on one model provider, agent framework, or local hardware strategy. OpenAI, Apple Intelligence, Claude, Codex, local models, and future personal AI computers should all be able to consume the same governed assets.

## 10. Examples must not become product logic

The Turtle example should validate Atlas, not define Atlas. Any assumptions specific to Turtle belong under `examples/turtle`.

## 11. AIPL stays conceptual for now

AIPL is a future runtime idea, not a current repository requirement. Atlas should prepare clean outputs for runtime systems without prematurely building the runtime layer.

## Grill-me review questions

Every Atlas Epic should answer:

1. What governance risk does this reduce?
2. What evidence proves this knowledge is correct?
3. Who reviews or approves the output?
4. What happens when this knowledge becomes outdated?
5. What can we delete from the scope?
6. Why should Atlas own this instead of Athena or AIPL?
