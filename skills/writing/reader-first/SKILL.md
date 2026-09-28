---
name: reader-first
description: Shape agent-written text so a person can read it and act on it without wasted effort. Covers what to include, what to cut, and what order to put it in. Use when writing or revising anything a human will read, such as PR descriptions, review reports, commit messages, Linear or Slack updates, design docs, handoff notes, and long chat replies. Also use when the user says the output is too long, asks for a tl;dr, or asks to make something readable.
---

# Reader first

An agent can write in seconds what takes a person ten minutes to read. This skill makes sure the reader's time goes to what they need. It decides what to include, what order to put it in, and what to cut. For sentence-level style, run `unslop` afterward.

The rules come from research on reading and comprehension. `references/evidence.md` gives the sources behind each rule.

## Workflow

1. Identify the reader.
2. Write down, for yourself, the one thing the reader must do or know after reading.
3. List what must be kept.
4. Draft the text, or take the existing text if you're rewriting.
5. Apply the edits below, in order.
6. Run the final check.

### 1. Identify the reader

When the text is a reply to the user in this conversation, you already know the reader. Use what they've shown about their expertise.

When other people will read the text, ask the user before writing, unless they already told you. Ask one question that covers:

- who will read it (for example, the PR reviewers, a PM, the on-call engineer)
- what those readers already know about this area
- what they need to do with the text (approve, decide, debug, get the gist)

Keep the answer in mind for the rest of the task. Don't ask again for later text meant for the same readers.

Detail that helps a newcomer slows an expert down, and the reverse. Fit the depth to the answer you got. If the user can't say, assume a competent peer in the field who has none of this session's context. They won't need the general background, but they will need what happened here: what you tried, what you ruled out, and why.

### 2. Name what the reader must do or know

Write one sentence, for yourself, that says what the reader should do or know after reading. For example: "Reviewer should check the retry cap and approve." If you can't write it, you don't know yet what the text is for. Work that out before drafting.

### 3. List what must be kept

Cutting is the main job, but some content can't be cut. Before editing, list what the user or the skill that produced the text requires, and keep all of it. Examples are the cited sources a review skill requires, a template's mandatory sections, and severity labels. Always keep AI-authorship disclosures and attribution lines, such as "Generated with Claude Code", a Copilot note, or a Co-Authored-By trailer. They aren't process narration. If the rewrite changed the text, you can add that it was rewritten.

"Required" means it has to be present. It doesn't have to stay at its current length, so make it as short as it can be and still do its job:

- Citations become a short tag after the claim, such as "(Nygard, *Release It!*)". The full list goes in a sources section at the end, one line per work. Cite each work once per claim. If one work backs two different findings, a short tag in each is fine.
- A required section that records process or coverage, such as "Lenses applied" or "What I read", becomes one or two lines at the end.
- A template's fixed section headings stay as they are. Headings you write yourself, such as the headings for individual findings, state a claim.

If the required and actionable content still goes over the reading-time ceiling, deliver it anyway. Don't pad it, and don't cut required content to fit. Then tell the user in one line that the calling skill's template makes the output longer than the reader's budget, so they can decide whether to change the template.

### 4. When rewriting existing text

A rewrite may change length, order, and wording, but not what the text claims. Keep:

- Conditions and hedges. "If the service starts from an empty log, deleting the table resets everyone's opt-outs" must not become "deleting the table resets everyone's opt-outs".
- The strength of each claim. Don't turn "bounded" into "small enough", or "likely" into "will".
- Concrete recommendations. Cut the explanation around a recommendation, not the specifics in it. "Fail closed for marketing, defer reminders" must not become "define a fallback".
- Severity and ranking labels, if the original had them.

Don't add structure the text doesn't deliver. If the opening promises "five reasons below", there must be five.

## The edits

Apply these to the draft in order. Each one fixes a common failure in agent-written text.

### Lead with the outcome

The first sentence states the result, decision, or request. The title or subject line does the same. Background comes after, and only if the reader needs it.

Readers decide within seconds whether to keep going, and skimmers read the start of each section and paragraph most closely. Anything important that isn't at the top may never get read.

### Put anything that needs action where it will be read

If the reader has to approve, decide, check, or do something, say so in the opening lines. Don't count on "see details below". Readers rarely go past the top layer of a document, so anything that needs action and sits only in an appendix or a later section is likely to be missed.

### Cut the process story

Delete narration of how you did the work ("I started by exploring...", "After reviewing the files...", "I then checked..."). Keep a step only if the reader needs it to trust the result, and then state it as evidence: "Replayed 41 failed orders against staging; all synced."

Also delete sections that exist to show effort: lists of files read, lenses applied, tools used.

### Cut what the reader already has

Don't restate things the reader can already see:

- the diff, file list, or commit list in a PR description
- the question they just asked
- the contents of a document they wrote
- general background an expert in the field already knows

Interesting details that aren't needed do real harm. They pull attention away from the main points, most of all when they come first.

### Open each section and paragraph with its point

Headings say something ("Retries block the worker for up to 2 minutes"), not just name a topic ("Retry behavior"). The first sentence of each paragraph carries its claim, and the rest of the paragraph supports it. A reader who reads only headings and first sentences should come away with the argument.

Only use headings when the text has more than one section. A three-paragraph reply doesn't need them.

### Limit how many things the reader must hold at once

People can hold about four things in working memory. If a text has more than about four findings, options, or steps that each need real thought, explain the most important few fully. List the rest one line each, or say they exist and offer them.

This limit is an inference from working-memory research, not a tested rule for documents. Use judgment. Never drop something the reader must act on. If more than four things need action, keep all of them. Group them where you can. In a review report, that could be "Before merging", "Soon after", and "Only if you keep the current design". In a consultation, group them into build steps. Template metadata for each finding, such as severity, lens, and evidence, can go on one line.

When a finding's severity depends on something unknown, say so inside the finding: "Blocker if refunds can be retried by the client; otherwise Change."

### Put evidence next to the claim

Each claim sits next to what supports it: the file and line, the log count, the test result, the source. Don't gather the claims in one place and the evidence in another.

### Make claims checkable, and state real uncertainty

Replace confident but vague wording with specifics the reader can verify:

- "comprehensive tests" becomes "12 tests; covers the retry cap and the dead-letter path"
- "significantly faster" becomes "p95 dropped from 800 ms to 120 ms"
- "should be safe" becomes the reason it's safe, or "I haven't verified X"

Don't lengthen an explanation to sound more convincing. Longer explanations make readers more confident in AI output without making them more accurate, so padding misleads the reader. When something is inferred or unverified, say so in a few words, at the point where it matters.

### Name what you left out

If you deliberately left out something the reader might expect, say so in one line: "Not in this PR: `payments/retry.py` does the same job." One line keeps the reader from wondering whether it was missed, without making them read it.

### Choose the format by the shape of the content

- Parallel facts about several items (options, before and after, one row per case) go in a table.
- Short items of the same kind go in a bulleted list.
- Reasoning, tradeoffs, and anything with "because" go in prose. Bullets break up the logic, and readers remember less of the prose around them.

### Write plain sentences, even for experts

Avoid clauses nested inside clauses, jargon where a plain word works, and passive voice that hides who acted. These slow down expert readers too. `unslop` has the detailed rules.

Don't aim for a readability-formula score. Those scores predict comprehension poorly.

## Final check

Before sending, check the draft:

1. The first two sentences give the outcome and any action needed.
2. Reading only the headings and first sentences gives the reader the argument.
3. Nothing restates what the reader already has.
4. No sentence describes your process unless it serves as evidence.
5. Every claim that matters can be checked, or is marked unverified.
6. Everything the user or the calling skill required is still there. In a rewrite, no condition, hedge, or concrete recommendation was lost.
7. Estimated reading time fits the reader's situation. Count all words, code included, and divide by 200 for technical text or 240 for general prose. Code reads slower than prose, so a text heavy with code takes longer than the estimate. Rough ceilings:

   | Text | Ceiling |
   | --- | --- |
   | Commit message, short chat answer | 1 min |
   | PR description, status update | 2 min |
   | Review report, consultation, design doc | 5 min |

   Choose the ceiling by what the text does, not where it appears. A design recommendation delivered in chat is a consultation, not a chat reply. The ceilings are judgment calls, not research findings. Going over one means you should find out what's making the text long and cut that, but don't cut required or actionable content to fit.

Use the reading-time estimate as a check on yourself. Don't print "X min read" on the text, except on a long document such as a design doc or report, where the reader may want to schedule time for it.

## Adapting to the type of text

- PR description. The title says what changes and why. Then give the problem, the fix, and a "please check" pointing at the decision that most needs review, with its file and lines. If there are several decisions, list them. If the branch isn't ready to merge, say so in the first line, then list what blocks it. Then give testing: say what you ran and what it showed, and name what you didn't test. Never imply a test was run when it wasn't. Check every claim against the diff. If the diff does something the description doesn't mention, or contradicts it, say so. Don't list files or restate the diff.
- Review report. Start with the verdict and the findings that block merging. Explain the top few findings fully and give the rest one line each. Put the evidence next to each finding. Keep any citations the review skill requires, in short form.
- Consultation ("how should we build X?"). Treat it like a design doc: the recommendation first, then the options in a table, then the steps to build it, with the risks attached to the step where each one bites.
- Commit message. The subject line is the change. The body says why, if that isn't obvious.
- Status update or Linear comment. Lead with the state and what's needed from the reader. Then what changed since the last update. Skip what they already know.
- Chat reply. Answer first. Stop when the information stops, without a recap or an offer to do more unless there's a real choice to make.
- Design doc. Put the decision or recommendation and the open questions at the top. Detail is fine further down, but anything that needs a decision appears first.

For readers outside software, each field has its own conventions:

- Medicine: put the assessment and plan first.
- Law: keep defined terms exact, but untangle the sentence structure.
- Business, government, and military: put the bottom line up front, keep it to one page, and put the request in the first paragraph.
- Anything for patients or the public: write at a general-audience reading level.

`references/evidence.md` covers these in more detail.

## Example

`references/examples.md` shows a PR description before and after these edits, with the reason for each change.
