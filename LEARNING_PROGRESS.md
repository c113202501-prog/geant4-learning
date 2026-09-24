# Geant4 Learning Progress

最後更新：2026-09-24（Asia/Taipei）

## 目前階段

HandsOn02 / Exercise 4：Sensitive Detector、Hit 與 Readout

目前狀態：Exercise 3 的 command-based scoring、mesh 座標與統計解讀已完成；正在學習 `G4Step → Sensitive Detector → raw hit → readout/digit → observable`。目前程式閱讀與概念建模已完成，尚未把 threshold/digitization 修改實作進 repository。

## 環境

- Windows 11 + WSL2
- WSL distribution：Ubuntu 24.04 LTS
- WSL architecture：x86_64
- Geant4：11.4.2
- Geant4 environment：`/home/sundae/geant4/install/bin/geant4.sh`
- Linux build directory：`/home/sundae/jlab-build/HandsOn01-B1`
- Linux executable：`/home/sundae/jlab-build/HandsOn01-B1/exampleB1`
- Qt / WSLg visualization：成功（學習者回報）
- HandsOn02 current source build：`[100%] Built target G4tut`（2026-09-24，`[CODEX-VERIFIED]`）。
- `scoring-batch.mac`：完成 1-event configuration run 與後續 199-event statistics run，process exit code 0；產生各 1803 行的 `eDep.txt` 與 `nOfStepGamma.txt`（2026-09-24，`[CODEX-VERIFIED]`）。

## 已完成

### 概念

- 理解 `solid → logical volume → physical volume` 的基本層級。
- 知道 material 屬於 logical volume。
- 知道同一個 `G4LogicalVolume` 可以有多個 physical placements。
- 知道 `fScoringVolume` 指向 scoring logical volume。
- 已通過 B1 geometry pre-exercise gate，不再重複考 geometry 基礎。
- `PrimaryGeneratorAction` 初始狀態：`UNDERSTOOD`。
  - 每個 event 產生 1 個 primary gamma。
  - 能量固定為 6 MeV。
  - 初始動量方向固定為 `(0, 0, 1)`，沿 `+z`。
  - `z0` 固定在 Envelope 的負 z 端（`-15 cm`）。
  - `x0`、`y0` 在每個 event 重新隨機取樣（各約為 `-8 cm` 至 `+8 cm`）。
  - 完成證據：學習者未照抄提示，能自行區分固定條件與 event-by-event 隨機條件。
- Tracking table 基本閱讀：`UNDERSTOOD`。
  - `Step# 0` 表示 track 建立時的初始狀態，尚未完成第一個輸運 step。
  - `Step# 1` 及後續各列表示相應 step 完成後的狀態。
  - 完成證據：學習者依實際 verbose table 正確辨認第 0、1、2 列的意義。
- B1 scoring-volume filter：`UNDERSTOOD`。
  - `SteppingAction` 不會累積所有 volumes 的能量沉積。
  - 只有 current logical volume 等於 `fScoringVolume` 時才繼續。
  - B1 的 `fScoringVolume` 指向 `logicShape2`。
  - 傳給 `EventAction` 的是該 step 的 `edepStep` 數值，而不是整個 `G4Step`。
  - 完成證據：學習者正確辨認 volume equality check 與 early return。
- Event-level energy accumulation：`UNDERSTOOD`。
  - `fEdep` 只代表目前一個 event 內所有合格 steps 的能量沉積總和。
  - `BeginOfEventAction()` 必須將 `fEdep` 歸零，避免上一個 event 污染下一個 event。
  - `EndOfEventAction()` 將完成的 event total 傳給 `RunAction`。
  - 完成證據：學習者能解釋 event boundary，並正確計算 `1 + 2 + 0.5 = 3.5 MeV`。
- Run-level accumulation and dose：`UNDERSTOOD`。
  - `RunAction::fEdep` 累積各 event 的 total energy deposit，而非直接累積 `G4Step`。
  - 三個 event totals `3.5 + 0 + 1.5 MeV` 會得到 run total `5.0 MeV`。
  - B1 使用 `dose = edep / scoring-volume mass`。
  - 在 total energy deposit 不變時，scoring-volume mass 加倍會使 dose 減半。
  - 完成證據：學習者正確計算 run total，並由公式推導質量變化對 dose 的影響。

### B1 mastery snapshot

- `PrimaryGeneratorAction → tracking → step filter → EventAction → RunAction → dose`：`UNDERSTOOD`
- B1 integrated explanation gate：`PASSED`。
  - 學習者能從每 event 的 6 MeV gamma 開始，說明 event reset、tracking、材料作用、能量沉積、run accumulation、worker merge、RMS、mass 與 dose。
  - 版本查證：B1 直接註冊 reference physics list `QBBC`；Geant4 11.4.2 的 `QBBC.cc` 內部註冊 `G4EmStandardPhysics`，兩者屬不同抽象層級。
  - 精確補充：primary 的 `x0/y0` 依分布隨機，`z0` 與初始方向固定；只有 Shape2 中的 step energy deposit 被計入。
- 尚未評為 `INDEPENDENT`：還未在沒有逐步提示下自行修改或重建流程。
- 尚未評為 `TRANSFERRED`：還未更換 scoring volume 或情境進行遷移測試。

### HandsOn02 / Exercise 1a

- `G4Element(name, symbol, Z, A)` 參數意義：`UNDERSTOOD`。
- `G4Material(name, density, ncomponents)` 的 `ncomponents`：`UNDERSTOOD`。
- `AddElement(element, natoms)` 的整數參數代表相對原子數：`UNDERSTOOD`。
- 化學計量轉換：`UNDERSTOOD`；例如 I×3、Cs×2 對應 `Cs2I3`。
- 夏校式引導填空：`PASSED`。
  - 學習者正確填入 I、Cs 的名稱、符號、原子序、莫耳質量、CsI 密度、兩種 components，以及 I:Cs = 1:1 的相對原子數。
  - 唯一錯誤是 `new G4Material(..., 2));` 多一個右括號，分類為 `C++ / simple syntax typo`，不是 Geant4 概念錯誤。
  - 修正後 repository source 已在 WSL + Geant4 11.4.2 重新編譯，結果為 `[100%] Built target G4tut`。`[CODEX-VERIFIED]`
- Mastery 維持 `UNDERSTOOD`：本次有填空框架與數值提示，尚不標記為 `INDEPENDENT`。
- 課程 supplied problem 檔已含答案；不以該檔既有內容當成獨立實作證據。

### HandsOn02 / Exercise 1b

- 夏校式引導填空：`PASSED`。
- 正確寫出 `nistManager->FindOrBuildMaterial("G4_Pb");`。
- 正確辨認 `G4_Pb` 是 Geant4 NIST material name，不是 C++ 變數或物理過程。
- 能區分手動建立複合材料 CsI 與向 NIST manager 查找／建立鉛材料。
- Mastery：`UNDERSTOOD`；因有提示，尚不標記為 `INDEPENDENT`。

### HandsOn02 / Exercise 2a

- 夏校式引導填空：`PASSED`。
- 正確以 `G4Material::GetMaterial("CsI")` 取得已建立的 CsI，而非重新建立材料。
- 正確將完整尺寸 `300 × 60 × 100 cm` 換算為 `G4Box` 半長 `150 × 30 × 50 cm`。
- 正確建立 `G4LogicalVolume(solid, material, name)`。
  - 過程中曾填入未宣告的 `CSI`，經提示後能區分材料名稱字串 `"CsI"` 與材料指標變數 `material`。
  - 錯誤分類：`C++ identifier / Geant4 object-reference confusion`，不是材料物理概念錯誤。
- 正確使用 `G4PVPlacement`，將 `hadCalorimeterLogical` 放入母體 `secondArmLogical` 的 `(0,0,3 m)`。
- WSL + Geant4 11.4.2 build 驗證：`[100%] Built target G4tut`。`[CODEX-VERIFIED]`
- Mastery：`UNDERSTOOD`；本次使用逐格提示，尚不標記為 `INDEPENDENT`。

### HandsOn02 / Exercise 2b

- 將材料指標統一命名為 `mat_csi`、`mat_pb`、`mat_scintillator`。
- 新增單一材料選擇點 `absorberMaterial`；目前指定為 `mat_pb`，geometry construction 僅使用此指標。
- 學習者最初寫成 `G4Material:GetMaterial("Pb")`：
  - `G4Material:` 應為 C++ scope-resolution operator `G4Material::`。
  - 鉛的 NIST material name 應為 `"G4_Pb"`，不是 `"Pb"`。
- 修正後 build 成功，batch run 正常處理 5 events；material-cuts couple 顯示 `G4_Pb` 已用於 geometry。`[CODEX-VERIFIED]`
- 控制變因檢查：`PASSED`。學習者正確指出比較材料時應保持粒子種類、能量、方向與 geometry 相同。
- 電磁 shower 預測：`PASSED`。根據 Pb 的 radiation length (`5.613 mm`) 小於 CsI (`1.860 cm`)，預測 Pb 中 shower 會在較短實際距離內發展。
- event display 辨識經修正：綠色五層是 drift chambers、紅色細條是 hodoscope、白色盒是 absorber；帶 `1 m` 標記的彩色線是座標軸，不是 particle trajectory。
- CsI 單一 event 定性觀察：shower vertex 位於 absorber 內，可見顯著 secondary multiplicity、扇形 lateral spread 與離開 absorber 的 trajectories。`[LEARNER-REPORTED]`
- Pb 單一 event 定性觀察：interaction 接近 absorber 入口，在 absorber 內僅發展一小段，並有大角度 secondary 向上游離開。`[LEARNER-REPORTED]`
- 新術語：沿原入射方向穿出 absorber 為 `forward leakage`；回到入射側／上游為 `backscatter`。Pb 截圖可見 backscatter，未見明顯 forward leakage。
- 限制：單一 Monte Carlo event 只能作定性示例，不能由一張圖建立材料差異的統計結論。
- Exercise 2b 操作與觀察：`PASSED`；物理機制 mastery：`UNDERSTOOD`。
  - 學習者主動回報先前答案主要由查單字拼湊，不能作為理解 shower mechanism、radiation length、leakage 或 backscatter 的充分證據。
  - 補強後能說明 `e± bremsstrahlung → gamma pair production → shower multiplication → energy loss/termination` 因果鏈。
  - 能區分制動輻射與電離：前者由高能帶電粒子受原子核庫侖場作用、偏轉並輻射光子；後者是將能量傳給束縛電子，使電子逸出並留下正離子。
  - 能說明 shower 不會無限增殖：能量分散後，低能粒子仍可運動，但電離等能量損失逐漸占主導。
  - 能以 `18.6 mm / 5.613 mm ≈ 3.3` 正確比較 CsI 與 Pb 的 radiation-length 尺度，並指出它是統計尺度而非固定作用位置。
  - 整合回答曾把電離與制動輻射串成同一過程；經針對性修正後，能獨立重述正確的制動輻射起始機制。
  - 尚未標記為 `INDEPENDENT` 或 `TRANSFERRED`：目前是在引導教學後完成因果解釋，尚未遷移到新材料／新能量情境。

### HandsOn02 / Exercise 3a

- Mastery：`UNDERSTOOD`；supplied source 已含答案，因此不標記為 `INDEPENDENT`。
- 能區分 particle transport 與 scoring：移除 scoring manager 不會阻止 geometry/physics/primary 所驅動的 transport，但 command-based scoring mesh 將無法正常使用。
- 能區分 scoring configuration 與 result data：manager 管理 mesh/scorer 設定，各 bin 數值是模擬後的累積結果。
- 能說明 `G4ScoringManager` 採共用 manager object 的必要性，避免 scoring configuration 分裂。
- C++ pointer：能說明 `scManager` 保存共用 object 的位址，`->` 要求其指向的 object 執行 method。
- `SetVerboseLevel(1)`：只改變 scoring 訊息詳細程度，不改變物理 transport 或 scoring 數值。
- Compile/runtime 分工：
  - `#include "G4ScoringManager.hh"` 在 preprocessing／編譯階段提供 class/interface declarations，不會建立 runtime object。
  - `GetScoringManager()` 在程式執行階段取得 singleton；若尚不存在則建立，若已存在則回傳同一共用 object 的位址。
- 錯誤修正證據：曾把 scoring manager 誤認為 transport 的必要條件，並曾稱 `#include` 為「呼叫函式庫」；經教學後能獨立修正兩者。
- Scoring mesh 教學分段：
  - `3b-1 mesh role`：`UNDERSTOOD`；能區分 absorber geometry 與虛擬測量網格。
  - `3b-2 mesh size`：`UNDERSTOOD`；`boxSize 150 30 50 cm` 為半長，完整尺寸 `300 × 60 × 100 cm`。
  - `3b-3 mesh position`：`UNDERSTOOD`；預設 `fArmAngle=0°` 時，second arm world `z=5 m` 加 absorber local `z=3 m`，得到 world `z=8 m`，與 scoring mesh 對準。

### 環境與執行

- B1 已在 WSL 中以 GNU C++ 13.3、CMake 3.28.3 重新編譯。
- 產物已確認為 Linux ELF 64-bit x86-64 執行檔。
- CMake 已確認找到 Geant4 11.4.2。
- Codex 已以 `run1.mac` 完成 batch smoke test，process exit code 為 0。
- `/run/beamOn 1` 成功，完成 1 event（學習者回報）。

## Needs Reinforcement

- Exercise 4 的 threshold、能量累積與 vector ntuple 目前是設計練習，尚未修改、build、run，因此不得標記為實作完成。
- TOF hit association：已理解最早 hit 不保證來自同一 track；下一步要練習使用 detector-level observable 配對，再以 `trackID` truth 評估 purity／efficiency。

- Primary particle settings 與 Physics List 的責任不同：
  - `PrimaryGeneratorAction` 建立 event 的初始粒子、能量、方向與位置。
  - Physics List 提供輸運時可用的物理過程與模型。

## Not Required Yet

- detailed scoring mechanism
- step-selection implementation details
- copy-number usage
- physics-process competition
- `G4Accumulable` 的多執行緒細節

## 目前學習原則

- 以進入實作為主，不先完整學完 Geant4。
- 理論只補到足以知道目前正在做什麼。
- 採用 `retrieve → verify → teach → test`。
- 每個新主題必須先展示真實程式及其上下文，再由 ChatGPT 講解，確認學習者已看過後才能測試或要求填空；不得以未教內容突襲測驗。
- 新領域採用認知學徒制順序：`Modeling（完整示範與設計理由）→ 低階理解確認 → Coaching／Scaffolding → Articulation → Reflection → Prediction／Exploration`；只有在先備 schema 已建立後才要求無提示預測。
- 每次作答後必須完成 consolidation：明確對照學習者答案、正確邏輯、差異與原因，不能只回覆對錯。
- 依 `GEANT4_PHYSICS_KNOWLEDGE_MAP.md`，所有程式教學先定位於完整實驗鏈，並區分 physical process、energy deposit、detector response、scoring/hit 與 reconstructed observable。
- 區分 physical phenomenon、physical model、Monte Carlo representation、Geant4 implementation、observable。
- ChatGPT 負責概念鏈、理解檢查、先備需求與 mastery 判斷。
- Codex 負責查看程式、修改、build、run、驗證，並更新本檔。
- 程式成功執行不自動等於概念已理解。
- 未經學習者自行解釋或轉移應用，不標記為 `UNDERSTOOD`、`INDEPENDENT` 或 `TRANSFERRED`。

## 下一步

下一步閱讀 `scoring.mac`，從 scoring mesh 的物理角色開始：

```text
locate the mesh in transport → measurement flow
        ↓
distinguish scoring mesh from detector geometry
        ↓
understand mesh size, position and bins one concept at a time
        ↓
connect energy-deposit quantities to physical observables
```

本階段的完成證據：

1. 學習者能用自己的話說明 primary settings 與 Physics List 的差異。
2. 學習者能沿 B1 程式指出一個 event 的資料流。
3. 學習者能區分視覺化軌跡、energy deposit、dose 與實驗偵測器訊號。
4. 完成下一個實作檢查點，並記錄修改、預測、觀察與解釋。

## 教材與程式位置

### Git repository

- GitHub：`https://github.com/c113202501-prog/geant4-learning`
- Repository source：`HandsOn01/B1`
- HandsOn02 source：`HandsOn02/HandsOn2`
- WSL build output remains outside Git：`/home/sundae/jlab-build/HandsOn01-B1`

### Notion learning workspace

- Workspace：`https://app.notion.com/p/ad09f5095b9c820f98a9015ad28dd43b`
- Notion 保存知識地圖、各題筆記、錯題與學習進度；Git 保存程式碼與可驗證證據。
- 已建立 HandsOn01/B1、HandsOn02 Exercises 1–3、完整知識地圖及錯題整理；Exercise 3 標為進行中。

### JLab 課程

- 課程根目錄：`C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025`
- B1 source：`C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025\HandsOn01\B1`
- HandsOn02：`C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025\HandsOn02\HandsOn2-problem`
- HandsOn03：`C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025\HandsOn03\HandsOn3-problem`
- 課程講義：`C:\Users\User\Downloads\JLab_Geant4School2025\JLab_Geant4School2025\Materials`

### 指定參考資料

- Geant4 11.4 Book for Application Developers：`C:\Users\User\Downloads\BookForApplicationDevelopers.pdf`
- Leo, *Techniques for Nuclear and Particle Physics Experiments*：`C:\Users\User\Downloads\Techniques-for-nuclear-and-parti.epub`
- Knoll, *Radiation Detection and Measurement*：`C:\Users\User\Downloads\Radiation detection and measurement (Knoll, Glenn F) (z-library.sk, 1lib.sk, z-lib.sk).pdf`
- 許淑艷，《蒙特卡罗方法在实验核物理中的应用》：`C:\Users\User\Downloads\蒙特卡罗方法在实验核物理中的应用 (许淑艳编著, 许淑艳编著, 许淑艳) (z-library.sk, 1lib.sk, z-lib.sk).pdf`

### 教學準則

- Geant4 Physics Knowledge Map：repository root 的 `GEANT4_PHYSICS_KNOWLEDGE_MAP.md`
- Geant4 Learning & Verification Protocol：`C:\Users\User\.codex\attachments\09319b4d-2080-4a89-b7d4-9c0fb98bb0cd\pasted-text.txt`
- Geant4 Learning Sources and Reference Policy：`C:\Users\User\.codex\attachments\a78f0b60-7758-4707-a9d0-4d71fa0020c0\pasted-text.txt`
- Teaching Grounding & Verification Protocol：`C:\Users\User\.codex\attachments\bfa3ac62-5271-49c8-b828-a3b4ed448c2d\pasted-text.txt`

## 證據標籤

- `[LEARNER-REPORTED]`：由學習者回報，尚未由 Codex 重做驗證。
- `[CODEX-VERIFIED]`：Codex 已直接檢查程式、build 或執行結果。
- `[SOURCE-VERIFIED]`：已由指定的課程、Geant4 官方文件或參考書支持。
- `[UNVERIFIED]`：目前資料不足，不推測。

## 更新規則

每完成一個實作檢查點，至少記錄：

1. 題目與預期結果。
2. 修改的檔案與核心變更。
3. build/run 驗證命令。
4. 實際觀察結果。
5. 錯誤分類與修正（若有）。
6. mastery 狀態：`SEEN / UNDERSTOOD / INDEPENDENT / TRANSFERRED / RETAINED`。

任何助手開始新工作前，先讀本檔；完成可驗證進展後，再更新本檔。
