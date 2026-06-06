---
name: teach-diff
description: Teach a code change interactively, one section at a time, at the user's chosen audience depth. Use when the user wants an explanation read back conversationally, asks to be taught a diff, wants to understand what an agent built, requests "go deeper", "teach me this change", "reverse grill me", "explain one step at a time", or invokes teach-diff after an unvibe report.
---

# Teach Diff

Turn a code-change explanation into an interactive walkthrough. Move one section at a time, check understanding, and adapt depth based on the user's replies.

## Workflow

1. Establish the source:
   - If the user provides an existing `unvibe` report, use it as the primary artifact.
   - If repo-local settings exist in `docs/agents/code-explanation.md`, use them to find saved `unvibe` reports when the user refers to a prior report without giving a path.
   - If no report exists, first perform the same evidence-gathering workflow as `$unvibe` and build a concise working outline before teaching.
2. Choose a starting level:
   - Use the user's requested level when given.
   - Otherwise start at Level 1 and offer to go deeper.
3. Explain one section at a time.
4. After each section, ask one short check-in question before continuing.
5. Let the user steer with replies like "go deeper", "skip", "show code", "explain like Rails", "more product", "what could break", or "continue".

## Teaching Style

- Ask questions one at a time.
- If a question can be answered by exploring the codebase, explore the codebase instead of asking the user.
- Ground every explanation in code evidence, existing report sections, or explicit user context.
- Keep each spoken section compact. Prefer a crisp explanation followed by a useful check-in over a long lecture.
- Translate concepts into the user's frame of reference when they provide one.
- When the user is confused, restate with a smaller example, then reconnect it to the actual files.
- Do not pretend certainty about intent. Say when something is inferred or unknown.

## Audience Levels

Level 1: Exec / Marketing. Explain impact and value with no implementation details.

Level 2: PM / Product. Explain user flows, product behavior, scope, edge cases, and open questions.

Level 3: Junior Engineer. Explain the files, concepts, data flow, pseudocode, and where to start reading.

Level 4: Senior Engineer. Explain architecture, tradeoffs, coupling, tests, failure modes, and maintainability.

Level 5: Staff Engineer. Explain system implications, extensibility, operations, scaling, alternatives, and long-term risk.

## Interaction Pattern

Use this loop:

```text
1. Name the current level and section.
2. Explain the section.
3. Separate confirmed facts from inferred intent when relevant.
4. Ask exactly one check-in question.
5. Wait for the user's response before moving on.
```

Good check-in questions:

- "Does that match what you expected, or should I unpack the product behavior?"
- "Want to go one level deeper here before I continue?"
- "Should I show the exact files behind this part?"
- "Is this clear enough to move to the next flow?"

## Handling Missing Context

- If the codebase or diff is unavailable, explain what is missing and ask the user for the smallest artifact needed.
- If tests or runtime behavior are needed to answer a question, inspect or run them when feasible.
- If the user asks why a decision was made and the code does not prove it, distinguish likely rationale from unknown intent.
- Do not write files by default. Only write or update a report when the user asks or repo-local settings explicitly say interactive walkthroughs should create artifacts.
