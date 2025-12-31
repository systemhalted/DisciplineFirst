# AGENTS.md

This repository is **documentation and templates only** for the **Discipline First** framework.

Your job here is to keep the kit **clear, copy-pasteable, and correct**.

## Scope
Allowed:
- Edit markdown docs (`README.md`, guides, templates)
- Add/update starter-pack files (templates under `starter-pack/`)
- Add examples (Agent Briefs, rules files) as markdown or template files
- Fix typos, tighten language, improve structure

Not allowed (unless explicitly requested):
- Adding application code
- Adding dependencies
- Introducing CI/build pipelines
- Large reorganizations or renames

## Non-negotiables
- Prefer **small diffs**. One change per PR when possible.
- Do not delete or rename existing files unless explicitly requested.
- Keep templates **generic** and **tool-agnostic** unless a folder is explicitly tool-specific.
- Do not invent commands, URLs, or capabilities. If uncertain, ask.
- Preserve existing tone: practical, standards-first, no hype.

## Change Brief (required, human-owned)

Before making changes, ensure there is a short brief in the PR description or issue:

- **Goal:**  
- **Non-goals:**  
- **Scope:** (files/sections)  
- **Acceptance criteria:** (what must be true for this to be done)

If the brief is missing or ambiguous, **stop and ask for it** before editing templates.

## How to work
1. Confirm the **Change Brief** exists (Goal, Non-goals, Scope, Acceptance criteria).
2. Restate the brief in 3–5 bullets.
3. Propose a plan (max 5 steps).
4. Make the smallest change that satisfies the brief.
5. Verify:
   - links you add are valid
   - templates remain copy-pasteable and safe-by-default
   - no invented claims or unverified URLs were introduced
6. If you add a new template, update `README.md` (or the relevant index doc) to link it.
7. Summarize: what changed, where it lives, and how a user should apply it.

## Guardrails (docs repo edition)
- Prefer **small diffs** and keep changes narrowly scoped.
- Keep templates safe-by-default (avoid destructive instructions).
- Avoid “tool wars” and model hype. This kit is model-agnostic.
- Do not add sources you haven’t verified.
- If a change affects guidance, update examples and links together.

## Template quality bar
All templates must be:
- Copy-paste friendly
- Clearly scoped (what problem they solve)
- Safe by default (avoid destructive instructions)
- Consistent with Discipline First principles (brief → guardrails → verification)

## Starter packs
Starter pack templates live under:
- `starter-pack/<stack>/...`

Keep stack-specific assumptions inside the stack folder.  
Keep repo-wide explanations in `README.md`.

## If you’re adding or updating an Agent Brief template
This repository’s templates assume:
- The **Agent Brief is human-owned**
- Agents should **not fabricate** a brief
- Templates should support **incremental work** using brief levels (0/1/2)

If that’s not true for a new starter pack, state the difference explicitly in that starter pack’s docs.

## When in doubt
Ask one focused question before proceeding rather than guessing.