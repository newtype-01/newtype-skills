<p align="right">
  <strong>English</strong> | <a href="./README.zh-cn.md">简体中文</a>
</p>

# newtype-skills

A collection of AI prompt skills for analysis, writing, fact-checking, editing, interviewing, workflow orchestration, and Obsidian knowledge-base operations. These skills are methodology-driven prompts that can be used with any AI assistant (ChatGPT, Claude, Gemini, etc.).

---

## Created by huangyihe (黄益贺)

- **YouTube**: [https://www.youtube.com/@huanyihe777](https://www.youtube.com/@huanyihe777)
- **Twitter**: [https://x.com/huangyihe](https://x.com/huangyihe)
- **Substack**: [https://newtype.pro/](https://newtype.pro/)
- **知识星球**: [https://t.zsxq.com/19IaNz5wK](https://t.zsxq.com/19IaNz5wK)

---

## Skills Overview

| Skill | Description | Use Cases |
|-------|-------------|-----------|
| **[Super Analyst](./skills/super-analyst/SKILL.md)** | 12 analysis frameworks + systematic research methodology | Strategic analysis, competitive research, investment decisions, root cause diagnosis |
| **[Super Writer](./skills/super-writer/SKILL.md)** | 6 writing methodologies (W.R.I.T.E, AIDA, Storytelling, etc.) | Blog posts, marketing copy, brand stories, social media content |
| **[Super Fact-Checker](./skills/super-fact-checker/SKILL.md)** | Systematic verification: claim extraction, source credibility, annotation | Content review, source validation, accuracy assurance |
| **[Super Editor](./skills/super-editor/SKILL.md)** | 4-layer editing: structure → paragraph → sentence → word | Draft polishing, readability improvement, consistency |
| **[Super Interviewer](./skills/super-interviewer/SKILL.md)** | Dialogue techniques: open questions, 5 whys, Socratic method | Brainstorming, requirement gathering, deep exploration |
| **[Super Workflow](./skills/super-workflow/SKILL.md)** | Standards-first content production workflow with hard quality gates | Newsletters, reports, long-form articles, multi-step content pipelines |
| **[Super Obsidian](./skills/super-obsidian/SKILL.md)** | CLI-first Obsidian vault operations for search, reading, and note management | Vault search, daily notes, backlinks, note creation, knowledge-base maintenance |

---

## How to Use

### Method 1: Direct Copy-Paste

1. Open the skill file (e.g., `skills/super-analyst/SKILL.md`)
2. Copy the entire content
3. Paste it at the beginning of your conversation with any AI assistant
4. The AI will follow the methodology when responding

### Method 2: With OpenCode / Claude Code

If you're using [OpenCode](https://opencode.ai) or Claude Code, you can load these as skills:

1. Clone this repo to `~/.claude/skills/` or `.opencode/skill/`:
   ```bash
   git clone https://github.com/newtype-01/newtype-skills.git ~/.claude/skills/newtype-skills
   ```

2. Use the `/skill` command to load:
   ```
   /skill super-analyst
   ```

### Method 3: Custom GPT / Claude Project

You can also add these prompts to:
- ChatGPT Custom GPT instructions
- Claude Project system prompts
- Any AI tool that supports custom instructions

---

## Skills Detail

### Super Analyst

**Best for**: Strategic decisions, competitive analysis, investment evaluation, problem diagnosis

**Features**:
- 3-tier complexity detection (simple → 1 framework → combined frameworks)
- 12 analysis frameworks with step-by-step guides:
  - SWOT, Porter's Five Forces, Cost-Benefit
  - First Principles, 5 Whys, Design Thinking
  - Systems Thinking, Scenario Planning, MECE
  - Pareto, Hypothesis-Driven, Socratic Method
- Research methodology: source hierarchy, credibility assessment, triangulation

**Example prompts**:
- "Analyze Tesla's competitive advantages using SWOT"
- "Should we enter the India market? Use appropriate frameworks"
- "What's the root cause of our declining conversion rate?"

---

### Super Writer

**Best for**: Content creation, copywriting, storytelling

**Features**:
- 6 writing methodologies:
  - **W.R.I.T.E**: Write → Research → Ideate → Target → Enhance
  - **AIDA**: Attention → Interest → Desire → Action
  - **Storytelling**: Setup → Conflict → Journey → Climax → Resolution
  - **Content Writing Process**: Planning → Research → Writing → Editing → Publishing
  - **Content Creation Techniques**: Hook-Story-Offer, Problem-Agitate-Solve, etc.
  - **High-Value Content Strategies**: Deep articles, original research, expert interviews
- Style extraction for mimicking reference content

**Example prompts**:
- "Write a blog post about AI productivity using the W.R.I.T.E method"
- "Create a sales email for our new product using AIDA"
- "Write a brand story for a startup founder"

---

### Super Fact-Checker

**Best for**: Content review, source validation, accuracy assurance

**Features**:
- Claim classification (verifiable vs non-verifiable)
- Priority matrix (impact × suspicion level)
- Source credibility hierarchy (6 levels)
- Verification methods for data, quotes, and events
- Annotation system: ✅ verified, ⚠️ partial, ❓ unverifiable, ❌ incorrect, 🔍 needs more

**Example prompts**:
- "Fact-check this article and annotate each claim"
- "Verify the data sources in this report"
- "Review this press release for accuracy"

---

### Super Editor

**Best for**: Draft polishing, readability improvement, consistency checks

**Features**:
- 4-layer editing methodology:
  1. **Structure**: Overall architecture, chapter order, logic flow
  2. **Paragraph**: Coherence, transitions, information density
  3. **Sentence**: Clarity, rhythm, ambiguity
  4. **Word**: Precision, consistency, redundancy
- Checklist and common problem diagnosis for each layer
- Edit report format with justification

**Example prompts**:
- "Edit this article focusing on structure and paragraph flow"
- "Polish this draft for clarity and conciseness"
- "Review this document for terminology consistency"

---

### Super Interviewer

**Best for**: Brainstorming, requirement gathering, deep exploration

**Features**:
- Question types: open/closed, clarifying, probing, challenging, summarizing
- 4-phase dialogue: ice-breaking → open exploration → deep digging → summary
- Socratic techniques: concept clarification, assumption questioning, consequence exploration
- 5 Whys methodology for root cause discovery
- Needs excavation: surface → deep → core motivation

**Example prompts**:
- "Help me think through this product idea using Socratic method"
- "Interview me to understand my real requirements"
- "Challenge my assumptions about this business plan"

---

### Super Workflow

**Best for**: End-to-end content production, multi-step writing tasks, quality-gated publishing

**Features**:
- Standards-first hard gate before drafting
- 8-step pipeline: standards → ideation → outline → drafting → review → diagnosis → final verification → delivery
- Anti-rationalization checks to prevent skipping quality gates
- Writer/editor handoff rules with stage-by-stage validation

**Example prompts**:
- "Help me produce a newsletter from scratch with explicit quality gates"
- "Define acceptance criteria before drafting this industry report"
- "Run a full workflow for this long-form article"

---

### Super Obsidian

**Best for**: Searching, reading, creating, and managing notes in an Obsidian vault

**Features**:
- CLI-first rule: use `obsidian search` instead of `grep`/`rg` for vault search
- Command reference for search, read, create, append, daily notes, properties, and workspace operations
- Typical workflows for summarizing notes, updating daily logs, and exploring backlinks
- Clear fallback rules for when direct filesystem access is acceptable

**Example prompts**:
- "Search my Obsidian vault for notes about project planning"
- "Append today's meeting summary to my daily note"
- "Find orphan notes and help me organize them"

---

## Language

All skills are written in **Chinese (简体中文)** as the primary language. The methodologies and frameworks are universal and work equally well regardless of whether you interact in Chinese or English.

---

## License

MIT License - Feel free to use, modify, and distribute.

---

## Contributing

Contributions are welcome! If you have improvements or new skills to add, please submit a pull request.
