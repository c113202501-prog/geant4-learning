# Learning State

This is the sole canonical snapshot of the learner's current position. Historical evidence belongs in `LEARNING_PROGRESS.md`.

```yaml
last_updated: 2026-09-26
current_exercise: HandsOn02 / Exercise 4 — Sensitive Detector, Hit, Readout, and TOF matching
current_concept: G4Step → Sensitive Detector → raw hit → readout/digit → ntuple → reconstructed observable; Monte Carlo truth stays separate
pending_question: >-
  Given 90 reconstructed hit pairs, 72 truth-confirmed pairs, and 120 truth-matchable cases,
  calculate purity and efficiency, then explain the usual trade-off when matching cuts are loosened.
next_step: >-
  Let the learner answer the pending question; consolidate the two denominators and matching-cut trade-off
  before changing code.
active_misconception:
  - A ProcessHits return value does not itself decide whether a hit was created; control flow and collection insertion do.
  - A raw Geant4 hit is not automatically an electronics-level signal or digit.
  - Event-wide accumulation is not automatically a finite electronics integration window.
  - Reading edep from G4Step does not prove that HodoscopeHit stores edep.
relevant_mastery:
  - concept: step / track / particle distinction
    level: UNDERSTOOD
    evidence: learner explained why nOfStepGamma counts steps rather than gamma particles
  - concept: command-based scoring mesh, voxel indices, and coordinate transforms
    level: UNDERSTOOD
    evidence: learner converted a voxel index to local and world coordinates and explained mesh-resolution effects
  - concept: raw hit versus readout/digit and per-strip accumulation
    level: UNDERSTOOD
    evidence: learner described same-strip edep accumulation, earliest-time retention, and post-accumulation thresholding
  - concept: vector ntuple column alignment
    level: UNDERSTOOD
    evidence: learner explained why strip/time/edep vectors require equal lengths and stable bindings
  - concept: trackID matching
    level: UNDERSTOOD
    evidence: learner identified trackID pairing as Monte Carlo truth, not detector reconstruction input
  - concept: purity and efficiency denominators
    level: SEEN
    evidence: pending unassisted calculation and trade-off explanation
implementation_status:
  - HandsOn02 source builds in the verified WSL environment.
  - Command-based scoring for Exercise 3 was enabled and exercised.
  - Exercise 4 thresholding, finite time-window digitization, vector output, and reconstruction matching are not implemented.
verification_status:
  - 2026-09-24 HandsOn02 build succeeded.
  - Batch macro exited 0 and generated 1803-line scoring outputs outside Git.
  - No Exercise 4 electronics/readout implementation has been built or run.
current_note: notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md
do_not_skip:
  - Use the actual repository code before claiming current behavior.
  - Keep truth, raw hits, digits/readout, and reconstructed observables distinct.
  - Do not infer INDEPENDENT or TRANSFERRED mastery from scaffolded answers.
sync_queue: []
handoff_gaps:
  - Exact Exercise 4 worksheet wording is not present in the repository.
  - The studied B5 source exists only in the local Geant4 installation, not this repository.
  - No verified electronics threshold, integration window, noise, gain, timing resolution, or ADC/TDC model has been supplied.
```
