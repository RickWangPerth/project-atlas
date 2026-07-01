# Architecture Overview

Atlas separates metadata collection from documentation generation.

```text
Source database or metadata export
  -> extractor
  -> raw metadata snapshot
  -> normalizer
  -> normalized metadata model
  -> generator
  -> documentation artifact
```

Optional business knowledge and future AI enrichment can be layered on top of
the normalized model, but they are not required for deterministic MVP output.

## Responsibilities

| Layer | Responsibility | Must not do |
| --- | --- | --- |
| Extractor | Read technical metadata from a source | Render documentation |
| Raw snapshot | Preserve source facts | Store credentials |
| Normalizer | Map source facts into Atlas concepts | Connect to databases |
| Knowledge overlay | Add human business context | Replace technical metadata |
| Generator | Render Markdown, DBML, or Mermaid | Query databases |

## Design Constraints

- The normalized model is the contract between extraction and generation.
- Generators should be testable with fixture files.
- Extractors should be testable without needing documentation output.
- Example-specific logic must stay out of core modules.
- AI enrichment must remain optional and reviewable.
