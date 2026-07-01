# Pipeline

The Atlas pipeline should be deterministic from source metadata to generated
artifacts.

## Stage 1: Extract

Input:

- database connection, or
- exported metadata files

Output:

- raw metadata snapshot

The extractor captures database facts. For SQL Server, this initially means
schemas, tables, columns, data types, nullability, primary keys, foreign keys,
and selected index metadata.

## Stage 2: Normalize

Input:

- raw metadata snapshot

Output:

- normalized Atlas metadata model

Normalization removes database-specific shape from downstream generators. The
same Markdown, DBML, and Mermaid generators should work for any future
extractor that can produce the normalized model.

## Stage 3: Overlay Knowledge

Input:

- normalized metadata model
- optional human-authored business knowledge
- optional future AI suggestions

Output:

- documentation context

Business knowledge is not the same as technical metadata. It should be stored
and reviewed separately so generated documentation can distinguish facts from
interpretation.

## Stage 4: Generate

Input:

- normalized metadata model
- optional knowledge overlay

Output:

- Markdown dictionary
- DBML file
- Mermaid diagrams

Generators must produce stable output for the same input. They should not
connect to databases or perform extraction work.

## Stage 5: Review

Generated artifacts should be suitable for pull request review. Changes in
database structure should be visible as focused diffs in Markdown, DBML, or
Mermaid output.
