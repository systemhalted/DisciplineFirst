# Discipline First

**Discipline First** is a **trust pipeline for AI-assisted coding**.

AI-assisted coding is a force multiplier. Force multipliers multiply **your discipline or your chaos**.

If you bring clear intent, small tasks, and real guardrails (tests, contracts, CI, review), these tools feel magical.
If you don’t, you get rewrites, confusion, and that familiar “this tool can’t be trusted” aftertaste.

This repo is the **kit**: durable repo instructions, an **Agent Brief** template (human-owned), and lightweight rules that make AI-assisted work **reviewable, testable, observable, and shippable**.

Read the full essay:  
https://systemhalted.in/2025/12/31/discipline-first-trust-pipeline-for-ai-assisted-coding/

---

## What this is (and what it isn’t)

This is **model-agnostic**. It’s not “use model X” or “use tool Y”.

It’s a stance:

> The agent isn’t the methodology. **Your engineering habits are.**

Discipline First is **Extreme Programming (XP) with a faster pair**:
- The agent is the **pair**
- The human is the **driver**
- **Tests are the spec**
- **Continuous Integration is the referee**
- **Small releases** turn speed into reliability

---

## The pipeline

Discipline First has three parts:

1. **Agent Brief (human-owned)**  
   Clear intent that the agent cannot “creatively interpret”.

2. **Guardrails**  
   Tests, contracts, CI, architecture checks, review, and small diffs that keep reality close.

3. **Durable Repo Instructions**  
   Repo-level rules that persist across prompts and sessions (AGENTS.md, EditorConfig, tool rules).

---

## Quick start

### Option A: Copy the Java starter pack into your repo

Copy these files into your repo root (create directories as needed):

- `.editorconfig`
- `AGENTS.md`
- `.cursor/rules.md` (if you use Cursor)
- `.github/pull_request_template.md` (optional but recommended)

Starter pack location in this repo:

- `starter-pack/java/`

### Option B: Adopt only the minimum baseline

If you only do one thing:
- Add `AGENTS.md` (human-owned brief + guardrails)
- Add `.editorconfig`

That alone makes behavior more predictable across humans, agents, and editors.

---

## Durable repo instructions (what goes where)

### `.editorconfig`
Portable formatting rules across editors and IDEs.  
Use this for “style that must survive tools”.

### `AGENTS.md`
Repo-wide behavioral contract for agents (and humans):
- how to scope work
- how to validate changes
- what not to touch
- how to handle uncertainty  
Use this for “how to behave here”.

### Tool rules files (example: `.cursor/rules.md`)
Tool-specific persistence:
- what to include in context
- response style
- safety boundaries  
Use this for “how this particular tool should operate”.

---

## Agent Brief (human-owned)

The **Agent Brief is written by humans**. Agents should not invent it.

If a brief is missing:
- the agent **stops**
- asks for a brief
- points out ambiguity
- proceeds only after the human provides it

### Brief Levels (to support incremental work)

Not every change deserves a full PRD. Use the smallest level that keeps the change safe and reviewable.  
If scope expands or uncertainty stays high, **escalate** to the next level.

#### Level 0: Micro-change (≤ 30 minutes)
Examples: rename, small refactor, tweak a log line, adjust a test, fix a null check.

Human provides:
- **Goal**
- **Acceptance criteria** (2–4 lines total)

#### Level 1: Incremental change (1–2 days)
Examples: add a validation rule, add one metric, add a feature-flagged branch, adjust endpoint behavior.

Human provides:
- **Goal**
- **Constraints**
- **Acceptance criteria**
- **Test plan** (what must fail before it passes)

Optional (recommended when relevant): Interfaces, Observability, Risks, Recovery.

#### Level 2: New feature / risky change
Examples: new endpoint/workflow, auth/payments/data deletion, migrations, cross-service changes.

Human provides the **full Agent Brief**.

### Delta Brief (preferred for incremental changes)

For existing systems, a diff-shaped brief beats a PRD.

- **Existing behavior:** (1–3 bullets)
- **Desired behavior:** (1–3 bullets)
- **Scope:** (files/components/endpoints likely touched)
- **Out of scope:** (what must not change)
- **Acceptance tests:** (scenarios or tests to add/modify)
- **Risk:** (one line)
- **Recovery:** (one line)

### Full Agent Brief Template (Level 2)

- **Goal**
- **Non-goals**
- **Constraints** (APIs, performance, security, compatibility, compliance)
- **Interfaces** (endpoints/classes/events/configs affected)
- **Acceptance criteria** (testable outcomes)
- **Risks** (failure modes, security, data integrity)
- **Test plan** (unit/functional/contract; what must fail before it passes)
- **Observability** (logs/metrics/traces; what changes and where)
- **Dependencies** (services, libs, configs, approvals)
- **Recovery and blast radius** (feature flag, rollback steps, safe defaults)

Hard rules:
- Do not change public APIs unless explicitly permitted.
- Prefer the smallest diff that can satisfy the brief.
- Stop and ask when uncertain.

---

## Guardrails

Guardrails aren’t bureaucracy. They’re how you make truth show up faster than code.

Recommended guardrails:
- Unit tests and functional tests (tests are the spec)
- Contract checks (where applicable)
- Architecture checks (where applicable)
- Code review
- CI as referee
- Small tasks and **small diffs**

**Small diffs** are about control:
- easier review
- easier reasoning
- easier testing
- easier rollback  
Agents tend to widen scope unless constrained. “Small diffs” is a safety boundary.

---

## The one-week experiment (tests only)

A safe way to start without debating beliefs:

1. Pick **one service**
2. Pick **one real user workflow**
3. Add missing **functional tests** until the behavior is pinned down

You’ll know it’s working when:
- tests fail for the wrong behavior and pass for the right behavior
- tests are deterministic in CI (no flakes)
- tests don’t depend on environment quirks or real external systems
- suite is fast enough to run often
- any production code change for testability is small and justified
- humans can read the tests as a spec and agree it’s real

Measure boring reality:
- number of rewrites / restatements
- diff size
- review time
- time to “tests green”
- confidence (self-reported)
- defects/regressions (later)

---

## The four personas (why people report opposite experiences)

Same tools. Opposite stories. Usually because of discipline.

- **Skeptic**: “prove it” (standards-first, authorship-doubt)
- **Dismisser**: “already decided” (sometimes reflexive, sometimes reasoned)
- **Viber**: “speed is truth” (great for spikes, dangerous in prod)
- **Disciplined Builder**: “trust is built” (small diffs, tests, loops, observability)

Discipline First is the on-ramp from *any* persona to *reliable shipping*.

---

## Repo contents

- `starter-pack/java/`  
  Copy-paste templates:
  - `.editorconfig`
  - `AGENTS.md` (with brief levels + templates)
  - `.cursor/rules.md`
  - `.github/pull_request_template.md`

---

## Contributing

PRs welcome, especially:
- starter packs for other stacks (Node, Python, Go)
- example Agent Briefs (Level 0/1/2)
- minimal rules files for popular agentic tools
- “failure modes” and “what to do when it breaks” guidance

Contribution style:
- keep templates copy-paste friendly
- prefer small diffs
- avoid tool wars and model wars
- be explicit about tradeoffs

---

## License

This project is licensed under the MIT License. See `LICENSE`.