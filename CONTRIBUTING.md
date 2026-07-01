# Contributing

Project Atlas is documentation-first and deterministic by default. Contributions
should make the metadata pipeline easier to understand, test, and review.

## Working Model

Use small, reviewable changes.

Preferred flow:

```text
Issue -> Design note -> Minimal implementation -> Tests -> Review -> Merge
```

For larger work, start with a short design note in `docs/` or an ADR before
writing production code.

## Contribution Rules

- Keep extractors separate from generators.
- Keep business knowledge separate from technical metadata.
- Keep Turtle-specific material inside `examples/turtle`.
- Prefer Markdown-first documentation.
- Prefer deterministic output over clever automation.
- Avoid adding dependencies unless they are clearly justified.
- Update tests when behavior changes.
- Update documentation when architecture or workflow changes.

## Code Quality Expectations

When Python implementation begins, contributors should expect to run:

```bash
uv run --extra dev pytest
uv run --extra dev mypy src
uv run --extra dev ruff check .
```

If a check cannot be run, explain why in the pull request and include the exact
command that should be run by the reviewer.

## Pull Request Checklist

- The change has a clear Atlas issue ID where practical.
- The module boundaries are respected.
- Output ordering is deterministic.
- Documentation was updated when behavior or scope changed.
- Tests or fixtures were added for behavior changes.
- No credentials, connection strings, or private database exports are included.
