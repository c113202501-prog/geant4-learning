# Current Learning State

## Location / exercise

HandsOn02 / Exercise 4 — Sensitive Detector, Hit, Readout, and TOF matching.

## Current concept

```text
G4Step → Sensitive Detector → raw hit → readout/digit → ntuple → observable
```

Monte Carlo truth must remain separate from detector-level reconstruction.

## Can explain

- Why `ProcessHits()` return value does not itself create a hit.
- Why reading `edep` does not mean the hit stores it.
- Same-strip energy accumulation and earliest-time retention.
- Raw hit vs thresholded readout/digit.
- Scalar vs vector ntuple storage and aligned-index invariants.
- Why earliest hits in two detectors need not belong to the same particle.
- Why `trackID` is validation truth, not reconstruction input.

## Not yet completed

- Purity/efficiency application question is awaiting an answer.
- Threshold, integration window, vector ntuple output, and digitization are not implemented.

## Next single step

Calculate purity and efficiency for 90 reconstructed pairs, 72 correct pairs, and 120 truth-matchable cases; then explain the effect of loosening matching cuts.

