# Learning State

This is the sole canonical snapshot of the learner's current position. Historical evidence belongs in `LEARNING_PROGRESS.md`.

```yaml
last_updated: 2026-10-06
current_exercise: HandsOn03 / hodoscope Sensitive Detector implementation — learning checkpoint Exercise 4
current_concept: Separate verified raw HodoscopeHit data from the next readout-level threshold decision
pending_question: >-
  No detector threshold has been verified; decide whether the next step uses an explicitly labelled teaching value or waits for a real specification.
next_step: >-
  Explain where threshold belongs relative to raw-hit accumulation, then choose a non-deceptive parameter source
  before implementing any readout filtering.
active_misconception: []
relevant_mastery:
  - concept: step / track / particle distinction
    level: UNDERSTOOD
    evidence: learner explained why nOfStepGamma counts steps rather than gamma particles
  - concept: command-based scoring mesh, voxel indices, and coordinate transforms
    level: UNDERSTOOD
    evidence: learner converted a voxel index to local and world coordinates and explained mesh-resolution effects
  - concept: raw hit versus readout/digit and per-strip accumulation
    level: UNDERSTOOD
    evidence: learner predicted 0.24 MeV and 12 ns, then explained why zero-edep steps must not create or retime a hit
  - concept: vector ntuple column alignment
    level: UNDERSTOOD
    evidence: learner explained why strip/time/edep vectors require equal lengths and stable bindings
  - concept: trackID matching
    level: UNDERSTOOD
    evidence: learner identified trackID pairing as Monte Carlo truth, not detector reconstruction input
  - concept: purity and efficiency denominators
    level: UNDERSTOOD
    evidence: learner calculated purity and efficiency and explained truth-matchable cases and the cut trade-off
implementation_status:
  - HandsOn02 source builds in the verified WSL environment.
  - Command-based scoring for Exercise 3 was enabled and exercised.
  - HandsOn03 course baseline was copied into Git without build artifacts on 2026-10-06.
  - HodoscopeHit now stores fEdep; HodoscopeSD accumulates non-zero step deposits per strip and retains the earliest valid time.
  - EventAction retrieves both HodoscopeHitsCollection objects and prints strip ID, earliest valid time, and accumulated fEdep.
  - Exercise 4 thresholding, finite time-window digitization, vector output, and reconstruction matching are not implemented.
verification_status:
  - 2026-09-24 HandsOn02 build succeeded.
  - Batch macro exited 0 and generated 1803-line scoring outputs outside Git.
  - No Exercise 4 electronics/readout implementation has been built or run.
  - 2026-10-06 HandsOn03 configured and built successfully after normalizing invalid U+2003 whitespace from the course files.
  - run1.mac processed 100 events successfully.
  - verify-hits.mac processed one event and directly observed H1 strip 7 at 6.896 ns with 3.031 MeV and H2 strip 9 at 60.111 ns with 2.779 MeV.
current_note: notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md
do_not_skip:
  - Use the actual repository code before claiming current behavior.
  - Keep truth, raw hits, digits/readout, and reconstructed observables distinct.
  - Do not infer INDEPENDENT or TRANSFERRED mastery from scaffolded answers.
sync_queue: []
handoff_gaps:
  - Exact Exercise 4 worksheet wording is not present in the repository.
  - No verified electronics threshold, integration window, noise, gain, timing resolution, or ADC/TDC model has been supplied.
```
