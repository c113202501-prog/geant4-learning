# Geant4 Concept Map

## Main experiment chain

```text
physics question
→ beam/source
→ interaction
→ particle transport
→ detector
→ signal/scoring
→ reconstruction
→ observable
→ physics interpretation
```

## Geometry

```text
Solid → shape
LogicalVolume → shape + material + shared properties
PhysicalVolume → placed instance in a mother coordinate system
```

## Transport to measurement

```text
Primary → Track → Step → Process
→ energy deposit / secondary particles
→ scorer or Sensitive Detector
→ raw hit
→ detector response / digit
→ reconstructed observable
```

## Current Exercise 4 distinctions

| Question | Correct layer |
|---|---|
| What happened in one transport increment? | `G4Step` |
| Which detector channel accumulated activity? | raw hit |
| Did electronics accept the signal? | readout/digitization |
| Which two detector hits belong together? | reconstruction |
| Were they truly produced by one track? | Monte Carlo truth validation |

## Code-reading frame

For each class or function ask: physics purpose, Geant4 abstraction, runtime behavior, minimal C++, design reason, and whether it is `[FRAMEWORK]`, `[USER]`, or `[EXAMPLE]`.

