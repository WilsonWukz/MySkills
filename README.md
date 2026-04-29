# MySkills

Welcome to the MySkills repository. This repository serves as a collection of specialized AI skills designed to enhance productivity in academic and technical workflows. Currently, there are three distinct skills available. The collection will continue to grow as new skills are developed and added.

---

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/0221b410-116e-4976-b2ff-7648164b4e59" />

---

## Available Skills

### 1. Paper Visualizer

The Paper Visualizer skill transforms complex academic papers into high-fidelity technical schematics. It acts as a structural architect, decoding the logic of a research paper and converting it into a structured prompt optimized for image generation models.

**Key Features:**
- **Cognitive Layout Engines:** Automatically selects the most appropriate visual topology for the paper, such as a linear pipeline, parallel dual-stream, or cyclic loop.
- **Typography Guardrails:** Enforces specific typography rules to ensure text remains legible and minimizes generation artifacts.
- **Structured Schema Output:** Produces a detailed, coordinate-based prompt that guides the image generation process, ensuring the final diagram adheres to the logical structure of the paper.

**How to Use:**
1. Download `skills/visual-architect/SKILL.md`.
2. Add it to your AI assistant's project knowledge or system instructions.
3. Provide the paper's methodology section and use the prompt: "Generate a visual schema for this paper's methodology."

---

### 2. Humanizer

The Humanizer skill takes existing text and rewrites it to sound more natural and less mechanical. It focuses on breaking down the rigid structural patterns often found in synthetic writing, rather than simply swapping vocabulary.

**Key Features:**
- **Structural Overhaul:** Shatters overly clean logic chains and forces an uneven sentence rhythm to mimic human writing.
- **Diagnostic Mode:** Can analyze text and explain exactly which patterns make it sound synthetic, providing a sentence-level rewrite plan.
- **21-Rule Experience Library:** Operates based on a strict set of rules derived from iterative rewrite feedback, targeting specific mechanical writing habits.
- **Feedback Learning:** Adjusts its approach based on user feedback within a session, learning which patterns to avoid.

**How to Use:**
1. Download `skills/humanizer/SKILL.md`.
2. Add it to your AI assistant's project knowledge or system instructions.
3. Provide the text you want to rewrite and use the prompt: "Humanize this. Make it read more naturally and reduce the overly synthetic patterns."

---

### 3. Human Writing Assistant

The Human Writing Assistant is designed to generate text from scratch that reads as naturally human-written. It applies the same 21-rule library used by the Humanizer skill, but does so proactively during the drafting process.

**Key Features:**
- **Natural Drafting:** Avoids synthetic patterns from the very beginning, ensuring the initial draft is structurally sound and natural.
- **Self-Evolution Loop:** Internally drafts, self-checks against the rule library, and refines weak sentences before presenting the final output.
- **Style Flexibility:** Supports optional flags like `--chinglish` for a less polished voice or `--short` for condensed output.

**How to Use:**
1. Download `skills/human-writing-assistant/SKILL.md`.
2. Add it to your AI assistant's project knowledge or system instructions.
3. Provide a writing brief and use a prompt like: "Write a methodology section introduction for a rhinoplasty outcome prediction project. Make it sound naturally human-written."

---

*Note: This repository is actively maintained, and new skills will be added in the future.*
