# Humanizer (Anthropic Skill)

> **Transform Synthetic-Sounding Text into Natural Human Writing.**  
> A specialized Anthropic Skill that rewrites text to read more naturally, with fewer mechanical patterns and less overly polished structure.

---

## Introduction

**"Why does my text still sound synthetic after I simplify the words?"**

Most people think synthetic writing is only about vocabulary. It is not. The stronger signal is usually **patterns and structure** — clean logic chains, perfect paragraph rhythm, and summary sentences that tie everything up too neatly.

**Humanizer** targets the structural root causes. It does not just swap hard words for easy ones. It breaks the logical skeleton, changes paragraph rhythm, and removes the invisible scaffolding that makes writing feel machine-polished.

### What Makes This Different

Standard paraphrasers change words. Humanizer changes **architecture**:
- Shatters "cause → effect → purpose → summary" logic chains
- Forces uneven sentence rhythm (fast-slow-fast, not a steady march)
- Cuts purpose tails ("to achieve X"), scope announcements ("covers everything from X to Y"), and self-endorsement sentences ("so they are quite reliable")
- Applies a 21-rule experience library built from iterative rewrite feedback

---

## How It Works

By default, Humanizer returns only the rewritten text. If you ask for `debug`,
`解释`, `诊断`, or give negative feedback such as `不佳` / `极差`, it switches to
full diagnostic mode with four sections:

### 1｜分析原段为什么有合成感
Diagnosis of which specific structural patterns make the text feel synthetic — not just "this sounds off" but *why* the structure creates that feeling.

### 2｜总结之前用户反馈"优秀"/"不佳"的改进思路和原因
Learns from your feedback within the session. Tracks which rules produced good results and which patterns caused failures. Avoids repeating mistakes.

### 3｜如何将优秀经验和之前的避免犯错用于这次的改进
Sentence-level rewrite plan: `[Original] → [What to do] → [Because: which rule]`

### 4｜给你的结果
The rewritten text. Same paragraph count as input. No explanation. Just the result.

---

## The 21 Iron Rules (Summary)

Built from iterative real-world rewrite feedback:

| # | Rule | What It Targets |
|---|---|---|
| 1 | Paragraph count is sacred | Never merge or split paragraphs |
| 2 | Long sentences get cut | One idea per sentence |
| 3 | Full vocabulary demotion | utilize→use, demonstrate→show, etc. |
| 4 | Student-level connectors only | Ban: Furthermore/Moreover/Thus |
| 5 | Kill template openers | Ban: "One of the most..." / "This study aims to..." |
| 6 | Active voice everywhere | Replace all passive with "We" |
| 7 | Data as action | "contains X%" → "We put X% into..." |
| 8 | Uneven tool descriptions | Vary length, never identical format |
| 9 | Destroy logic skeletons | Break "X instead of Y because Z" chains |
| 10 | Extract bracket explanations | Pull (parenthetical) into own sentence |
| 11 | Delete closing summary sentences | No "bow on the package" |
| 12 | Cut ALL purpose tails | Delete all "to + verb" purpose endings |
| 13 | No identical role/tool formats | Vary grammar pattern for each item |
| 14 | Delete section cross-references | Remove "as explained in Section X" |
| 15 | No repeated sentence formats | Vary openers constantly |
| 16 | Uneven list treatment | 5+ items must have mixed lengths |
| 17 | Delete scope announcements | Remove "covers everything from X to Y" |
| 18 | Delete function-explainer sentences | Remove "This makes it easy to see..." |
| 19 | Split nested conditionals | "If A, then B, even if C" → 3 sentences |
| 20 | Delete self-endorsement | Remove "so they are quite reliable" |
| 21 | Force paragraph rhythm variation | Must have fast-slow-fast sentence lengths |

---

## Built-in Feedback Learning

Humanizer uses a lightweight self-evolution loop:

- It drafts a rewrite, scores it against the 21 rules, reflects on the weakest
  pattern, and refines once or twice before showing the final result.
- This loop is hidden by default. Ask for `debug`, `诊断`, or `解释` to see the
  self-check.
- Within one conversation, feedback like **"优秀" / "极优秀"** or **"不佳" /
  "极差"** shapes the next rewrite.

Persistent memory is opt-in. If you say `经验入库`, `记住这个规则`, or `以后都这样`,
the agent may add an abstract lesson to
[`references/evolution-memory.md`](references/evolution-memory.md). It should
not store private source text.

---

## Installation & Usage

1. Download [`skills/humanizer/SKILL.md`](skills/humanizer/SKILL.md)
2. Add to **Project Knowledge** (Claude Desktop / Cursor) or **System Instructions**
3. Trigger with any text:

```
Humanize this. Make it read more naturally and reduce the overly synthetic patterns.

[paste your text here]
```

Or in Chinese:
```
帮我把这段改得更自然，少一点机器味：[你的文字]
```

For diagnosis, add:
```
帮我改得更自然，并解释为什么原文有合成感
```

---

## Example

**Input (synthetic-sounding):**
> Rhinoplasty is one of the most common cosmetic and reconstructive surgeries worldwide. However, a significant gap often exists between patient expectations and actual surgical results, a common cause of postoperative dissatisfaction.

**Output (Humanized):**
> Rhinoplasty is a very common surgery, for both cosmetic and reconstructive reasons. But what patient expect and what really happen after surgery is often quite different. This lead to disappointment after the procedure.

See [`skills/humanizer/example/`](skills/humanizer/example/) for the full annotated rewrite with diagnosis.

---

## Benchmark

This skill was developed through 20+ iterative rewrite sessions, producing the 21-rule experience library. Each rule was kept only after receiving "优秀" or "极优秀" feedback during rewrite review.
