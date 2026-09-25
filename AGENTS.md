# Agent Instructions

## Purpose

This repository is a learning-first Geant4 workspace. Preserve both executable evidence and the learner's actual understanding; never treat a successful build/run as mastery.

## Start here

1. Read `LEARNING_STATE.md` before broad exploration.
2. Read only the linked note/source files needed for the current question.
3. Use `LEARNING_PROGRESS.md` only when chronology or older evidence is needed.

## Teaching rules

- Follow: physical meaning → Geant4 abstraction → minimal C++ → runtime behavior → design reason.
- For a new domain concept, use Modeling first; then low-level confirmation, guided practice, self-explanation, reflection, and only then prediction/independent exploration.
- Teach one necessary concept at a time and complete consolidation after each learner answer.
- Label `[FRAMEWORK]`, `[USER]`, and `[EXAMPLE]` choices when useful.
- Distinguish implementation status, verification status, and understanding status.
- Do not mark `UNDERSTOOD` without learner explanation; do not mark `INDEPENDENT` from scaffolded work.

## Before editing code

1. Locate the change in `physics question → source → transport → detector → signal/scoring → observable`.
2. Show the relevant real repository code and explain its current behavior.
3. Ask for a prediction only after prerequisites have been modeled.
4. Make the smallest relevant change; build/run; compare Prediction vs Actual; extract a transfer rule.
5. Update `LEARNING_STATE.md` and add a meaningful milestone to `LEARNING_PROGRESS.md`.

## Environment

```bash
source /home/sundae/geant4/install/bin/geant4.sh
```

- B1 build: `/home/sundae/jlab-build/HandsOn01-B1`
- HandsOn02 build: `/home/sundae/jlab-build/HandsOn02-baseline`
- See `ENVIRONMENT.md` for verified paths and commands.

Do not commit build artifacts, generated score files, Geant4 installations, or downloaded binaries. Never use the macOS ARM64 executables in WSL x86_64.

## Scope

- Do not modify unrelated exercises.
- Git Markdown is canonical; Notion is a student-facing projection.
- Prefer targeted `rg`, `git status`, and `git diff` over repository-wide analysis.

