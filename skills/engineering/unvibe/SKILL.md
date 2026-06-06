---
name: unvibe
description: Explain code changes at multiple audience depths and produce a Markdown after-action report. Use when the user asks what was built, wants to understand uncommitted changes, a commit range, a PR branch versus main, a recent agent-built project, or says phrases like "unvibe", "after action", "explain what I built", "code archaeology", "walk me through the diff", or "what happened in this codebase".
---

# Unvibe

Generate a source-grounded Markdown explanation of a code change for multiple audiences, from exec summary through staff-engineer review.

## Workflow

1. Determine the source range:
   - Use the user's explicit source if provided: uncommitted diff, commit range, branch comparison, PR, or named project path.
   - If unspecified inside a git repo, inspect `git status`, recent commits, and likely base branches before choosing a comparison.
   - If the project is not a git repo, inspect the file tree and recent artifacts, then state that no diff source was available.
2. Load repo-local output settings:
   - Look for a `## Code explanation skills` block in `AGENTS.md` or `CLAUDE.md`.
   - If present, read `docs/agents/code-explanation.md` or the path named in that block.
   - If settings exist, follow the configured report output directory, naming convention, and default write behavior.
   - If settings do not exist, default to chat output and ask before writing a file. Suggest running `$setup-eddorre-skills` when the user wants durable repo-level behavior.
3. Gather evidence before explaining:
   - Read the diff or changed files.
   - Inspect surrounding code, tests, package metadata, routes, schemas, and user-facing entry points as needed.
   - Run lightweight commands that clarify behavior, such as `rg`, `git diff --stat`, `git diff --name-only`, `git log`, and focused tests when appropriate.
4. Separate evidence from interpretation:
   - Label facts as `Confirmed From Code`.
   - Label likely purpose or rationale as `Inferred Intent`.
   - Label missing context as `Unknown / Needs Human Confirmation`.
5. Produce one Markdown report unless the user asks for an interactive walkthrough instead.
6. Save the report only when the user requested a file or the repo-local settings say to write reports. Create the configured output directory when needed.
7. Keep the report readable for a human catching up after a burst of coding. Prefer clear prose, short tables, and execution paths over exhaustive line-by-line commentary.

## Required Report Shape

Use this structure unless the user's requested format is more specific:

```markdown
# Code Change Explanation

## Source
- Mode:
- Base:
- Compared:
- Generated:
- Confidence:

## Level 1: Exec / Marketing

## Level 2: PM / Product

## Level 3: Junior Engineer

## Level 4: Senior Engineer

## Level 5: Staff Engineer

## Key Files
| File | Why It Matters | Evidence Level |
| --- | --- | --- |

## Important Flows

## Decisions and Tradeoffs

## Risks / TODOs / Unknowns

## Suggested Follow-up Questions

## Evidence Ledger
### Confirmed From Code
### Inferred Intent
### Unknown / Needs Human Confirmation
```

## Audience Depths

Level 1: Explain what changed, why it matters, and expected user or business impact. Avoid implementation detail.

Level 2: Explain product behavior, user flows, scope boundaries, edge cases, decisions made, and open product questions.

Level 3: Explain files touched, concepts involved, how the feature works, diagrams or pseudocode when useful, and where to start reading.

Level 4: Explain architecture, tradeoffs, local patterns, coupling, tests, failure modes, maintainability concerns, and likely review points.

Level 5: Explain system implications, extensibility, operational concerns, scaling, alternative designs visible from the code, and long-term risks.

## Evidence Rules

- Do not invent product intent, business rationale, or rejected alternatives. Infer only when the code, names, tests, comments, or surrounding patterns support the inference.
- When intent is unclear, say so plainly and give the exact code evidence that creates uncertainty.
- Prefer "appears to" and "likely" for inferences.
- Include file paths for important claims. Include line references when the claim depends on a small piece of code.
- If tests were not run, say that. If no tests exist for the changed behavior, call it out as a risk.
- If the codebase cannot be inspected deeply enough, reduce confidence instead of filling gaps.

## Useful Commands

Use commands appropriate to the repo and source mode:

```bash
git status --short
git diff --stat
git diff --name-only
git diff
git log --oneline --decorate -n 12
git branch --show-current
```

For branch comparisons, prefer the repository's actual base branch when discoverable. Common forms:

```bash
git diff main...HEAD --stat
git diff main...HEAD
```

Use `rg` to connect changed files to routes, entry points, tests, and callers.
