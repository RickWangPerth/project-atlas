# Turtle Example

This directory is the first Project Atlas case study.

The Turtle example should prove the Atlas workflow with realistic metadata while
keeping the core project generic.

## Directory Purpose

```text
examples/turtle/
  metadata/      Example input metadata exports
  dictionary/    Example generated Markdown dictionary output
  diagrams/      Example generated Mermaid diagrams
  generated/     Other generated artifacts, such as DBML
```

## Rules

- Turtle-specific files belong in this directory.
- Turtle-specific logic must not be added to `atlas`.
- Example metadata must not include credentials, secrets, or private connection
  details.
- Generated files should be deterministic and reviewable.

## Planned Use

The MVP should eventually use this example to demonstrate:

- SQL Server metadata extraction or metadata import
- normalized metadata model output
- Markdown dictionary generation
- DBML generation
- Mermaid relationship diagrams

Business explanations for Turtle should be stored as example knowledge, not as
hardcoded generator behavior.
