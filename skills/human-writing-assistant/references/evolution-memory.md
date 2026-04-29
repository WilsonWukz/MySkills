# Human Writing Assistant Evolution Memory

This file stores reusable drafting lessons only after the user explicitly asks
to keep them. It is not a raw transcript log.

## When To Add An Entry

Add an entry only when the user says one of these:
- "经验入库"
- "记住这个规则"
- "以后都这样"
- "keep this pattern"
- clear positive feedback plus a request to remember it

Do not add entries after ordinary drafts. Do not store private source text.

## Entry Format

```markdown
### M-001: [Short rule name]

- **Pattern**: The recurring drafting pattern.
- **Failure Signal**: How the weak version usually sounds.
- **Correction**: The concrete generation move that fixes it.
- **Evidence**: Short abstract example, not user text.
- **Status**: proposed | confirmed | retired
```

## Seed Entries

### M-001: Draft With Gaps

- **Pattern**: A draft tries to explain every reason and consequence.
- **Failure Signal**: The paragraph feels too complete for a first human draft.
- **Correction**: Keep one or two facts unexplained. Let the reader infer the
  link when the meaning is still clear.
- **Evidence**: `The input is a regular photo. No special equipment needed.`
  feels more natural than a fully justified purpose sentence.
- **Status**: confirmed

### M-002: Rewrite Weak Sentences From Scratch

- **Pattern**: The draft keeps a stiff sentence and only swaps vocabulary.
- **Failure Signal**: The sentence still has the same rhythm and logic skeleton.
- **Correction**: Throw away the sentence shape. Rebuild it as two shorter
  sentences or one plain fact.
- **Evidence**: Replace structure, not just words.
- **Status**: confirmed
