# Agent Skills

Collection of portable agent skills following the [Agent Skills](https://agentskills.io) open standard. Works with Claude Code, Cursor, GitHub Copilot, Codex, Antigravity, and any agent supporting the Skills standard.

## Available Skills

### [`thinker`](./thinker/)

Socratic mastery partner for deep technical understanding through questions and challenges.

- **What it does:** Converts the agent into a question-only partner that never writes answers, summaries, or explanations for you.
- **Triggers:** "think with me about", "mastery mode", "question me on", "grill me on [component]"

```bash
npx skills add quanhua92/skills --skill thinker
```

---

### [`pr-reader`](./pr-reader/)

Extract and organize GitHub PR review comments into prioritized action plans.

- **What it does:** Extracts review comments via `gh` CLI, sorts by severity/difficulty, and creates a systematic fix list.
- **Triggers:** "read PR #X comments", "extract review feedback", "parse PR #X"

```bash
npx skills add quanhua92/skills --skill pr-reader
```

---

### [`first-principles`](./first-principles/)

Structured first-principles thinking with the D.A.R.E. prompt chain (Decompose, Audit, Recombine, Experiment).

- **What it does:** Deconstructs problems to root truths, questions inherited assumptions, recombines verified building blocks, and designs cheap real-world tests.
- **Triggers:** "first-principles", "first principles thinking", "D.A.R.E.", "decompose the problem", "audit assumptions"

```bash
npx skills add quanhua92/skills --skill first-principles
```

---

## Installation

### Add all skills
```bash
npx skills add quanhua92/skills
```

### Add a single skill
```bash
npx skills add quanhua92/skills --skill thinker
```

## Structure

```text
skills/
├── first-principles/
│   ├── references/
│   │   ├── prompt-pack.txt
│   │   └── transcripts.txt
│   └── SKILL.md
├── pr-reader/
│   └── SKILL.md
├── thinker/
│   └── SKILL.md
└── README.md
```

## License

MIT
