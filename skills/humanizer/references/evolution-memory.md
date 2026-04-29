# Humanizer Evolution Memory

This file stores reusable rewrite lessons only after the user explicitly asks
to keep them. It is not a raw transcript log.

## When To Add An Entry

Add an entry only when the user says one of these:
- "经验入库"
- "记住这个规则"
- "以后都这样"
- "keep this pattern"
- clear positive feedback plus a request to remember it

Do not add entries after ordinary rewrites. Do not store private source text.

## Entry Format

```markdown
### M-001: [Short rule name]

- **Pattern**: The recurring writing pattern.
- **Failure Signal**: How the weak version usually sounds.
- **Correction**: The concrete rewrite move that fixes it.
- **Evidence**: Short abstract example, not user text.
- **Status**: proposed | confirmed | retired
```

## Seed Entries

### M-001: Break Complete Explanation Chains

- **Pattern**: One sentence explains action, contrast, reason, and value.
- **Failure Signal**: The sentence feels too complete and too balanced.
- **Correction**: Split the chain. Keep the action. State the contrast plainly.
  Drop the value claim if it only wraps up the thought.
- **Evidence**: `We use X. Y does not fit here.` works better than
  `We use X instead of Y because Z.`
- **Status**: confirmed

### M-002: End On A Plain Fact

- **Pattern**: Paragraphs end with a summary or significance sentence.
- **Failure Signal**: The ending sounds like it is closing a section.
- **Correction**: Delete the summary. End on the last concrete fact.
- **Evidence**: `Small clinics usually cannot afford either option.` is enough.
- **Status**: confirmed
