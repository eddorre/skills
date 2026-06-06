# Code Explanation Skills

This repository contains agent skills for understanding an unfamiliar codebase, explaining recent code changes, and turning that explanation into an interactive walkthrough.

- `unvibe`: create a source-grounded Markdown report that explains what changed at several audience depths.
- `teach-diff`: walk through a code change interactively, one section at a time.
- `setup-eddorre-skills`: configure where reports should be saved in a repo.

Use `unvibe` when you want a durable written artifact. Use `teach-diff` when you want the agent to explain the work conversationally and pause for questions.

## Install

Install these skills with the `skills` CLI:

```bash
npx skills@latest add eddorre/skills
```

The npm package in this command is `skills`. This repository is the GitHub source that the installer downloads.

During install, pick the skills you want and the coding agents you want to install them on. Make sure you select `setup-eddorre-skills`.

Then run this in your agent:

```text
/setup-eddorre-skills
```

It will ask:

- where `unvibe` reports should be saved
- how report files should be named
- whether reports should be written automatically, written after asking, or kept chat-only unless requested
- how `teach-diff` should find saved reports

After setup, `unvibe` and `teach-diff` will read the repo-local settings before writing or looking up reports.

## Skills

### setup-eddorre-skills

`setup-eddorre-skills` answers the question: "Where should these skills save and find explanation artifacts in this repo?"

It writes repo-local guidance to an agent instruction file and to `docs/agents/code-explanation.md`.

Example prompt:

```text
/setup-eddorre-skills
```

### unvibe

`unvibe` answers the question: "What did we build, and what should I understand about it?"

It is useful for:

- uncommitted changes
- commit ranges
- a feature branch compared with `main`
- pull request branches
- recent agent-written code
- projects where you want a structured after-action explanation

Example prompts:

```text
/unvibe explain the uncommitted changes in this repo.
```

```text
/unvibe explain main...HEAD, with extra focus on architecture and risk.
```

```text
/unvibe explain the project at filesystem path ../my-app.
```

```text
/unvibe explain git commits abc123..def456.
```

The generated report is organized by audience level:

1. Exec / Marketing
2. PM / Product
3. Junior Engineer
4. Senior Engineer
5. Staff Engineer

It also includes key files, important flows, decisions and tradeoffs, risks, follow-up questions, and an evidence ledger.

The evidence ledger is the heart of the skill:

- `Confirmed From Code`: facts supported by files, diffs, tests, routes, configs, or other inspectable evidence.
- `Inferred Intent`: likely purpose or rationale based on code evidence.
- `Unknown / Needs Human Confirmation`: things the code does not prove.

This keeps the agent from turning a code summary into confident storytelling.

### teach-diff

`teach-diff` answers the question: "Can you teach me what changed without dumping everything at once?"

It is useful when:

- you want an interactive walkthrough
- you already have an `unvibe` report and want it explained
- you want to start at a non-technical level and go deeper gradually
- you want to ask for "show code", "skip", "go deeper", or "what could break"

Example prompts:

```text
/teach-diff walk me through this change from Level 1.
```

```text
/teach-diff use the unvibe report and explain one section at a time.
```

```text
/teach-diff teach me the architecture part, then quiz me lightly.
```

The skill follows a loop:

1. Name the current level and section.
2. Explain the section.
3. Separate confirmed facts from inferred intent when useful.
4. Ask one short check-in question.
5. Wait for your response before continuing.

## Typical Workflow

First, generate a report:

```text
/unvibe explain the git comparison main...HEAD.
```

Then, use the report as a teaching artifact:

```text
/teach-diff teach me the saved report at docs/unvibe/2026-06-04-main-head.md one section at a time.
```

You can also skip the report and start with the interactive walkthrough:

```text
/teach-diff explain the uncommitted changes in this repo.
```

In that case, the agent should gather the same code evidence before teaching.

## File Layout

```text
.
├── README.md
├── LICENSE
└── skills
    └── engineering
        ├── setup-eddorre-skills
        │   └── SKILL.md
        ├── teach-diff
        │   └── SKILL.md
        └── unvibe
            └── SKILL.md
```
