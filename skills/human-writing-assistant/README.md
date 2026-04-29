# Human Writing Assistant (Anthropic Skill)

> **Generate Text That Reads as Human-Written From the Start.**  
> A specialized Anthropic Skill that produces natural-sounding academic and technical text, built on the same 21-rule experience library as the Humanizer skill.

---

## Introduction

**"Can this sound like a real person wrote it?"**

Overly synthetic writing often has the same structural fingerprints: perfect logic chains, uniform sentence lengths, complete purpose explanations, and summary sentences that tie everything together. Even after vocabulary simplification, these patterns persist.

**Human Writing Assistant** generates text that avoids those fingerprints from the start. It applies the 21-rule natural writing library at the generation stage — producing output that is slightly uneven, slightly incomplete, and structured the way humans actually write.

### Humanizer vs. Human Writing Assistant

| | Humanizer | Human Writing Assistant |
|---|---|---|
| **Use case** | You already have text; make it read more naturally | You need to write something; avoid synthetic patterns from scratch |
| **Input** | Existing synthetic or human text | A topic, section, or writing brief |
| **Output format** | Direct rewrite by default; optional diagnosis mode | Direct output, no explanation |
| **Best for** | Reports, essays, papers already written | Drafting new sections, paragraphs, descriptions |

---

## The 21 Iron Rules (Applied at Generation)

The same rule library as Humanizer, applied proactively during writing:

**Structure:** Paragraphs match requested count. One idea per sentence. No "both X and Y" parallels. Lists get uneven treatment. Nested conditionals split layer by layer. Paragraph rhythm forced to vary (fast-slow-fast).

**Vocabulary:** All high-register words demoted. Only student-level connectors (So / Also / Then / But). No template openers ("One of the most..." / "This study aims to...").

**Logic & Flow:** Active voice with "We" as subject. Data described as action ("We put 70% into training"). Tool/role descriptions varied in length and format.

**Sentence endings:** No bracket explanations. No closing summary sentences. No purpose tails ("to achieve X"). No self-endorsement ("so they are quite reliable").

**Framing:** No section cross-references. No scope announcements ("covers everything from X to Y"). No function-explainer sentences ("This makes it easy to see...").

---

## Self-Evolution Loop

Before showing the result, the skill drafts, self-checks, reflects on the
weakest pattern, and rewrites weak sentences from scratch. This happens silently
by default.

Ask for `debug`, `诊断`, or `为什么这么写` to see the self-check. Within one
conversation, user feedback shapes later drafts. Persistent memory is opt-in:
say `经验入库`, `记住这个规则`, or `以后都这样` to let the agent add an abstract
lesson to [`references/evolution-memory.md`](references/evolution-memory.md).
It should not store private source text.

---

## Installation & Usage

1. Download [`skills/human-writing-assistant/SKILL.md`](skills/human-writing-assistant/SKILL.md)
2. Add to **Project Knowledge** (Claude Desktop / Cursor) or **System Instructions**
3. Trigger with any writing request:

```
Write a methodology section introduction for a rhinoplasty outcome prediction project.
Make it sound naturally human-written.
```

Or in Chinese:
```
帮我写[内容]，要像人写的，不要太机械
```

**Optional style flags:**
- Add `--chinglish` to allow light Chinese-English feel when a less polished voice fits the task
- Add `--short` for condensed output

---

## Example

**Prompt:**
> Write a paragraph introducing the methodology of a rhinoplasty outcome prediction project.

**Output:**
> We build a deep learning model to predict how a patient's face may look after rhinoplasty. The input is a regular 2D photo. No special equipment needed. The model learns from a dataset of before and after photo pairs. We use Pix2Pix as the main baseline, and add perceptual loss on top. For evaluation, we check SSIM, PSNR, and FID. The whole thing runs on CPU, so normal clinic desktop can handle it.

Notice: short sentences mixed with longer ones, no closing summary, no "This study aims to...", active voice throughout.

See [`skills/human-writing-assistant/example/`](skills/human-writing-assistant/example/) for more.

---

## Related Skill

Use this skill together with **[Humanizer](../humanizer/)** for a complete workflow:
1. Draft with **Human Writing Assistant** → naturally human from the start
2. Paste final text into **Humanizer** for a structural cleanup

---

## Benchmark

Both skills share the same 21-rule experience library, developed through 20+ iterative rewrite sessions. Rules were kept only after receiving validated positive feedback during rewrite review.
