# Learning Log

```yaml
schema_version: 1
audience: Codex and GPT tutors
canonical_current_state: LEARNING_STATE.md
implementation_evidence: LEARNING_PROGRESS.md
student_notes: Notion
latest_session_id: 2026-10-08-sampling-bootstrap
historical_notion_log: notes/archive/Notion-Learning-Log-2026-10-08.md
```

## Session: 2026-10-08-sampling-bootstrap

### Scope and user constraints

- Learner: physics junior; Geant4 toward ePIC ZDC; seeks the complete analysis framework and techniques for identifying error sources.
- Current scope is learning, not running a research campaign. Small examples, predictions, existing plots and short code are preferred; do not configure environments, produce more events or scan parameters merely to advance teaching.
- New subject: ask for the learner's own current understanding first. If clear, skip explanation and use an application/judgment exercise.
- One concept at a time: purpose → learner-calculated small example → formula/source → applicability and a failure counterexample → three-sentence checkpoint → exercise.
- Feedback: correct part first, actual gap and its consequence second, only one follow-up. Do not invent gaps. Default difficulty is appropriate (剛好).
- Two consecutive unaided correct responses require migration of context/conditions. Maximum one retrieval exercise per concept, then a judgment case with a trap.
- Prompted answers, provided numerical results, demonstrated examples and successful software runs are not independent mastery evidence.
- Source changes require the learner's “你來改”. Notebook/analysis artifacts already exist, but no new simulation is requested now.
- Authority clarified by user: GitHub Learning Log is for Codex/GPT and may use machine-friendly fields; Notion is for student-facing learning/review notes. Move the historical Notion Learning Log to GitHub, verify, then trash that Notion page.

### Concept chain covered

1. Data level: step → strip accumulation → threshold → event observable → histogram/ROOT; denominator, zero events and entry units.
2. Statistics: sample width versus bin width/mean uncertainty; selection/truncation; aggregation and weighting; source covariance.
3. Calorimetry: EM shower vocabulary/scales, active/absorber energy partition and sampling fluctuations; particle counts alone do not determine the signal.
4. Numerical/scoring checks: PreStepPoint volume classification; cut dependence; Labs is accumulated charged path, not penetration depth; containment needs a defined energy account.
5. Bootstrap: R=s_f/mean(f); SE(R), SE(ΔR), paired versus independent resampling, tail representation, original N versus bootstrap B.
6. Practical convergence: interval including zero is not sufficient; define an acceptable δ and check precision and relevant observables.
7. Error framework: statistical/systematic distinction; design difference is the research signal; common nuisance parameter can have unequal geometry sensitivities.
8. Calibration: signal/incident-energy correspondence; independent validation of bias, linearity, resolution and applicability.

### Learner evidence

Evaluator: Codex. Date: 2026-10-08. No new formal mastery level assigned; no delayed RETAINED evidence. Provided teaching numbers are not evidence of independent numerical derivation.

| ID | Subject | Original learner wording | Assistance / limit |
|---|---|---|---|
| E01 | Bin width versus sample width | 「這只是數值上的巧合，兩者沒有因果或比例關係。」 | Taught relationship; supplied numerical case |
| E02 | Sampling partition | 「貢獻訊號的電子數相同，不代表每個電子在閃爍體留下的沉積量相同」 | Mechanism already taught |
| E03 | Cross-volume scoring | 「錯誤只是把能量在鉛與閃爍體之間重新分配，總和仍不變。」 | Supplied step example; total account alone insufficient |
| E04 | Paired versus independent bootstrap | 「即使兩組事件數相同，也不代表具有配對關係。」 | Initially applied paired method to independent runs; corrected after explicit hint |
| E05 | Cut convergence | 「不顯著不等於已收斂。」；「若 ΔR 的信賴區間完整落在 [−δ,+δ] 內，才有較充分的收斂證據。」 | Existing-understanding assessment; data supplied; not a formal equivalence test |
| E06 | N versus B | 「在 0.1 mm 和 0.01 mm 兩組各增加獨立 events，保留每個 event 的 f 值，再重新執行 Bootstrap。」 | Tutor had explicitly corrected N/B confusion |
| E07 | Statistical/systematic | 「幾何 A/B 的預期設計差異是研究訊號，不是系統誤差。」；「這個差異能否在合理的系統設定變動下維持。」 | Own initial explanation, no answer hint |
| E08 | Shared nuisance sensitivity | 「共用系統參數不代表系統誤差會抵消，A、B 對 θ 的敏感度不同」；「增加 events 只能降低統計誤差，無法消除 θ 的不確定性。」；「θ 的合理範圍、實驗約束及可能的機率分布。」 | Judgment exercise without answer hints; supplied teaching table |
| E09 | Calibration purpose | 「校正就是建立『探測器讀出訊號』與『真實入射能量』之間的對應關係。」；「找出兩者的比例、偏移及是否具有線性關係。」 | Own initial explanation; reliability still requires validation |
| E10 | Validation | 「用未參與校正的獨立測試資料，檢查校正後的能量是否接近真實入射能量。」 | Initial understanding after reliability limitation named; listed bias/linearity/resolution/position/angle/species, no answer template |
| E11 | Electron versus hadron response | 「電子與強子 shower 的『可見能量比例』不一樣」；「強子 shower 分電磁跟強子成分」；「核反應要花能量打斷核束縛」 | Own initial explanation; tutor clarified neutron response depends on material/integration time; no claim every neutron is invisible |
| E12 | Mean calibration versus fluctuations | 「甲的讀數…9 GeV」；「乙…6 GeV」；「甲…12 GeV」「乙…8 GeV」；「平均能量校正可以消除平均偏差，但無法消除事件間組成波動造成的解析度損失。」 | Learner calculated without answer hint; supplied teaching model/numbers, not independently established physical coefficients |

### Small cases and interpretation boundaries

- Bootstrap paired example (teaching, not runtime): original rows (.10,.20),(.20,.40),(.30,.60); draw rows [3,1,1]. Learner calculated R_A=R_B≈.692820323 because B=2A. Differences near 1e−10 are rounding, not physical effects.
- Tail trap (teaching): f={.04,.05,.06,.40}; forcing .40 once conditions out its multiplicity fluctuations. This example underestimates SE; the direction is not a universal rule. A missed population tail cannot be recreated by ordinary empirical bootstrap.
- Common θ case (teaching): low (R_A,R_B)=(19%,20%), central (20%,18%), high (21%,18%). ΔR is −1,+2,+3 percentage points; shared parameter does not ensure cancellation or stable ranking.
- Hadronic response case (teaching): equal incident 10 GeV, EM response=1 and non-EM=0.5; mixes (8,2) and (2,8) give readings 9,6, mean7.5. Learner independently calculated common scaling4/3 yields12,8; mean correction does not remove fluctuations. Then tutor introduced Erec/E=f_em+(h/e)(1-f_em), distinguished f_em from earlier active-layer fraction f, and named leakage/saturation as limits. Three-sentence checkpoint pending in state. This is not an ePIC design coefficient or full response model.
- Increasing bootstrap B stabilizes the numerical estimate of SE/interval endpoints; it does not add original observations. Increasing independent N usually improves precision, but discovering rare tails can temporarily increase estimated SE.
- R based on active deposited fraction is not automatically pure sampling fluctuation or reconstructed energy resolution. Mean≈0, incorrect event units, correlations, incomplete energy accounts and nonrepresentative tails require care.

### Existing executable evidence (not learner implementation)

- Hodoscope source/readout/ROOT extension verified locally in earlier checkpoints. Its source modifications were not published by this session's documentation migration; remote source may be older.
- ROOT fixed-3/event 1040: H1 strip 7 energy=74.79219437246496 MeV, time=6.8393795730932405 ns, H2 empty. Proton fixed-momentum case; this is not calorimeter f and its selected vectors lack an all-material denominator. Cause of tail is not established.
- Hodoscope file: C:/Users/User/Documents/Codex-results/Geant4/2026-10-08/learning-case/momentum-control-02/fixed-3/hodoscope_run0.root.
- Existing B4a: Geant4 11.4.2, FTFP_BERT, 1 GeV electron, 10 layers of 10 mm Pb + 5 mm liquid Ar, transverse 10 cm, one thread; cuts .7,.1,.01 mm, 1000 events each, independent seeds. Unmodified official B4a source; active material is liquid argon, not scintillator; not geometry A/B.
- Per-event f=Egap/(Eabs+Egap), s_f uses ddof=1. R_f differs from earlier R_Egap. No complete escaping-energy account or isolated intrinsic sampling term.
- Current independent comparison: R(.1)=.20450240782490106, R(.01)=.19530412169437228, ΔR=.009198286130528782. B=500: SE=.005997803945200401; percentile95=[−.0021688502405860653,.020858212758559667]. Multiply differences by 100 for percentage points.
- Same roots/N, existing B=10000 reference: SE(ΔR)=.006248875283754619; interval=[−.0029708571753251168,.02142953010461869]. More B did not reduce the underlying sampling width.
- Root hashes: cut-.1 ca67088523a9404d1b55ee44bf81fea4b7eb926469d7fb423758f7a6d3bbef9e; cut-.01 650953fa6c0957d99649792c134fde0296b278876562d9d92a63ee686114c372.
- Case artifacts: C:/Users/User/Documents/Codex-results/Geant4/2026-10-08/learning-case/B4a-cut-convergence/. Current fraction-cut-comparison.json and B4a-cut-case.ipynb use B=500; B10000-reference files retain old results. Notebook outputs were generated by Python execution, not a verified Jupyter kernel session.
- During the note/migration request: no new simulation, build, bootstrap run, package installation or simulator source edit. Existing outputs are context only.

### Sources actually read

- SciPy official bootstrap documentation: resampling, paired, standard_error and interval methods. NumPy was used in the teaching analysis, not SciPy execution. https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.bootstrap.html
- Think Stats third edition chapter 8: selected sampling-uncertainty material; its main examples use parametric resampling, not the exact empirical bootstrap algorithm here. https://allendowney.github.io/ThinkStats/chap08.html
- Earlier session selected Geant4 cut documentation and local source plus Livan/Wigmans sampling sections; details in the current concept note. Do not invent book page numbers or claim full-book reading.
- PDG 2024 Particle Detectors at Accelerators, printed pp.88–90, relevant hadronic-response/neutron-time paragraphs actually read: https://pdg.lbl.gov/2024/reviews/rpp2024-rev-particle-detectors-accel.pdf . Current response example is simplified, not a verified ePIC ZDC model.

### Remaining framework (not a remedial prerequisite wall)

- Statistical/systematic error budget, correlations/bias and convergence versus model validation.
- Cleaning/quality, PMF/CDF, selection/tails, estimation/testing in a complete analysis.
- Calibration/validation, response/resolution, regression/fits/likelihood and residual diagnostics.
- Containment energy accounts, hadronic/invisible energy, noncompensation and ZDC relevance.
- Visible response/readout; optical/PDE/sensor effects when the actual design requires them. Actual MPPC source/model remains unlocated.
- Case-based Notebook work; time-series/survival topics only when a question warrants them.

### Continuation routing

Read LEARNING_STATE.md for the actual pending question and next step. Do not restart H1 sums, basic standard deviation, independent bootstrap operations or calibration definitions already answered. Do not start simulations as an automatic consequence of discussing an analysis plan.

