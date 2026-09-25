# Geant4 Learning

Hands-on learning workspace for Geant4 11.4.x on Windows 11 + WSL2 + Ubuntu 24.04.

## Current stage

`HandsOn02 / Exercise 4 — Sensitive Detector, Hit, Readout, and TOF matching`

Cold start from [`AGENTS.md`](AGENTS.md), then [`LEARNER_PROFILE.md`](LEARNER_PROFILE.md) and
[`LEARNING_STATE.md`](LEARNING_STATE.md). Chronology and evidence are in
[`LEARNING_PROGRESS.md`](LEARNING_PROGRESS.md); the teaching procedure is in
[`GEANT4_LEARNING_PROTOCOL.md`](GEANT4_LEARNING_PROTOCOL.md); verified commands are in
[`ENVIRONMENT.md`](ENVIRONMENT.md).

## Build B1 in WSL

```bash
source /home/sundae/geant4/install/bin/geant4.sh
cmake -S HandsOn01/B1 -B build/HandsOn01-B1 \
  -DCMAKE_BUILD_TYPE=Release \
  -DCMAKE_PREFIX_PATH=/home/sundae/geant4/install
cmake --build build/HandsOn01-B1 -j4
```

Run interactively with visualization:

```bash
cd build/HandsOn01-B1
./exampleB1
```

Build products, Geant4 installations, and generated visualization files are intentionally excluded
from version control.
