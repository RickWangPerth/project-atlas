# Knowledge Model

The knowledge model describes meaning that sits beside technical metadata.

Atlas should be able to generate useful documentation from metadata alone, but
human knowledge makes that documentation more valuable.

## Knowledge Sources

Potential knowledge sources include:

- human-authored glossary definitions
- stewardship notes
- data quality caveats
- known business rules
- examples of valid or invalid values
- future AI-generated suggestions reviewed by humans

## Separation From Metadata

Business knowledge should not be treated as extracted database fact.

For example:

- a column name and data type are technical metadata
- a description of how the organization uses that column is business knowledge
- an AI suggestion about that column is an enrichment suggestion until reviewed

## MVP Position

The MVP should prepare for knowledge overlays but should not require them.
Markdown dictionary generation must work from normalized metadata alone.

## Future Enrichment

Future AI enrichment may suggest:

- plain-language table summaries
- column descriptions
- glossary links
- relationship explanations
- missing documentation warnings

These suggestions should be reviewable and should not overwrite deterministic
metadata.
