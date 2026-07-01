# Knowledge Candidate Review

## Purpose

Knowledge Candidate Review is the Atlas workflow for deciding whether a
candidate from Athena should become governed knowledge.

A candidate may come from static compilation or living knowledge harvest. Atlas
must not assume either source is automatically correct.

## Candidate Review Flow

```text
Knowledge Candidate
  ↓
Validation
  ↓
Review
  ↓
Approve / Reject / Request Repair / Needs More Evidence
  ↓
Knowledge Pack update
```

## Review Questions

A reviewer should ask:

- Is the claim understandable?
- Is the evidence sufficient?
- Is the source trustworthy enough for the intended use?
- Does this duplicate existing knowledge?
- Does it conflict with existing knowledge?
- Is it still current?
- Should it become a concept, rule, decision, glossary term, pattern, caveat, or
  repair note?
- Is it safe to expose to future runtimes?

## Review Outcomes

| Outcome | Meaning |
| --- | --- |
| approve | Candidate can be merged into a Knowledge Pack. |
| reject | Candidate should not be used. Keep audit record and reason. |
| request-repair | Candidate may be useful but needs correction. |
| needs-more-evidence | Candidate is plausible but not sufficiently supported. |
| duplicate | Candidate is already represented elsewhere. |
| stale | Candidate was true or useful before but should not be published now. |

## Review Record

Each review should record:

- candidate id;
- reviewer;
- decision;
- rationale;
- timestamp;
- candidate version or hash;
- linked evidence;
- linked repair request if applicable.

## Boundary Rules

- Atlas owns approval.
- Athena owns candidate generation.
- Runtime systems consume only approved Knowledge Packs.
- Review history must be preserved even when a candidate is rejected.