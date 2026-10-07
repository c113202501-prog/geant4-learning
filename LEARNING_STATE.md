# Learning State

This is the sole canonical snapshot of the learner's current position. Historical evidence belongs in `LEARNING_PROGRESS.md`.

```yaml
last_updated: 2026-10-07
current_exercise: HandsOn03 / hodoscope Sensitive Detector implementation — learning checkpoint Exercise 4
current_concept: Plan a separate event-integrated readout selection in EventAction while preserving raw hits
pending_question: >-
  None. The learner chose an inclusive illustrative threshold: accumulated strip edep >= 0.20 MeV passes.
next_step: >-
  Continue from the actual EventAction source: define what information the selected readout should retain
  before introducing vector output. Keep the readout selection separate from raw HodoscopeHitsCollection data.
  The learner chose >= 0.20 MeV for the EXAMPLE event-integrated teaching threshold; this is not a verified
  detector specification, no threshold/readout code has been changed, and no finite integration-window model is implied.
active_misconception: []
relevant_mastery:
  - concept: preserve raw hits while selecting readout data
    level: UNDERSTOOD
    evidence: learner explained that 0.24 and 0.08 MeV give two raw hits but one readout at a 0.20 MeV teaching threshold; the rejected raw hit remains
  - concept: event-integrated threshold uses accumulated per-strip edep
    level: UNDERSTOOD
    evidence: after one corrected attempt, learner independently summed 0.04 + 0.06 + 0.10 = 0.20 MeV and correctly applied the chosen >= 0.20 MeV boundary; learner also correctly selected strip 5 at 0.20 MeV and strip 9 at 0.28 MeV while rejecting strip 2 at 0.13 MeV
  - concept: time information lost by event-level compression
    level: UNDERSTOOD
    evidence: learner explained that total edep and earliest time cannot recover window energies; per-step timestamps paired with edep or time bins are needed
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
  - Do not repeat the already answered boundary, raw/readout-count, accumulated-edep, or time-information questions.
  - Use existing general knowledge efficiently; inspect only relevant reference pages for exact source claims and OCR only needed unreadable pages.
  - Use the actual repository code before claiming current behavior.
  - Keep truth, raw hits, digits/readout, and reconstructed observables distinct.
  - Do not infer INDEPENDENT or TRANSFERRED mastery from scaffolded answers.
sync_queue: []
handoff_gaps:
  - Exact Exercise 4 worksheet wording is not present in the repository.
  - No verified electronics threshold, integration window, noise, gain, timing resolution, or ADC/TDC model has been supplied.
```
