# Agent Router

This repository is a learning-first Geant4 workspace. Preserve executable evidence and the learner's demonstrated understanding as separate facts. A successful build or run is never proof of mastery.

## Cold-start route

Read in this order:

1. `AGENTS.md` — authority, routing, and update rules.
2. `LEARNER_PROFILE.md` — stable, cross-domain learning preferences.
3. `LEARNING_STATE.md` — sole source of current exercise, pending question, mastery, and next step.
4. Only the current note or source linked from `LEARNING_STATE.md`.

Read conditionally:

- `LEARNING_PROGRESS.md` for chronology or prior evidence.
- `GEANT4_LEARNING_PROTOCOL.md` before substantial tutoring or assessment.
- `GEANT4_PHYSICS_KNOWLEDGE_MAP.md` when locating a concept in the experiment chain.
- `ENVIRONMENT.md` before build, run, or path-dependent work.

Do not scan the repository broadly when these files answer the question.
If newer relevant progress evidence appears to contradict or postdate the state, flag possible staleness and reconcile `LEARNING_STATE.md` before teaching.

## Authority and update routing

| Information | Canonical location | Update rule |
|---|---|---|
| Current exercise, pending question, next step, active misconception | `LEARNING_STATE.md` | Replace stale current state; keep compact |
| Demonstrated milestone or verification evidence | `LEARNING_PROGRESS.md` | Append only; never maintain a second current-state block |
| Stable learner preferences | `LEARNER_PROFILE.md` | Update only after repeated or explicit confirmation |
| Geant4 tutoring procedure and mastery criteria | `GEANT4_LEARNING_PROTOCOL.md` | Domain-operational rules only |
| Physics/concept relationships | `GEANT4_PHYSICS_KNOWLEDGE_MAP.md` | Concept map only; no progress tracking |
| Verified paths and commands | `ENVIRONMENT.md` | Update after environment verification |
| Durable concept/exercise explanation | `notes/` | Preserve evidence, misconceptions, and transfer rules |
| Student-facing notes and review schedule | Notion | Projection only; scheduling/history may live there |

Conflict resolution:

- Git Markdown wins for current state, mastery, implementation, and verification.
- Notion wins for review scheduling.
- `LEARNING_STATE.md` wins over old summaries elsewhere in Git.
- Preserve a meaningful misconception in the current note or progress log before removing it from active state.

Use `sync_queue` in `LEARNING_STATE.md` only for concrete projections still owed to Notion, including useful misconception-review items when direct Notion access is unavailable. Never claim a sync without verification; remove an item after confirmed synchronization.

## Interaction and teaching

- Default learner-facing language: Traditional Chinese.
- Before substantive tutoring, consult the protocol and current state.
- Follow: physical meaning → Geant4 abstraction → minimal C++ → runtime behavior → design reason.
- For an unfamiliar domain concept, model one complete example before guided questions.
- Teach one necessary concept at a time and consolidate each learner answer.
- Label `[FRAMEWORK]`, `[USER]`, and `[EXAMPLE]` when the distinction matters.
- Distinguish implementation, verification, and understanding status.
- Never mark `UNDERSTOOD` without the learner's explanation or `INDEPENDENT` from scaffolded work.
- Do not reteach demonstrated prerequisites unless current evidence exposes a gap.

## Before editing code

1. Locate the change in `physics question → source → transport → detector → signal/scoring → observable`.
2. Show the relevant repository code and explain its current behavior.
3. Ask for a prediction only after prerequisites have been modeled.
4. Make the smallest relevant change; build/run; compare Prediction vs Actual; extract a transfer rule.
5. Update `LEARNING_STATE.md` and append a meaningful milestone to `LEARNING_PROGRESS.md`.

## Scope and environment guardrails

- Do not modify unrelated exercises.
- Do not commit build artifacts, generated score files, Geant4 installations, or downloaded binaries.
- Never use macOS ARM64 executables in WSL x86_64.
- Prefer targeted `rg`, `git status`, and `git diff`.
- For verified paths and setup, read `ENVIRONMENT.md`; do not duplicate them here.
