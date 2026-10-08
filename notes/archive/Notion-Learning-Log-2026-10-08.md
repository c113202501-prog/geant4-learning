# Historical Notion Learning Log — migration snapshot

- Captured from visible Notion page text on 2026-10-08.
- Source: https://app.notion.com/p/Learning-Log-3e69f5095b9c818b958be27f02d14650
- Purpose: preserve historical evidence before the user's requested recoverable deletion.
- Old next-step and authority statements below are historical, not current instructions. Read ../../LEARNING_STATE.md for current state.
- Duplicate entries are deliberately preserved. Historical mastery labels have not been reassessed.
- Page metadata: tag 實作紀錄; project Geant4 學習：JLab Geant4 School 2025; understanding SEEN; review count 0; linked repository c113202501-prog/geant4-learning.

## Original body

HandsOn01 / B1 — foundation

Implementation: Linux x86-64 build and event display succeeded.

Verification: B1 executable and event processing verified.

Understanding: geometry hierarchy, primary generation, step filtering, event/run accumulation, and dose reached UNDERSTOOD; not independent.

HandsOn02 / Exercises 1–2

Implementation: CsI/Pb materials and absorber geometry built and run.

Verification: build/run and material use verified; event displays are qualitative evidence only.

Understanding: material composition, half-length geometry, electromagnetic shower, radiation length, ionization, bremsstrahlung, and pair production reached guided UNDERSTOOD.

HandsOn02 / Exercise 3

Implementation: scoring manager, rotated/transformed mesh, beam angle command, interactive and batch macros present.

Verification: 2026-09-24 build and batch run succeeded; score dumps produced outside Git.

Understanding: mesh role, coordinate transforms, voxel/bin mapping, step-based scorers, and dump statistics reached UNDERSTOOD with calculation support.

HandsOn02 / Exercise 4 — 先前概念設計階段（後續進展見 2026-10-07）

Implementation: threshold/digitization changes not implemented.

Verification: source behavior inspected in Geant4 basic/B5; no new Exercise 4 runtime evidence.

當時理解：SD/raw/readout、通道累積、ntuple schema、truth/reconstruction 已 UNDERSTOOD；當時 purity/efficiency 待應用。後續已有分母計算與 cut trade-off 解釋證據，非目前待答題。

Canonical chronology and evidence: Git LEARNING_PROGRESS.md and notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md.

2026-10-07 晚間—MPPC 計數定義（引導式 EXAMPLE）
概念：把到達光子數、被模型偵測的光子／photoelectron 數及重複進入次數分開；光收集比例須指定哪些光子與分母。未查到實際 MPPC 專案，不聲稱40、12、80/100、150來自 runtime。
學習者原文 [LEARNER-VERIFIED]：「把收到的光轉成電訊號」；「欄位名稱不會改變程式實際累加的是什麼。」；「若程式每次進入都加一，沒有記錄哪些光子已算過，最後 counter 會是 3。」；「更改後光收集效率依然是 80%。」
提示程度：先教概念及數字例子，再作答；僅記回答證據，本次未評新 mastery，未取得無提示跨情境或延後保留證據。
2026-10-08—筆記收尾與學習方式調整
Notion 目的：學習記錄兼複習。入口、Current State、總地圖、主動複習中心、關鍵字與避坑頁整合受影響內容，保存歷史答題與實際模擬圖；不擴大「需要補強」清單。
教材處理：24份檔案完成盤點與抽取（含一份重複 Geant4 手冊）；完成部分相關章節／研究摘要的選讀，並非所有書逐頁精讀。Perkins PDF 為掃描版，全文 OCR 未完成；頁碼未核對處不冒充已核對。學習方式見主動複習中心。
Source/build/run：本次未改模擬原碼、未新增 build/run，沒有新的物理結果與 mastery 評分；未 commit/push。
下一步：導師先用已有 H1 readout vector 示範每 event selected 能量、空 vector 為0與局部沉積的限制，再問一題。筆記單元結束集中保存，不以整理阻擋開課。

Date: 2026-10-07
HandsOn / Exercise: 學習里程碑 HandsOn02 / Exercise 4；source HandsOn03 Exercises 2、3 + readout/ntuple 延伸。
What changed: 加入 raw edep 累積、六個 per-event vectors、逐 strip >=0.20 MeV 教學 cut、ROOT vector binding、eventID/row、run 開寫關檔；本日整合 Notion 與 handoff 第10–15節規則。
What was learned [LEARNER-VERIFIED]: 同 EventAction 的原 vectors、欄名/來源分開、同 hit 三欄對齊、空 event 留列、列印不控制資料輸出、Write/CloseFile 皆需成功；逐 strip 門檻使相同 raw 總量依空間分布留下不同 readout 能量。
Implementation evidence [CODEX-VERIFIED]: Ubuntu build/run 成功；兩 runs 各100 ROOT列，print off仍留列，run0逐event tuples對回 diagnostics；人工 fixture 空→H1兩筆→空，驗證 strip0、clear、0.20邊界/raw保留，非物理 beam test。新驗證並未在本次筆記同步重跑。
Mastery change: 七切片因果解釋及三題讀懂檢查支持 UNDERSTOOD；修正 last-step/累積與 []/[0] 混淆；無 INDEPENDENT/TRANSFERRED/RETAINED 宣稱。
Next step: 定義 existing vectors 的 event selected energy sum，未開始新教學。
Evidence location: 本機 LEARNING_PROGRESS.md、notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md、HandsOn03/HandsOn3；外部 logs /home/sundae/jlab-build/HandsOn03-hodoscope。[SOURCE-VERIFIED] 原課程註解題號已核對。[UNVERIFIED] 本次檔案未commit/push，不能宣稱GitHub已有最新證據。Learning Log保留歷史，唯一目前位置見Current Learning State。

2026-10-07 晚間—MPPC 計數定義（引導式 EXAMPLE）
概念：區分到達、偵測／photoelectron、同光子重複進入及效率分母；40、12、80/100、150皆為教學例，實際 MPPC source/runtime 尚未定位。
[LEARNER-VERIFIED] 原文：「把收到的光轉成電訊號」；「欄位名稱不會改變程式實際累加的是什麼。」；「若程式每次進入都加一，沒有記錄哪些光子已算過，最後 counter 會是 3。」；「更改後光收集效率依然是 80%。」
提示：先教概念與數字例子再作答；只記回答證據，未評新的 mastery。
2026-10-08—筆記收尾與學習方式調整
入口、Current State、總地圖、主動複習中心、關鍵字與避坑頁整合受影響內容，保留歷史答題與實際模擬圖；不擴大需要補強清單。
24份參考檔案完成盤點與抽取（含一份重複手冊），部分相關章節／研究已選讀；並非所有書逐頁精讀。Perkins掃描PDF的全文OCR未完成，不編造頁碼。方法見主動複習中心。
本次未改source、未新增build/run、未commit/push，無新物理結果或mastery評分。下一步由導師先示範H1每event selected能量與空vector，再問一題；單元結束集中保存，避免筆記阻擋開課。

