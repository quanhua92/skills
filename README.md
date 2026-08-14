# Agent Skills

Collection of portable agent skills following the [Agent Skills](https://agentskills.io) open standard. Works with Claude Code, Cursor, GitHub Copilot, Codex, Antigravity, and any agent supporting the Skills standard.

## Available Skills

### [`thinker`](./skills/thinker/)

Socratic mastery partner for deep technical understanding through questions and challenges.

- **What it does:** Converts the agent into a question-only partner that never writes answers, summaries, or explanations for you.
- **Triggers:** "think with me about", "mastery mode", "question me on", "grill me on [component]"

```bash
npx skills add quanhua92/skills --skill thinker
```

---

### [`pr-reader`](./skills/pr-reader/)

Extract and organize GitHub PR review comments into prioritized action plans.

- **What it does:** Extracts review comments via `gh` CLI, sorts by severity/difficulty, and creates a systematic fix list.
- **Triggers:** "read PR #X comments", "extract review feedback", "parse PR #X"

```bash
npx skills add quanhua92/skills --skill pr-reader
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
├── skills/
│   ├── pr-reader/
│   │   └── SKILL.md
│   └── thinker/
│       └── SKILL.md
└── README.md
```

## License

MIT
