# Geant4 Physics Knowledge Map

## Goal

Learn Geant4 as a simulation of a real particle-physics experiment, not as isolated C++ classes.

Always connect code to:

`physics question → beam/source → interaction → particle transport → detector → signal/scoring → observable → physics interpretation`

## Reference roles

Use these books as complementary conceptual references:

- **Povh et al., Particles and Nuclei**  
  Focus: scattering, cross sections, matter structure, experimental inference.
- **Perkins, Introduction to High Energy Physics**  
  Focus: particles, interactions, conservation laws, scattering, experimental methods, physical interpretation.
- **Fernow, Introduction to Experimental Particle Physics**  
  Focus: beams, targets, particle–matter interactions, detectors, electronics, triggers, detector systems.

Do NOT invent exact book content, quotations, page numbers, or chapter claims unless the source is actually available. General physics knowledge may be used but must not be presented as extracted book content.

## Knowledge map

### 1. Physics objects

`leptons/quarks → hadrons/nuclei → EM/strong/weak interactions`

Learn only enough theory to understand what Geant4 particles/processes physically represent.

### 2. Experimental inference

`scattering → cross section → momentum transfer → resolution → elastic/inelastic/DIS → structure`

Mental model:

`cross section → interaction probability → mean free path → transport/process occurrence`

### 3. Beam/source

`source → acceleration/beam → target/collision → outgoing particles`

Geant4 mapping:

`real beam/source → PrimaryGeneratorAction → primary vertex/particle`

### 4. Particle transport

`particle + material → possible processes → state change/secondaries`

Key processes:  
`ionization | multiple scattering | bremsstrahlung | pair production | photon interactions | hadronic interactions | decay`

Always ask:

- What can happen?
- How likely?
- What changes afterward?

### 5. Detector physics

`particle–matter interaction → measurable response`

Functions:

`tracking → position/trajectory/momentum`  
`calorimetry → deposited energy/shower/energy`  
`PID → identify particle`  
`trigger → decide which events to retain`

Do not equate:  
`physical interaction ≠ detector signal ≠ reconstructed observable`

### 6. Geometry

Real detector → Geant4 model:

`Solid → shape`  
`LogicalVolume → shape + material/properties`  
`PhysicalVolume/Placement → instance placed in geometry`

Core question:  
Why does Geant4 separate shape/material/placement, and what would fail/become inefficient if it did not?

### 7. Transport → measurement

`Primary → Track → Step → Process → energy deposition/secondaries → scoring/sensitive detector → hit → observable`

Always distinguish:

- simulated physical process
- deposited energy
- detector response
- scoring/hit
- reconstructed quantity

### 8. Full experiment loop

`physics question → experimental design → beam → interaction → detector → signal → reconstruction → observable → statistics → physics interpretation`

## Code-learning rule

For every Geant4 class/function/code block, first locate it on this map.

Ask:

1. Where is this in the experiment/simulation flow?
2. What physical problem does it solve?
3. What happens at runtime?
4. Why is Geant4 designed this way?
5. What breaks/changes if removed or redesigned?
6. Which part is:
   - `[FRAMEWORK]` required by Geant4
   - `[USER]` detector/physics choice
   - `[EXAMPLE]` implementation choice of this example

Never teach a Geant4 API as an isolated programming fact when a physical interpretation exists.

## Learning priority

`correct mental model > design rationale > predict behavior > modify code > successful execution`

Before modifying code:

`predict → modify → run/verify → compare prediction vs result → correct mental model`

Do not generate a full project/class unless explicitly requested. Prefer the minimum code change needed for the current learning step.

When a C++ concept blocks understanding, teach only the minimum prerequisite C++ concept, then return to Geant4.

## Current main path

`DetectorConstruction → PrimaryGeneratorAction → Tracking → Step/Process → Scoring/Hit`

Keep new learning attached to this path unless another branch is explicitly requested.
