# Environment

LAST VERIFIED: 2026-09-25

## Host and runtime

- `[VERIFIED]` Windows 11 host with WSL2 Ubuntu 24.04 LTS.
- `[VERIFIED]` WSL architecture: `x86_64`.
- `[VERIFIED]` Geant4 setup script: `/home/sundae/geant4/install/bin/geant4.sh`.
- `[VERIFIED]` Geant4 version used by builds: 11.4.2.
- `[VERIFIED]` Git working tree: `C:\Users\User\Documents\Codex\2026-09-16\can`.
- `[VERIFIED]` Git remote: `https://github.com/c113202501-prog/geant4-learning`.

## Builds

### HandsOn01 / B1

- `[VERIFIED]` Build directory: `/home/sundae/jlab-build/HandsOn01-B1`.
- `[VERIFIED]` Executable: `/home/sundae/jlab-build/HandsOn01-B1/exampleB1`.
- `[VERIFIED]` Executable is Linux ELF 64-bit x86-64.
- `[VERIFIED]` CMake source recorded in cache: `/mnt/c/Users/User/Downloads/JLab_Geant4School2025/JLab_Geant4School2025/HandsOn01/B1`.

```bash
source /home/sundae/geant4/install/bin/geant4.sh
cd /home/sundae/jlab-build/HandsOn01-B1
./exampleB1
```

### HandsOn02

- `[VERIFIED]` Repository source: `/mnt/c/Users/User/Documents/Codex/2026-09-16/can/HandsOn02/HandsOn2`.
- `[VERIFIED]` Build directory: `/home/sundae/jlab-build/HandsOn02-baseline`.
- `[VERIFIED]` Executable: `/home/sundae/jlab-build/HandsOn02-baseline/G4tut`.
- `[VERIFIED]` 2026-09-24 build and batch scoring run succeeded.

```bash
source /home/sundae/geant4/install/bin/geant4.sh
cmake --build /home/sundae/jlab-build/HandsOn02-baseline -j2
cd /home/sundae/jlab-build/HandsOn02-baseline
./G4tut /mnt/c/Users/User/Documents/Codex/2026-09-16/can/HandsOn02/HandsOn2/scoring-batch.mac
```

## Course and references

- `[VERIFIED]` Course root: `C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025`.
- `[VERIFIED]` Geant4 Book for Application Developers: `C:\Users\User\Downloads\BookForApplicationDevelopers.pdf`.
- `[VERIFIED]` Leo: `C:\Users\User\Downloads\Techniques-for-nuclear-and-parti.epub`.
- `[VERIFIED]` Knoll: `C:\Users\User\Downloads\Radiation detection and measurement (Knoll, Glenn F) (z-library.sk, 1lib.sk, z-lib.sk).pdf`.
- `[VERIFIED]` 許淑艷: `C:\Users\User\Downloads\蒙特卡罗方法在实验核物理中的应用 (许淑艳编著, 许淑艳编著, 许淑艳) (z-library.sk, 1lib.sk, z-lib.sk).pdf`.

Do not execute downloaded macOS ARM64 binaries in WSL.

