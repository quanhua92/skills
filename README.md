# Agent Skills

Collection of portable agent skills following the [Agent Skills](https://agentskills.io) open standard. Works with Claude Code, Cursor, GitHub Copilot, Codex, Antigravity, and any agent supporting the Skills standard.

## The Three-Skill Thinking System

Three cognitive modes for working inside an Obsidian vault (or any knowledge environment) with an AI agent:

```
thinking-partner        "Think with me."
first-principles        "Reconstruct this from fundamentals."
mastery-coach           "Test whether I really understand this."
```

**The human remains the thinker. The AI becomes leverage on thinking.**

AI contributes questions, challenges, explanations, connections, counterexamples, evidence, models, and experiments. The user thinks, concludes, and writes permanent knowledge in their own words.

### Which skill should I use?

```
I DON'T KNOW WHAT I THINK YET
            │
            ▼
     thinking-partner


THE NORMAL FRAMING MAY BE WRONG
            │
            ▼
     first-principles


I THINK I UNDERSTAND THIS
AND WANT TO TEST THAT
            │
            ▼
      mastery-coach
```

### Recommended default workflow

```
Open Obsidian vault
       ↓
Open Codex
       ↓
Enter Plan mode
       ↓
Activate thinking-partner
       ↓
Discuss / investigate / challenge
       ↓
User updates notes in own words
```

Plan mode provides the technical boundary: *don't edit my vault.*

Thinking-partner provides the cognitive boundary: *don't take over my thinking.*

These are complementary rather than redundant.

### Skill escalation

`thinking-partner` is normally the starting point. During discussion, escalate when needed:

```
thinking-partner
      │
      ├── inherited assumptions / bad framing
      │         ↓
      │   first-principles
      │
      ├── factual uncertainty
      │         ↓
      │   inspect / search / research
      │
      ├── competing hypotheses
      │         ↓
      │   evidence / experiment
      │
      └── user wants to prove mastery
                ↓
          mastery-coach
```

---

## The Three Procedures

### Procedure A — Thinking (`thinking-partner`)

```
read current notes
      ↓
understand user's current model
      ↓
find the most useful next intervention
      ↓
question / challenge / explain / connect
      ↓
user responds
      ↓
mental model evolves
      ↓
user updates notes
```

General-purpose collaborative thinking. The partner can ask, explain, challenge, connect, compare, summarize, and research. It does not automatically rewrite notes or produce polished prose unless asked.

### Procedure B — First Principles (`first-principles`)

```
D — Decompose
↓
A — Audit assumptions
↓
R — Recombine surviving building blocks
↓
E — Experiment against reality
↓
update the model
```

This is usually a loop, not a one-time waterfall:

```
D → A → R → E
↑           │
└───────────┘
```

Use when the current framing rests on assumptions that should be reconstructed. The D.A.R.E. method has explicit stage boundaries — do not turn every thinking session into D.A.R.E.

### Procedure C — Mastery (`mastery-coach`)

```
What?
  ↓
Why?
  ↓
How?
  ↓
What if?
  ↓
Prove it.
```

The user answers. The coach probes weaknesses. Difficulty escalates as understanding improves. The output is demonstrated understanding, not a polished essay.

---

## Example Transition

```
User:
  I think independent verification requires another LLM.

thinking-partner:
  helps distinguish model independence from evidence independence.

User:
  Maybe the important thing is epistemic independence.

User:
  Let's first-principles this.

first-principles:
  decomposes what "independent verification" actually requires.

  ...

Later:

User:
  I think I understand the architecture now. Grill me.

mastery-coach:
  What invariant does independent verification preserve?
  What breaks if the worker verifies itself?
  What evidence proves the verifier is actually independent?
```

---

## Available Skills

### [`thinking-partner`](./thinking-partner/)

General-purpose collaborative thinking partner for exploring ideas, challenging reasoning, and developing understanding.

- **Use when:** you're figuring out what you think, exploring an idea, challenging reasoning, or need help connecting concepts.
- **Triggers:** "think with me about", "help me reason about", "challenge this", "explore this with me"

```bash
npx skills add quanhua92/skills --skill thinking-partner
```

### [`first-principles`](./first-principles/)

Structured first-principles thinking with the D.A.R.E. prompt chain (Decompose, Audit, Recombine, Experiment).

- **Use when:** the current framing may rest on inherited assumptions that should be reconstructed.
- **Triggers:** "first-principles", "D.A.R.E.", "decompose the problem", "audit assumptions"

```bash
npx skills add quanhua92/skills --skill first-principles
```

### [`mastery-coach`](./mastery-coach/)

Socratic mastery coach that tests whether you truly understand a concept through questioning and challenge.

- **Use when:** you think you understand something and want to prove it.
- **Triggers:** "quiz me", "grill me", "test my understanding", "mastery mode"

```bash
npx skills add quanhua92/skills --skill mastery-coach
```

### [`pr-reader`](./pr-reader/)

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
npx skills add quanhua92/skills --skill thinking-partner
```

## Structure

```text
skills/
├── thinking-partner/
│   └── SKILL.md
├── first-principles/
│   ├── references/
│   │   ├── prompt-pack.txt
│   │   └── transcripts.txt
│   └── SKILL.md
├── mastery-coach/
│   └── SKILL.md
├── pr-reader/
│   └── SKILL.md
└── README.md
```

## License

MIT
