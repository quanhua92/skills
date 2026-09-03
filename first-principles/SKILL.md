---
name: first-principles
description: >
  Apply first-principles thinking with the D.A.R.E. sequence: decompose
  the problem, audit inherited assumptions, recombine surviving building
  blocks, and test them against reality. Use when the problem framing,
  requirements, constraints, or conventional solution may rest on
  assumptions that should be reconstructed from fundamentals, or when
  the user explicitly requests first-principles reasoning.
---

# First-Principles Thinking

Use first-principles thinking to replace inherited stories and conventions with a model of what is actually known, then rebuild and test from there. The objective is not to be right every time; it is to learn quickly why an idea is wrong or right. AI performs the analysis while making the result inspectable: evidence, assumptions, uncertainty, dependencies, and decision criteria should be explicit. The user remains the decision maker and keeps the judgment.

## The D.A.R.E. framework

D.A.R.E. is a four-step prompt chain:

1. **D — Decompose:** Break the problem into its smallest useful constituent parts.
2. **A — Audit assumptions:** Identify and question the inherited assumptions in those parts.
3. **R — Recombine facts:** Assemble new solutions only from building blocks that survived the audit.
4. **E — Experiment against reality:** Design the smallest, cheapest, fastest real-world tests.

Run the stages in order. Do not jump to solutions during decomposition or to implementation before testing. At every stage, make the reasoning visible enough for the user to inspect.

Each prompt follows **AIM**:

- **Actor:** Tell the model what role and posture to take.
- **Input:** Supply the problem, context, evidence, and outputs from previous stages.
- **Mission:** Define the requested work and what completion looks like.

The prompts below are starting points, not immutable formulas. Improve them for the user, the problem, and the available model while preserving the stage boundaries.

## D — Decompose

The purpose of this stage is to see the parts of the machinery. Conventional advice often bundles optional resources into a supposed requirement. Strip the problem down without evaluating it.

Use this prompt:

> Act as a world-class first-principles analyst. Your job in this step is decomposition only. You are penalized for introducing advice, solutions, assumptions, or standard playbooks. Be my thought partner. Do not suck up to me.
>
> I want to understand exactly what this problem is made of. My problem is: **[INSERT PROBLEM]**. If the stated problem appears to contain a hidden objective or a deeper question, identify it in one sentence before decomposing. Ask whether I want you to decompose the original problem or the deeper one. Do not continue until I choose. Do not silently replace or reframe my problem.
>
> Break the problem into its smallest useful constituent parts. Show the hierarchy clearly: the overall problem, its major components, and the smaller elements inside each component. Use only dimensions that are relevant, such as people, process steps, time, resources, costs, and other dimensions that materially clarify the problem. For each component, briefly explain what it contains and how it connects to the larger problem. Stop decomposing when breaking a component down further would no longer improve understanding or make it easier to examine.
>
> Do not evaluate the components. Do not classify them as facts or assumptions. Do not recommend solutions. Only show me what parts the problem is made of.

If the model detects a hidden or deeper question, pause for the user's choice before proceeding. The model must not silently substitute a more convenient problem.

## A — Audit assumptions

The purpose of this stage is to distinguish what is supported from what is merely conventional. Treat every obvious component as potentially inherited until evidence proves otherwise. Audit load-bearing assumptions first because removing one may destroy the current solution while opening a better design space.

Use the output of D as input and use this prompt:

> Act as a skeptical red-team analyst whose only job is to uncover and question inherited assumptions. Assume that every “obvious” part of the problem may be hiding a convention until evidence proves otherwise.
>
> I want to know which of the building blocks above are load-bearing assumptions, not facts, and what becomes possible if they are wrong.
>
> Review the blocks from the previous step. Give me a numbered list of the assumptions hiding in them. For each one, on its own line, name the assumption. Classify whether it is a fact, convention, or unknown based on the evidence available. Verify the evidence. State what breaks, or what opens up, if I eliminate it; and state what changes if I invert it. Order the list from the most load-bearing assumption to the least.

Do not accept a claim as fact merely because it is common practice, familiar, expert-supplied, or present in a prior solution. Clearly distinguish verified evidence, convention, and unknowns. Do not rebuild the solution yet.

## R — Recombine verified building blocks

The purpose of this stage is creative reconstruction after the audit. The standard playbook is deliberately unavailable. Use the same verified elements in different arrangements, connections, and stacks, like the same musical notes arranged into different songs. Innovation does not require a secret extra ingredient; it often comes from a new combination of existing ones.

Use the surviving blocks and the audit output as input to this prompt:

> Act as an architect designing with no memory of how this problem has been solved before. The standard playbook is unavailable to you. Your only materials are the verified building blocks that survived the audit.
>
> I want new solutions assembled from those building blocks — not fresh ideas pulled from how it is normally done, and not variations on the standard answer.
>
> Take the building blocks that survived the audit. Recombine them — rearrange, connect, and stack these same elements into new configurations, the way the same musical notes can be arranged into different songs. Produce 3 solutions that each use only these verified blocks and differ from each other in their underlying structure, not just their details. For each solution: name which building blocks it is built from, which discarded convention it refuses to obey, and its single biggest point of failure. Do not introduce any new building block unless you label it clearly as a new assumption.

Keep the alternatives structurally distinct. Label every new assumption, and do not smuggle conventional practice back into the answer as an unmarked requirement.

## E — Experiment against reality

The purpose of this stage is to let the real world vote. Theoretical possibilities are not yet solutions. Design tests that reveal what works and what does not as early and cheaply as the problem permits, minimizing time, money, effort, and reputation risk.

Use the three R-stage solutions as input to this prompt:

> Act as a skeptical experimenter. Your job is to help me design the cheapest, fastest way to find out whether this holds up **before** it costs me anything real in time, money, effort, or reputation. Do not try to sell me the idea. Give me a test I could actually run, and the pass/fail lines to read it by.
>
> I want the smallest real-world test that helps me understand what parts work and what parts do not, as early and as cheaply as the problem allows.
>
> Take the 3 solutions from the previous step and design experiments to test whether they will work in the real world. Design the smallest concrete test for each: what to actually do, who to talk to, or what to build, using the least time, money, effort, or social risk the problem allows. For each test, tell me what result would rule that solution out, what result would keep it alive, and what I would learn about the problem either way. Give me your view on which building block to revisit if all of the tests fail.

For each experiment, make the action, measurement, decision thresholds, and learning explicit. A failed test is useful if it identifies which building block or assumption needs to be revisited. Do not present a test as proof of universal success; it is a fast way to update the model.

## Operating principles

### Start with what is known

People inherit assumptions from colleagues, family, industries, experts, and previous experience without investigating them. Begin by asking:

- What do I actually know for sure?
- What am I assuming?
- What else could produce this result?
- Which part can I test?

Do not normalize a persistent problem by repeating its story. Deconstruct the system from the root cause upward.

### Keep AI from making thinking average

General-purpose language models are mathematical pattern-matching systems. They do not directly observe the universe or possess ordinary real-world experience; they generate likely continuations from learned patterns. Familiar answers can therefore sound better than they deserve, and a more fluent answer can make the user less likely to check it. The D.A.R.E. constraints force the model to examine the problem rather than reflexively provide a familiar solution.

Use AI as an unusually powerful partner for searching combinations and simulating possible tests, but preserve human judgment. Require it to show its work, expose evidence and uncertainty, and state what would change its conclusion.

### Learn quickly from failure

First principles are not a surefire way to avoid failure. The aim is not 100% correct predictions. The aim is to discover quickly why an assumption or configuration failed. A low hit rate can still work when one successful experiment has a large effect: you do not need 100 wins; you may need one that changes the trajectory.

## Illustrative examples

These examples clarify the framework; they are not universal facts or required answers.

- **Persistent exhaustion:** Someone who woke exhausted despite having more control over their schedule initially explained it as needing more sleep, enduring the grind, drinking more coffee, or working less. A sleep study instead found frequent awakenings caused by a jaw structure blocking the airway. Decomposing the system exposed that the perceived problem was not the root cause.
- **Reusable rockets:** Rockets were conventionally treated as disposable, unlike cars. Asking why a rocket could not land vertically and fly again challenged the assumption and changed the economics of space travel.
- **Focus:** “I cannot focus” may decompose into sleep, phone addiction, unclear tasks, too many priorities, boredom, lack of a deadline, or work with no real impact. The label is not yet the diagnosis.
- **Starting a YouTube channel:** Expert playbooks may prescribe a studio, professional camera, lighting, editor, creative director, and production agency. At the essential level, a phone and a story can be enough to begin. A company likewise does not inherently require millions in funding or a prestigious office.
- **Toyota production:** After World War II, Toyota had less capital, fewer resources, and a smaller market than American mass-production companies. Rather than copy Detroit, it questioned assumptions about big cars, huge batches, large inventories, defect handling, and process organization. This helped produce just-in-time production, later adopted widely.
- **Tesla:** Tesla questioned assumptions shared by Toyota and other automakers, including the need for a combustion engine. By 2020, Tesla had overtaken Toyota as the world's most valuable automaker.
- **Music and recombination:** Western music often uses 12 notes as its alphabet, while Indian classical and Arabic traditions can use pitches between Western piano notes. The different sound is not necessarily out of tune; it reflects a different rule set. Even with the same 12 notes, Bach, the Beatles, and Beyoncé produced radically different compositions. The same ingredients can make millions of dishes.
- **Vacuum cleaners:** James Dyson observed that bagged vacuum cleaners lost suction as their bags filled and reportedly made 5,127 prototypes over five years before reaching a breakthrough design. Iteration made the idea answerable to reality.
- **Google experiments:** Google has run large numbers of experiments, including testing shades of blue to learn which one encouraged more link clicks. Small controlled changes can resolve questions that intuition cannot.
- **Comedic failure:** Martin Short has described failure rates around 98% in comedy as “great odds,” because the small fraction that works can still matter enormously. Treat experiments as learning opportunities rather than as a demand for perfect prediction.

## Suggested response discipline

When applying this skill:

1. Confirm the exact problem and preserve its wording unless the user approves a deeper or reframed version.
2. State which D.A.R.E. stage is active.
3. Keep stage outputs separate so facts, assumptions, recombinations, and tests are not conflated.
4. Cite or request evidence when classifying a claim as fact; otherwise mark it as convention or unknown.
5. Surface uncertainty, dependencies, and failure modes.
6. End experiments with an explicit next update: continue, revise a building block, or discard the solution.

Use judgment and taste to adapt the prompts. The framework is a tool for clearer thinking, not a substitute for domain expertise, evidence, or the user's final decision.
