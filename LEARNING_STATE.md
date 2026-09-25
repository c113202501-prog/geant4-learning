# Geant4 Learning State

LAST UPDATED: 2026-09-25 (Asia/Taipei)

## CURRENT EXERCISE

HandsOn02 / Exercise 4 — Sensitive Detector, Hit, Readout, and TOF matching.

## CURRENT CONCEPT

`G4Step → Sensitive Detector → raw hit → readout/digit → ntuple → reconstructed observable`, with Monte Carlo truth kept separate from detector-level reconstruction.

## CURRENT QUESTION

Given 90 reconstructed hit pairs, 72 truth-confirmed pairs, and 120 truth-matchable cases: calculate purity and efficiency, then explain the usual trade-off when matching cuts are loosened.

## LAST VERIFIED RUN

- 2026-09-24 `[CODEX-VERIFIED]`: HandsOn02 built successfully (`[100%] Built target G4tut`).
- `scoring-batch.mac` exited 0 and produced 1803-line `eDep.txt` and `nOfStepGamma.txt` files outside Git.
- Exercise 4 threshold/digitization changes have **not** been implemented or run.

## WHAT THE STUDENT CAN EXPLAIN

- Step/track/particle and energy-deposit distinctions.
- Raw hit vs readout/digit; threshold belongs after channel/time-window integration in the realistic model.
- Same-strip hits should accumulate `edep` and retain the earliest time.
- Scalar ntuple fields cannot preserve multiple hit identities; parallel vectors require equal lengths and aligned indices.
- `trackID` is Monte Carlo truth for validation, not reconstruction input.
- Earliest hits in two detectors may come from different particles because one event can contain multiple tracks and detector acceptances differ.

## SHOWN BUT NOT YET MASTERED

- Purity/efficiency calculation and matching-cut trade-off: introduced, awaiting learner answer.
- Threshold, time-window integration, vector ntuple output, and digitization: designed conceptually, not implemented.
- Exercise 4 remains scaffolded; not `INDEPENDENT` or `TRANSFERRED`.

## KNOWN MISCONCEPTIONS / CONFUSIONS

- Reading `edep` in `ProcessHits()` does not mean the hit stores it.
- `ProcessHits()` returning `true` does not itself create a hit.
- Raw Geant4 hit is not automatically a real electronic signal.
- Event-wide accumulation is not automatically an electronics integration window.
- Successful execution is not evidence of learner mastery.

## NEXT SINGLE LEARNING STEP

Let the learner answer the pending purity/efficiency question; consolidate the denominators and cut trade-off before any Exercise 4 code modification.

## DO NOT SKIP

- Do not jump directly to implementing `fEdep`, threshold, or vector ntuple output.
- Do not use `trackID` as detector reconstruction input.
- Do not return to geometry basics already passed unless a new error demonstrates the need.

## HANDOFF GAPS

- Exact JLab worksheet wording/numbering for Exercise 4 has not been copied into Git.
- Exercise 4 source currently studied is Geant4 basic/B5 under the local Geant4 installation, not yet copied into this repository.
- No verified detector electronics parameters exist yet: threshold value, integration-window width, noise, gain, or ADC/TDC model remain teaching assumptions.

