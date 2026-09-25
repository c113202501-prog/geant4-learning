# Project Map

## Repository

```text
geant4-learning/
├─ LEARNING_STATE.md          # read first
├─ LEARNING_PROGRESS.md       # chronology and evidence
├─ GEANT4_LEARNING_PROTOCOL.md
├─ GEANT4_PHYSICS_KNOWLEDGE_MAP.md
├─ ENVIRONMENT.md
├─ HandsOn01/B1/              # completed foundation
├─ HandsOn02/HandsOn2/        # current repository exercise source
├─ notes/                     # durable concept notes
└─ NOTION_EXPORT/             # student-facing Markdown projection
```

## JLab course

- Local course root: `C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025`.
- Repository copies only the exercises currently used; do not import or modify unrelated exercises.

## HandsOn01 / B1 map

| Flow | Relevant file/class | Role |
|---|---|---|
| Application setup | `exampleB1.cc` | Registers detector, `QBBC`, and actions. |
| Detector | `DetectorConstruction.cc` | Builds geometry/materials; assigns `logicShape2` as scoring volume. |
| Source | `PrimaryGeneratorAction.cc` | Creates one 6 MeV gamma and calls `GeneratePrimaryVertex(event)`. |
| Event actions | `EventAction.cc` | Resets and forwards per-event deposited energy. |
| Step/scoring | `SteppingAction.cc` | Filters to scoring logical volume and reads `GetTotalEnergyDeposit()`. |
| Run observable | `RunAction.cc` | Merges accumulables and reports energy/dose statistics. |

## Current HandsOn02 path

- Exercises 1–3: materials, absorber/shower, command-based scoring, mesh coordinate transforms, and dump statistics.
- Exercise 4: Sensitive Detector, raw hit, readout/digitization, ntuple schema, and TOF hit association.
- Current durable note: `notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md`.
- Exercise 4 code modifications are not implemented.

