# AGENTS.md

This repo follows **Discipline First**: clarity first, guardrails always, smallest diff that works.

## Non-negotiables
- Do not change public APIs unless explicitly permitted.
- No big diffs. Prefer the smallest change that satisfies acceptance criteria.
- Never remove or weaken auth, validation, security checks, or audit logging without explicit permission.
- Do not delete files unless asked. If deletion is needed, explain why and list the files first.
- Do not introduce new frameworks/libraries unless explicitly requested. Prefer existing patterns.

## The Agent Brief (required)

Before writing or changing production code, create an **Agent Brief** in the PR description (or in an issue/comment) using this template.
If any field is unknown, ask before guessing.

### Agent Brief Template

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
1. Create or confirm the **Agent Brief** (above). If missing, write it first.
2. Propose a plan in small steps (max 5) mapped to acceptance criteria.
3. Make the smallest code change that satisfies *one* slice of the brief.
4. Add/modify tests. If tests are missing, write them. Tests are the spec.
5. Run tests and include the exact command(s) and summary of results.
6. Summarize: what changed, why, how to verify, and rollback plan.

## Guardrails
- Tests are the spec. If behavior matters, it must be covered by tests.
- Prefer refactors only after tests are green.
- Keep changes observable: logs/metrics/traces where relevant.
- Avoid broad package moves or “cleanup” sweeps.
- If a dependency change seems necessary: propose it first with alternatives.

## Commands
Use the repo’s build tool. If unsure, ask before guessing.

### Gradle
- Build: `./gradlew clean build`
- Unit tests: `./gradlew test`
- Integration tests (if present): `./gradlew integrationTest`
- Spotless/format (if present): `./gradlew spotlessApply`
- Check: `./gradlew check`

### Maven
- Build: `./mvnw -q -DskipTests=false clean verify`
- Unit tests: `./mvnw -q test`
- Integration tests (Failsafe): `./mvnw -q verify -DskipITs=false`

If commands differ in this repo, follow the README or CI config.

## Java conventions
- Prefer immutable data where reasonable.
- Prefer constructor injection (if using Spring).
- Avoid reflection-heavy “magic” unless the codebase already uses it.
- Keep exception handling explicit; don’t swallow exceptions.
- Keep logging structured and at appropriate levels.