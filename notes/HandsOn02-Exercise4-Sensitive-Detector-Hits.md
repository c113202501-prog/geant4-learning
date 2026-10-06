# HandsOn02 / Exercise 4：Sensitive Detector、Hit 與 Readout

## 整體定位

```text
G4Step
→ Sensitive Detector::ProcessHits()
→ raw HodoscopeHit
→ event-level collection
→ readout / digitization
→ ntuple / reconstructed observable
```

本篇區分物理輸運、raw hit、電子學決策與分析輸出。程式能建立 hit，不代表已模擬真實 detector signal。

## Repository evidence

目前實作來源已納入 repository：`HandsOn03/HandsOn3`，改編自 Geant4 basic/B5。

- `HodoscopeSD::Initialize()`：每個 event 建立新的 hits collection，加入 `G4HCofThisEvent`。
- `HodoscopeSD::ProcessHits()`：讀取 step 的 `edep`、copy number 與 global time。
- 同一 event、同一 strip 只建立一筆 `HodoscopeHit`；後續 steps 只更新最早時間。
- `HodoscopeHit` 現已保存 strip ID、最早有效時間與累積 `edep`。
- `EventAction` 從 `G4HCofThisEvent` 取回 collections；B5 的 `Time1`、`Time2` 是 scalar ntuple columns。

## 已確認理解

### `ProcessHits()` 回傳值與控制流程

- `G4bool` 是 framework method signature 的一部分。
- Geant4 kernel 不以這個布林值決定 hit 是否存在。
- 真正的控制點是程式是否執行建立、更新及 `insert()` hit 的程式碼。
- `edep == 0` 的 early return 會跳過 hit 建立；回傳 `true` 本身不等於建立 hit。

### 同一 strip 的 hit 合併

`copyNo` 識別 physical strip。若同一 strip 已有 hit，應更新原 hit，而非建立第二筆。

若要加入能量資訊，概念上的更新是：

```cpp
existingHit->AddEdep(edep);
existingHit->SetTime(min(existingTime, hitTime));
```

新 hit 也必須先加入第一個 step 的 `edep`。

### Threshold 的層級

逐 step threshold 會受 Geant4 step 切分影響。較接近具有整合時間窗的電子學模型是：

```text
同一通道、同一時間窗內累積訊號
→ 模擬 detector/readout response
→ 套 threshold
→ 形成可讀出的 hit／digit
```

raw `HodoscopeHit` 與通過 threshold 的 readout hit 不應混為同一層。

### 資訊壓縮與時間窗

只保存「總 `fEdep`＋最早時間」會遺失每個 step 的時間與能量分布，因此無法在事後重建多個時間群。完整時間窗模型需要保存逐 step `(time, edep)`、固定 time bins 或獨立 digitizer。

### Geometry information in a hit

- Logical volume：要畫的形狀與共同屬性。
- Copy number：辨認是哪個 physical placement。
- Touchable transform：該 placement 在世界座標的位置與旋轉。

保存 transform 的設計目的，是讓 hit 在 event display 中能標亮正確位置的 strip。

### Ntuple schema

若要保存多個 readout hits，可使用平行 vectors：

```text
stripIDs[i] ↔ hitTimes[i] ↔ hitEdeps[i]
```

不變條件：三個 vectors 等長，且同一 index 表示同一 hit。每個 event 對已綁定 ntuple 的 member vectors 呼叫 `clear()`；不可用短生命週期的區域 vector 取代。

scalar `Time1` 只能表達一個數值；若有多個 hits，必須明確選擇代表時間或改用 vector schema。

### TOF association：truth 與 reconstruction

同一 event 可能包含 primary 與多個 secondaries，兩側 detector 的幾何接受度也不同，因此兩側最早 hit 不保證來自同一粒子。

- `trackID` matching：Monte Carlo truth，只能作為事後驗證答案。
- detector-level matching：使用 strip 位置、時間、能量與 reconstructed track，才代表真實實驗可用的 reconstruction。
- 不得把 `trackID` 當成 reconstruction 輸入，再宣稱得到 detector 的實際配對能力。

後續評估指標：

```text
purity     = truth-confirmed reconstructed matches / all reconstructed matches
efficiency = truth-confirmed reconstructed matches / all truth matchable cases
```

## Mastery

- Sensitive detector、raw hit、readout/digit 分層：`UNDERSTOOD`
- 同 strip 累積 `edep` 與最早時間的程式邏輯：`UNDERSTOOD`（引導填空完成）
- ntuple scalar/vector 與跨欄位一對一關係：`UNDERSTOOD`
- `trackID` truth 不可作為 detector reconstruction 輸入：`UNDERSTOOD`
- raw-hit `fEdep` accumulation：`IMPLEMENTED / BUILT / NUMERICALLY VERIFIED`
- `G4HCofThisEvent → HodoscopeHitsCollection → Print()`：`IMPLEMENTED / NUMERICALLY VERIFIED`
- threshold/digitization 程式修改：`NOT IMPLEMENTED`
- TOF matching purity/efficiency：`UNDERSTOOD`（既有 LEARNING_STATE 記錄已支持計算與分母解釋）；未據此宣稱遷移掌握。

## 下一步

目前下一步以 LEARNING_STATE.md 為準。raw-hit 能量累積與 collection 列印已完成；threshold、有限時間窗與 vector 輸出尚未實作。

## 2026-10-06：readout 分層與資訊壓縮的理解證據

- 教學例：同 event 的 strip 7 為 0.24 MeV、strip 8 為 0.08 MeV，門檻假設 0.20 MeV。學習者回答 raw collection 保留兩筆、readout 一筆，並解釋 strip 8 只在 readout 被篩掉，raw hit 不刪除。
- 時間窗例：10 ns、100 ns 各沉積 0.12 MeV；event 累積為 0.24 MeV，但假設固定 20 ns 窗，各窗僅 0.12 MeV。學習者正確解釋總能量與最早時間無法還原能量的時間分布，缺少逐 step 的 (time, edep) 對應資訊。
- 以上支持 UNDERSTOOD，不支持 INDEPENDENT／TRANSFERRED，也不是新增程式驗證。
- 導師提出先做整個 event 的能量門檻，0.20 MeV 明確為 EXAMPLE。尚待學習者回答恰好 0.20 MeV 時採 > 還是 >=；尚未改碼。

## 一句話總結

Geant4 step 是輸運計算單位；Sensitive Detector 將 steps 彙整成 raw hits；電子學模型再以時間窗與 threshold 形成可讀出資料；truth ID 只負責驗證 reconstruction。
