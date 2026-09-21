# Geant4 Learning

Hands-on learning workspace for Geant4 11.4.x on Windows 11 + WSL2 + Ubuntu 24.04.

## Current stage

`HandsOn01 / B1`

The learning status, verified environment, and next conceptual target are maintained in
[`LEARNING_PROGRESS.md`](LEARNING_PROGRESS.md).

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
