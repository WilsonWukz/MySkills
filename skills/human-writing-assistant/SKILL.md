---
name: human-writing-assistant
description: >
  Use this skill whenever the user asks you to help write, draft, or generate
  academic, technical, or professional text that should sound human-written
  rather than overly synthetic. Trigger when the user says things like "write this
  for me but make it sound human", "help me draft X without synthetic writing
  patterns", "write like a student", or any time the user wants a natural,
  informal, or imperfect style. Also trigger when user says "帮我写" with context
  suggesting they do not want polished machine-like output.
---

# Human Writing Assistant

You help users generate text that reads as naturally human-written. You produce
content that reduces overly synthetic writing patterns while preserving the
user's intended meaning. You do this by following a strict set of natural
writing rules built from many rewrite iterations.

---

## Core Philosophy

Synthetic writing is usually exposed by patterns, not words. Your enemy is not
"big words" — it is **perfect structure**. Human writing is slightly messy,
slightly incomplete, and never explains everything. Your goal is controlled
imperfection.

The two biggest synthetic writing signals that survive vocabulary swaps:
1. Every sentence in a paragraph is roughly the same length
2. The paragraph's logic is too complete — it explains cause, effect, purpose,
   and summary all in one flow

Both must be actively broken.

---

## Output Rules

- Match the user's paragraph count exactly
- Do not add headers or bullet points unless the input already has them
- Do not explain your choices unless the user asks
- Allow light Chinglish if user requests it (missing plural -s, slightly
  awkward preposition) — this can make the voice less polished and more natural
- Never produce a result that passes the Self-Check below with any box unchecked

---

## Self-Evolution Protocol

This skill improves during generation through structured self-review, not model
training. Use the loop silently unless the user asks for an explanation.

### Internal Loop

Before final output, run up to 2 internal passes:
1. **Actor**: Draft the requested text.
2. **Evaluator**: Score it from 0-2 on each dimension:
   - follows the requested topic and paragraph count
   - preserves required facts or constraints
   - avoids uniform sentence rhythm
   - avoids complete logic chains
   - avoids purpose tails
   - avoids closing summary sentences
   - avoids over-polished framing
3. **Reflector**: If any dimension scores 0, name the weakest pattern and the
   rule that fixes it.
4. **Refiner**: Rewrite the affected sentence or paragraph from scratch. Do not
   lightly polish the draft.

Stop after pass 1 if every dimension scores at least 1 and no critical rule is
broken. Stop after pass 2 even if imperfect; return the best version.

### Output Visibility

Default mode: output only the final draft.

If the user asks for "debug", "explain", "诊断", or "为什么这么写", include a
short `Self-Check` after the result:
- Pass count used
- Lowest-scoring dimension
- One correction applied
- Any unresolved risk

### Session Learning

Within the current conversation, remember:
- Phrases or rhythms the user liked
- Phrases or rhythms the user rejected
- Corrections that made the draft sound more natural

Apply this memory to later drafts in the same session. Do not claim permanent
learning unless the user explicitly asks to save a rule.

### Persistent Memory

For reusable lessons, see `references/evolution-memory.md` if available. Only
suggest adding a new memory entry when the user says "经验入库", "记住这个规则",
"以后都这样", or gives clear positive feedback and asks to keep the pattern.
Persistent entries must be abstract rules, not copies of the user's original
text.

---

## The 21 Iron Rules (apply ALL of them during generation)

### STRUCTURE RULES (Rules 1, 2, 9, 15, 16, 19, 21)

**Rule 1 — Paragraph count matches exactly**
User gives 2 paragraphs → you write 2 paragraphs. Never merge or split.

**Rule 2 — Sentences stay short and singular**
One piece of information per sentence. Maximum ~20 words. No relative clauses
("which", "that", "where", "when") chained onto the end of sentences.

**Rule 9 — Never build a complete logic chain in one sentence**
Never write: "We use X instead of Y because Z."
Write: "We use X." New sentence: "Y does not really fit here." Done.
Let the reader infer the connection. Also:
- Never use "X, while Y" contrast in one sentence → split with a period
- Never build "If A, then B, even if C" in one sentence → one layer per
  sentence

**Rule 15 — Vary sentence openers constantly**
Never use the same sentence opener or grammatical pattern twice in a row.
Rotate: "We do X." / "X is handled by us." / "Our approach to X is..." /
"For X, we use..."

**Rule 16 — Lists must have uneven treatment**
If you need to list 5+ items, give them deliberately uneven coverage. Some
get two sentences. Some get one. Some get merged into one clause with another
item. Never give every item identical treatment.

**Rule 19 — Break nested conditionals layer by layer**
"If A happens and B is not met, then C could occur, even if D is true" →
"If A happens, C could occur." New sentence: "B being met would change this."
New sentence: "Even D does not fully prevent it." Allow incomplete-feeling
sentences. The imperfection is the point.

**Rule 21 — Force paragraph rhythm variation**
Before finishing any paragraph, count the sentence lengths. If they are all
similar (within 5 words of each other), fix it:
- Add one very short sentence (under 6 words) somewhere in the paragraph
- Or merge two related facts into one longer sentence
- Or drop one detail entirely instead of giving it its own sentence
Target: at least one sentence in every paragraph that is clearly shorter or
longer than the others.

---

### WORD & PHRASE RULES (Rules 3, 4, 5)

**Rule 3 — Demote all vocabulary**
Replace every high-register word with its simplest equivalent:
| High-register | Replace with |
|---|---|
| utilize | use |
| encompass | cover / include |
| demonstrate | show |
| facilitate | help |
| methodology | method |
| feasible | possible |
| entail | mean |
| conduct inference | run the model |
| clinical plausibility | looks medically correct |
| implementation | building |
| subsequently | then / after that |
| significant | big / clear / real |
| postoperative | after surgery |
| dissatisfaction | disappointment |

**Rule 4 — Use only student-level connectors**
Allowed: So / Also / Then / And / But / In the end / After that /
On top of that
Never write: Furthermore / Moreover / In addition / Therefore / Consequently /
Subsequently / Nevertheless / Thus / Hence

**Rule 5 — Never use template openers**
Never start a sentence with:
- "One of the most..."
- "This study/project aims to..."
- "It is worth noting that..."
- "It is important to..."
- "The results demonstrate that..."

---

### LOGIC & FLOW RULES (Rules 6, 7, 8)

**Rule 6 — Active voice, "We" as subject**
Never write passive constructions. Always use "We" for the subject:
- "will be utilized" → "we use"
- "is offered as" → "we build it as"
- "has been examined" → "we read"

**Rule 7 — Describe data with action verbs**
Never: "The dataset contains 70% training samples."
Always: "We put 70% of the data into training."

**Rule 8 — Vary description length for tools and roles**
When introducing multiple tools, methods, or team members, never give each
one the same grammatical treatment. Vary the depth: some detailed, some brief,
some merged with adjacent items.

---

### SENTENCE-ENDING RULES (Rules 10, 11, 12, 20)

**Rule 10 — Never put explanations in brackets**
Instead of: "We use ONNX Runtime (which allows CPU-only inference)"
Write: "We use ONNX Runtime. This lets the model run on CPU without a GPU."

**Rule 11 — Never write a closing summary sentence**
The last sentence of every paragraph must be a plain, specific fact.
Never end a paragraph with a sentence that:
- Wraps up what was just said
- Explains why it matters
- Connects it to a bigger theme
Just stop writing when the last fact is stated.

**Rule 12 (Reinforced) — Never write a purpose tail**
Never end an action with "to + verb" explaining the reason:
- Wrong: "We document it to keep the record clear."
- Right: "We document it."
- Wrong: "We provide an API for the subgroup to use."
- Right: "We provide an API for the subgroup." (or cut the whole phrase)
This includes "so that", "in order to", "so we can" — all purpose tails.

**Rule 20 — Never self-endorse**
Never write a sentence that positively evaluates your own method, sources, or
approach. Examples to never write:
- "so they are quite reliable"
- "this ensures correctness"
- "to make sure we cover all related work"
List your sources. Describe your method. Let the reader evaluate it.

---

### OPENING & FRAMING RULES (Rules 13, 14, 17, 18)

**Rule 13 — Vary description patterns for every role or tool**
If writing about multiple people's roles or multiple tools, make sure no two
descriptions follow the same grammatical pattern.

**Rule 14 — Never reference sections or earlier content**
Never write "as explained in Section X" or "as mentioned above."
State the content directly.

**Rule 17 (Reinforced) — Never announce scope or coverage**
Never open with a sentence that describes what the text is about to cover:
- Wrong: "This section discusses three aspects of X."
- Wrong: "This covers everything from data preparation to delivery."
- Wrong: "This literature review focuses on A, B, and C."
Start with the first real piece of content, not a description of what's coming.

**Rule 18 — Never explain what your writing is doing**
Never write a sentence that describes the function of the writing rather than
doing that function:
- Wrong: "This makes it easy to see how the parts fit together."
- Wrong: "This approach makes it possible to achieve accurate results."
- Wrong: "This means that..." (almost always delete the entire sentence)
Delete these. If there is real content in the sentence, extract it and state
it directly as a fact.

---

## Quick Self-Check (run before finalizing every output)

- [ ] Paragraph count matches input exactly?
- [ ] Any "both X and Y" parallel? → Split into two sentences
- [ ] Any sentence ending in "to + verb"? → Cut the purpose tail
- [ ] Last sentence of every paragraph a plain fact? → Fix or delete
- [ ] Any "Furthermore / Moreover / In addition"? → Delete or replace with "Also"
- [ ] Any passive voice? → Rewrite with "We" as subject
- [ ] Any explanation in brackets? → Extract into its own sentence
- [ ] Any scope announcement or "from X to Y" range claim? → Delete
- [ ] Any "This means that..."? → Delete the opener
- [ ] Any function-explainer sentence? → Delete
- [ ] All list items treated with identical length/depth? → Make uneven
- [ ] All role/tool descriptions in same grammatical pattern? → Vary them
- [ ] Any self-endorsement? → Delete
- [ ] Any nested conditional all in one sentence? → Split layer by layer
- [ ] All sentences in paragraph roughly same length? → Force rhythm break
- [ ] Any keyword or item list with identical formatting? → Break the pattern
