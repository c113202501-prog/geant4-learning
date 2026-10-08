# Learning State

Current snapshot: 2026-10-08 (Asia/Taipei). Canonical state in GitHub; Notion is a student-facing projection. This replaces the stale H1-sum/Notion-cache next step.

```yaml
schema_version: 2
last_updated: 2026-10-08
current_stage: event observables, analysis judgment, calorimeter response
long_term_goal: ePIC ZDC simulation and complete data-analysis/error-source skills
current_scope: learning the framework; no new simulation or environment preparation requested
current_concept: electromagnetic fraction response model; mean calibration versus event fluctuations
last_completed_unit: calibration purpose and independent validation; shared nuisance parameter sensitivities
pending_question: >-
  Three-sentence checkpoint: what f_em is; how it affects the reading
  when electromagnetic/non-electromagnetic responses differ;
  one situation the simplified model cannot explain directly.
next_step: Review checkpoint gaps/consequences only; if passed move to a changed-context application, not another mean-rescaling drill
active_misconception: []
understanding_gap_to_check: distinction between mean calibration and event-dependent electromagnetic fraction response
current_unit_mastery: no new formal level; do not infer independence or retention from prompted answers
current_unit_evidence: LEARNING_LOG.md E07-E12 and current note
current_note: notes/2026-10-08-Sampling-Bootstrap-Review.md
student_note: https://app.notion.com/p/Bootstrap-cut-2026-10-08-3f39f5095b9c8015a03ac39680eac6ea
source_change_authorization: learner must say 你來改
simulation_action: none requested; treat proposed checks as learning plans
sync_queue: [project latest response concept to Notion student notes]
```

## Continuation rules

- Do not restart H1 sums, basic standard deviation, bootstrap row operations, statistical/systematic definitions or calibration definitions already answered.
- New subject: ask the learner's understanding first; skip explanation if clear. One concept at a time; user-calculated small example before formula; applicability with a failure case; three-sentence checkpoint before exercise when teaching is needed.
- Default difficulty 剛好. After two unaided correct rounds, change context/conditions. At most one retrieval question per concept, then a judgment case with a trap. Hints and supplied numbers/results are not independent evidence.
- User seeks complete framework and error-source judgment, not a current research campaign. Use small cases, predictions, existing plots or short analysis code. Do not configure environments or run more events automatically.
- User can learn while authorized documentation work proceeds. GitHub LEARNING_LOG.md is for Codex/GPT; Notion contains student-readable notes. Historical Notion log is archived under notes/archive/.

## Most recent evidence

- Statistical/systematic distinction and shared-parameter case answered correctly; common parameter does not guarantee cancellation, and more events cannot resolve its uncertainty.
- Calibration defined as signal-to-energy relation; independent validation includes bias, linearity, resolution and position/angle/species applicability.
- Electron-to-hadron assessment: learner correctly named different visible response, EM/non-EM components and nuclear binding losses. Tutor clarified that neutron energy may be detected with material/time dependence, rather than being categorically invisible. PDG 2024 pp.88–90 actually read. Learner independently calculated teaching readings 9,6 GeV and mean correction 12,8 GeV; correctly explained calibration of average cannot remove composition fluctuations. Tutor then introduced the simplified response formula and its leakage/saturation limits. Current checkpoint pending.
- Bootstrap/cut: finite original N versus resampling B distinguished after correction. CI containing zero does not establish convergence; practical tolerance needed. No formal equivalence test established. Tail support and pairing limitations recorded in the log.
- Historical UNDERSTOOD labels in earlier progress retained; no new INDEPENDENT/TRANSFERRED/RETAINED claim.

## Executable evidence boundary

Local source/readout and existing ROOT evidence are indexed in LEARNING_LOG.md. Documentation publication does not publish local simulator changes or generated ROOTs. The remote source may predate the locally verified extension.

- Existing hodoscope fixed-3/event1040: selected H1 strip7=74.79219437246496 MeV; this is not calorimeter f, and the cause is unestablished.
- Existing B4a: 1 GeV electron, Pb/liquid-Ar, independent cut runs, N=1000 each. f=Egap/(Eabs+Egap), sample std(ddof=1). R_f is not pure isolated sampling or reconstructed energy resolution.
- Existing B=500 comparison: ΔR≈0.920 pp, SE≈0.600 pp, percentile95≈[−0.217,+2.086] pp. No new runs during documentation migration.
- Finite readout window/electronics/actual MPPC source remain unverified or unimplemented; no current-design specification inferred.

## Remaining framework

Response and resolution → hadronic/invisible energy/noncompensation → containment and energy accounts → error budgets/correlations/model validation → fits, likelihood and residuals → visible response/optics/readout as required by actual ZDC design. Cleaning/PMF/CDF/testing are integrated in cases; regression, time-series and survival methods are chosen when a real learning question warrants them. This is not a prerequisite checklist blocking the next concept.
