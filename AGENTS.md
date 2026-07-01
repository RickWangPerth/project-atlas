# Atlas Development Agents

Atlas work is split into clear responsibilities. These agent roles are planning
boundaries, not separate runtime services.

## Shared Rule

Documentation-first. Prefer deterministic outputs.

All agents must respect these project constraints:

- Do not hardcode Turtle-specific logic into core Atlas.
- Keep extractors separate from generators.
- Keep business knowledge separate from technical metadata.
- Prefer Markdown-first documentation.
- Do not introduce AI requirements into the deterministic MVP pipeline.

## Architect

Owns system shape, module boundaries, ADRs, and roadmap alignment.

Focus areas:

- normalized metadata model
- extractor and generator contracts
- package layout
- long-term extensibility without early overbuilding

## Database Agent

Owns database metadata extraction design.

Focus areas:

- SQL Server metadata extraction
- raw metadata snapshots
- source-specific metadata mapping
- avoiding secrets in logs or serialized outputs

The Database Agent must not render documentation.

## Documentation Agent

Owns Markdown-first documentation output and project documentation quality.

Focus areas:

- generated data dictionaries
- repository documentation
- contribution guidance
- example case study writeups

The Documentation Agent consumes normalized metadata and optional knowledge
overlays. It must not connect to databases.

## Diagram Agent

Owns relationship-oriented generated artifacts.

Focus areas:

- Mermaid relationship diagrams
- DBML generation
- deterministic diagram ordering
- readable relationship summaries

The Diagram Agent consumes normalized metadata only.

## AI Enrichment Agent

Owns future optional enrichment workflows.

Focus areas:

- suggested descriptions
- glossary link suggestions
- documentation gap analysis
- reviewable AI output

The AI Enrichment Agent must not replace deterministic extraction,
normalization, or generation.
