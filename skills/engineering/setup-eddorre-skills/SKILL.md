---
name: setup-eddorre-skills
description: Configure a repository for the unvibe and teach-diff skills by recording where code explanation reports should be saved, how report files should be named, and how interactive walkthroughs should use saved reports. Run before first use of unvibe or teach-diff in a repo, or when those skills do not know where to write or find explanation artifacts.
---

# Setup Code Explanation Skills

Scaffold the per-repo configuration that `unvibe` and `teach-diff` read before explaining code changes.

This is a prompt-driven setup skill. Explore, present what you found, show a draft, stop for explicit confirmation, then write.

Do not write or modify files until the user has confirmed the exact draft.

## Process

### 1. Explore

Inspect the current repo before asking questions:

- `AGENTS.md` and `CLAUDE.md` at the repo root: which agent instruction file already exists?
- `docs/agents/`: does prior setup output already exist?
- likely docs directories such as `docs/`, `.scratch/`, `notes/`, or `adr/`
- git status and branch info when useful

Do not assume the repo has any docs layout.

### 2. Present findings and ask

Summarize what exists and what is missing. Then ask the setup decisions one at a time.

Section A: Output directory.

Explain that `unvibe` can write durable Markdown reports, and it needs to know where those reports should live. Default to `docs/unvibe/` unless the repo already has a better docs convention.

Offer:

- `docs/unvibe/`: default for durable code explanation reports
- `docs/agents/unvibe/`: useful when agent-generated docs should live together
- `.scratch/unvibe/`: useful for local-only reports that should not be committed
- custom path: use the user's exact preference

Section B: File naming.

Explain that deterministic names make reports easy to find later. Default to:

```text
YYYY-MM-DD-slug.md
```

Examples:

```text
2026-06-04-main-head-auth-flow.md
2026-06-04-uncommitted-payment-ui.md
```

Section C: Default write behavior.

Explain that the skill can either always write reports, ask before writing, or write only when requested. Default to ask before writing unless the user says they want file artifacts by default.

Offer:

- ask before writing
- always write reports
- chat-only unless requested

Section D: Interactive walkthrough behavior.

Explain that `teach-diff` should usually teach in chat, but it can read saved reports from the configured output directory. Default to chat-only teaching with optional report lookup.

### 3. Confirm and edit

Show the user a draft of:

- the `## Code explanation skills` block for `AGENTS.md` or `CLAUDE.md`
- the full contents of `docs/agents/code-explanation.md`

Use this confirmation format:

```text
Draft to write:

<AGENTS.md or CLAUDE.md> gets this block:

<markdown block>

I'll also create/update:

docs/agents/code-explanation.md with:

<markdown document>

Confirm and I'll write it.
```

Stop after showing the draft. Do not call file editing tools yet.

If the user asks for changes, revise the draft and show it again. Only write after the user explicitly confirms.

### 4. Write

Pick the file to edit:

- If `AGENTS.md` exists, edit it.
- Else if `CLAUDE.md` exists, edit it.
- If neither exists, ask the user which one to create.

If a `## Code explanation skills` block already exists, update it in place. Do not append a duplicate.

Use this block:

```markdown
## Code explanation skills

This repo is configured for `unvibe` and `teach-diff`.

- Report settings live in `docs/agents/code-explanation.md`.
- `unvibe` reads those settings before creating code-change reports.
- `teach-diff` reads those settings before looking for saved reports or teaching a change interactively.
```

Then create or update `docs/agents/code-explanation.md` with:

```markdown
# Code Explanation Skill Settings

## Report Output

- Directory:
- Naming:
- Default write behavior:

## Interactive Walkthroughs

- Default behavior:
- Saved report lookup:

## Notes

- `unvibe` should inspect code evidence before writing.
- `teach-diff` should teach conversationally and ask one check-in question at a time.
- Agents should distinguish confirmed facts, inferred intent, and unknowns.
```

Fill in the blanks from the user's choices.

### 5. Done

Tell the user setup is complete and name the files written. Mention that they can edit `docs/agents/code-explanation.md` directly later.
