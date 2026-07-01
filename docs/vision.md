# Vision

Project Atlas exists to transform database metadata into human knowledge.

Databases describe real systems: entities, relationships, constraints, and
operational decisions. Atlas makes that information easier to inspect,
document, and improve without requiring teams to reverse-engineer every schema
from scratch.

## What Atlas Should Produce

Atlas should produce documentation that is:

- understandable by engineers, analysts, and domain experts
- deterministic enough to review in version control
- modular enough to support multiple database engines
- structured enough to support future AI enrichment
- grounded in database facts before adding interpretation

## MVP Focus

The MVP is intentionally narrow:

- SQL Server metadata extraction
- normalized metadata model
- Markdown data dictionary generation
- DBML generation
- Mermaid relationship diagrams
- Turtle example case study

## Long-Term Direction

Future versions may add AI-assisted enrichment, documentation publishing,
change reports, and more extractors. Those features should build on the same
deterministic metadata pipeline rather than bypassing it.
