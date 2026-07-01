# Metadata Model

The metadata model is the core Atlas contract. It represents technical database
facts in a source-neutral shape.

## Technical Metadata

Technical metadata describes what exists in the database.

Initial concepts:

- database
- schema
- table
- column
- data type
- nullability
- primary key
- foreign key
- index
- relationship
- source description or comment

## Raw Metadata vs Normalized Metadata

Raw metadata preserves source-specific details. For SQL Server, that may include
system catalog names, engine-specific type names, and source identifiers.

Normalized metadata maps those details into Atlas concepts so generators can be
database-agnostic.

## Deterministic Model Rules

- Entity identifiers should be stable.
- Ordering should be explicit.
- Optional fields should be represented consistently.
- Serialization should avoid environment-specific values.
- Secrets and connection details must never be part of metadata output.

## What Does Not Belong Here

The metadata model should not include:

- Turtle-specific fields
- business glossary definitions
- AI-generated descriptions as source facts
- documentation layout decisions
- database credentials
