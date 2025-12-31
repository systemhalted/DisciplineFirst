# AGENTS.md

This repo follows **Discipline First**: clarity first, guardrails always, smallest diff that works.

## Non-negotiables
- Do not change public APIs unless explicitly permitted.
- No big diffs. Prefer the smallest change that satisfies acceptance criteria.
- Never remove or weaken auth, validation, security checks, or audit logging without explicit permission.
- Do not delete files unless asked. If deletion is needed, explain why and list the files first.
- Do not introduce new frameworks/libraries unless explicitly requested. Prefer existing patterns.

## Workflow (always)
1. Restate the goal and acceptance criteria in 3–5 bullets.
2. Propose a plan in small steps (max 5).
3. Make the smallest code change.
4. Add/modify tests. If tests are missing, write them.
5. Run tests and include the exact command(s) and summary of results.
6. Summarize: what changed, why, how to verify, and rollback plan.

## Guardrails
- Tests are the spec. If behavior matters, it must be covered by tests.
- Prefer refactors only after tests are green.
- Keep changes observable: logs/metrics/traces where relevant.
- Avoid broad package moves or “cleanup” sweeps.

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
