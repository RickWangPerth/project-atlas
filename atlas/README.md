# Atlas Package Plan

This directory is reserved for the future Python package. Sprint 0 does not add
production code.

Planned module boundaries:

```text
atlas/
  cli/          command-line entry points
  extractor/    source metadata extraction
  parser/       raw-to-normalized metadata conversion
  generator/    Markdown, DBML, and Mermaid generation
  exporters/    file writing and output layout helpers
  enrich/       future human and AI knowledge overlays
```

Rules:

- Extractors must not render documentation.
- Generators must not connect to databases.
- Business knowledge must stay separate from technical metadata.
- Example-specific logic must not live in this package.
