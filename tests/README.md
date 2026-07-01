# Tests

This directory is reserved for the future pytest test suite.

Planned test coverage:

- SQL Server metadata extraction mapping
- raw snapshot normalization
- normalized metadata validation
- Markdown generator fixture output
- DBML generator fixture output
- Mermaid generator fixture output

Core tests should use small synthetic fixtures. Example-specific fixtures should
stay under `examples/<name>` unless they are generalized for core behavior.
