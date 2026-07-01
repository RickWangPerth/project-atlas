# Business Glossary

The business glossary is a human-owned layer of meaning. It defines terms,
domains, and usage notes that are not guaranteed to exist in database metadata.

## Purpose

The glossary should help readers understand what data means in practice.

Examples:

- domain terms
- abbreviations
- stewardship notes
- policy references
- operational caveats

## Relationship To Metadata

Metadata can point to glossary terms, but glossary entries should remain
separate from the technical metadata model.

This separation makes it clear which information came from the database and
which information came from human knowledge or later enrichment.

## MVP Guidance

For the MVP, glossary support should stay simple:

- Markdown-first
- optional
- reviewable in version control
- referenced by generated documentation only when explicitly provided

## Future Guidance

AI may later suggest glossary entries or links. Those suggestions should be
stored separately until reviewed.
