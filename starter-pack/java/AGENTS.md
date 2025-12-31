## Agent Brief (human-owned, required)

The **Agent Brief is written by humans** and is maintained here as the canonical template.

If no Agent Brief is provided in the PR description or issue, **do not proceed with production code changes**. Instead:
1. Ask the human to paste a filled brief (Level 0/1/2 below).
2. Point out missing sections or ambiguity.
3. Wait for the brief before implementing.

### Brief Levels (so this works for incremental work)

Use the smallest level that still makes the change safe and reviewable.  
If scope expands or uncertainty stays high, **escalate to the next level** before coding more.

**Level 0: Micro-change (≤ 30 minutes)**  
Examples: rename, small refactor, fix null check, tweak a log line, adjust a test.  
Human must provide:
- **Goal**
- **Acceptance criteria** (or “how we’ll know it worked”)

**Level 1: Incremental change (1–2 days)**  
Examples: add a small validation rule, add one metric, add a feature-flagged branch, update one endpoint behavior.  
Human must provide:
- **Goal**
- **Constraints**
- **Acceptance criteria**
- **Test plan** (at least: what must fail before it passes)

Optional (recommended when relevant): Interfaces, Observability, Risks, Recovery.

**Level 2: New feature / risky change**  
Examples: new endpoint/workflow, auth/payments/data deletion, migrations, cross-service behavior.  
Human must provide the **full Agent Brief** template.

### Delta Brief (preferred for incremental changes)

For existing systems, a diff-shaped brief is often better than a PRD.

**Existing behavior:** (1–3 bullets)  
**Desired behavior:** (1–3 bullets)  
**Scope:** (files/components/endpoints likely touched)  
**Out of scope:** (what must not change)  
**Acceptance tests:** (scenarios or tests to add/modify)  
**Risk:** (one line)  
**Recovery:** (one line)

### Full Agent Brief Template (Level 2)

**Goal:**  
**Non-goals:**  
**Constraints:** (APIs, performance, security, compatibility, compliance)  
**Interfaces:** (endpoints/classes/events/configs affected)  
**Acceptance criteria:** (testable outcomes)  
**Risks:** (failure modes, security, data integrity)  
**Test plan:** (unit/functional/contract; what must fail before it passes)  
**Observability:** (logs/metrics/traces; what changes and where)  
**Dependencies:** (services, libs, configs, migrations, approvals)  
**Recovery and blast radius:** (feature flag, rollback steps, safe defaults)

### Brief Hard Rules
- Do not change public APIs unless explicitly permitted.
- Prefer the smallest diff that can satisfy the brief.
- Stop and ask when uncertain.

## Workflow (always)
1. Confirm there is a **human-provided brief** (Level 0/1/2). If missing, stop and request it.
2. Restate the brief in 3–5 bullets (goal + acceptance criteria + constraints).
3. Propose a plan in small steps (max 5) mapped to acceptance criteria.
4. Make the smallest code change that satisfies *one* slice of the brief (one PR = one slice).
5. Add/modify tests. If tests are missing, write them. Tests are the spec.
6. Run tests and include the exact command(s) and summary of results.
7. Summarize: what changed, why, how to verify, and recovery/rollback plan.