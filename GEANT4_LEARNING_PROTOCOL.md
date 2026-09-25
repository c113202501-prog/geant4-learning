# Geant4 Learning Protocol

## Goal

Build a transferable mental model of a real particle experiment:

`physics question → source → interaction → transport → detector → signal/scoring → observable → interpretation`

## Teaching loop

1. **Locate** the concept in the experiment/simulation chain.
2. **Model** the expert reasoning, definitions, data flow, runtime behavior, and design purpose.
3. **Check prerequisites** with one low-level question.
4. **Coach/scaffold** one small code-reading or calculation task.
5. **Articulate**: learner explains the result in their own words.
6. **Consolidate**: compare learner answer, correct model, mismatch, and cause.
7. **Predict → modify → run → compare** only after the schema exists.
8. **Extract** one transferable rule and test it later.

Use worked examples for unfamiliar Geant4 APIs; fade support as domain expertise grows. Productive failure is allowed only when the learner has enough prior structure and a consolidation step follows.

## Required distinctions

- `[FRAMEWORK]`: required Geant4 interface/behavior.
- `[USER]`: physics, detector, analysis, or readout choice.
- `[EXAMPLE]`: replaceable organization used by this exercise.
- Physical process ≠ energy deposit ≠ detector response ≠ hit/scorer ≠ reconstructed observable.
- Implementation complete ≠ verified ≠ understood ≠ independent.

## Knowledge status

- `SEEN`: introduced.
- `UNDERSTOOD`: learner explains the causal model.
- `INDEPENDENT`: completes a comparable task without stepwise scaffolding.
- `TRANSFERRED`: succeeds when conditions change.
- `RETAINED`: recalls after delay.

## Documentation rule

- `LEARNING_STATE.md`: short resume state.
- `LEARNING_PROGRESS.md`: chronological milestones and evidence.
- `notes/`: durable concept notes.
- Git Markdown is canonical; Notion mirrors student-facing summaries.

