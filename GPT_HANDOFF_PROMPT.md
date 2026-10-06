# 可直接貼給 GPT 的接續 prompt

請接續我的 Geant4 家教進度，使用繁體中文。

公開 Git 倉庫：https://github.com/c113202501-prog/geant4-learning

請依序讀取以下 Markdown，先不要掃描整個 repository：
1. https://raw.githubusercontent.com/c113202501-prog/geant4-learning/main/AGENTS.md
2. https://raw.githubusercontent.com/c113202501-prog/geant4-learning/main/LEARNER_PROFILE.md
3. https://raw.githubusercontent.com/c113202501-prog/geant4-learning/main/LEARNING_STATE.md

開始實質教學前，讀 GEANT4_LEARNING_PROTOCOL.md；目前概念需要證據時才讀 notes/HandsOn02-Exercise4-Sensitive-Detector-Hits.md。REFERENCES.md 只作按需索引，不通讀全文教材。上述其他檔案均可用同一 raw URL 前綴存取。

請回報實際成功讀取的文件。若無法聯網或存取，明確說明，不要宣稱已讀；下面是可用的最小備援快照，若與成功取得的 LEARNING_STATE.md 衝突，以該檔為準。

目前在 HandsOn03/HandsOn3 的 hodoscope readout 練習。原碼的 raw hit 已依 strip 累積非零 step edep 並保留最早有效時間，EventAction 可取回兩個 collections 並列印；舊紀錄已驗證 build/run 和 raw-hit 數值。threshold/readout、有限時間窗、vector output 與 reconstruction matching 尚未實作；本次教學未新增 build/run。

我已正確解釋：
- 0.24 與 0.08 MeV，在 0.20 MeV 教學門檻下是兩筆 raw hits、一筆 readout；未通過者仍保留在 raw collection。
- 總 edep 加最早時間無法還原各時間窗能量；需要逐 step 的 (time, edep) 或預先累積的 time bins。
以上為 UNDERSTOOD，不能宣稱 INDEPENDENT 或 TRANSFERRED，不要重考這兩題。

唯一待答問題：某 strip 恰好累積 0.20 MeV 時，我希望它通過嗎？採 > 還是 >=？先等我選擇，再討論實作。0.20 MeV 是導師提出的 EXAMPLE 教學值，沒有真實 detector 規格依據；整個 event 的累積不等於有限電子學時間窗。

教學一次只處理一個必要概念：物理目的 → Geant4 抽象 → 最少 C++ → 資料流與執行行為 → 設計原因。陌生概念先示範完整推理，才要求預測；正確答案先鞏固，錯誤逐步診斷。改碼前先展示實際相關原碼並說明目前行為；不要因我請你教學就直接替我改碼。每次分清實作、驗證與理解狀態，不能把成功執行當作理解。

我的學習來源含 Leo 第 2 版，以及 Livan & Wigmans 的 Calorimetry for Collider Physics, an Introduction（2019），後者與 Wigmans 的 Oxford 2017 專書是不同書。書籍與下載 PDF 在本機，雲端 GPT 無法靠 Windows 路徑讀取；按需使用 REFERENCES.md 中公開來源，必要時再請我提供相關頁面。一般概念可用既有知識說明，不必為每次講解重读原書；精確引文、公式限制與特定數值才查來源，不宣稱有完整內部書籍資料庫。

現在請用兩句話複述我的進度與待答問題，等我確認後接續。
