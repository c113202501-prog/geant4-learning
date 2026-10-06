# Geant4／ZDC 教學參考索引

整理日期：2026-10-06。這是按概念選讀的索引，不是全文摘要或熟練度紀錄；目前進度以 LEARNING_STATE.md 為準。

## 使用規則

- 教新概念前查本索引，只讀吻合概念的相關段落；每個 session 最多兩份來源，每份一個重點，說明與今天概念的關聯。
- 陌生概念先依教學 protocol 建模；具備先備後，先讓學習者預測，再用文獻驗證或補充，不先揭露待判斷的結論。
- 先備未具備時先補最小必要概念，將待用來源記入下一步，不把本索引列出的概念當作已掌握。
- 用自己的話解釋並標來源、版本與實際章節／頁碼。未核對的章節不編造編號。
- 設計文件不確定是否最新時，說明版本日期與不確定性，請學習者確認後才將其當成現行設計規格。
- PDF 放 notes/refs/；下載與雜湊記錄見 download-manifest.json。下載不等於已精讀。
- 2026-10-06 學習者明確偏好節省 token：已掌握的一般概念可直接融入教學，不為每次講解重讀原書；需要確切引文、頁碼、公式限制或特定實驗數值時才查相關頁面。不可宣稱有可查詢的完整內部書籍資料庫，也不可把模型既有知識當作已核對原書。
- 不整本 OCR。先抽查文字層；只有當前所需頁面無法可靠擷取時才局部 OCR，尤其核對公式與圖表標籤。

## A. 基礎與速查

### Leo — Techniques for Nuclear and Particle Physics Experiments
- 來源：William R. Leo，第 2 版（1994），[出版社](https://link.springer.com/book/10.1007/978-3-642-57920-2)。
- 位置：既有 C:/Users/User/Downloads/Techniques-for-nuclear-and-parti.epub；付費書籍未另下載全文。既有 EPUB 的 OPF metadata 為 title=index、creator=Unknown，無法確認書名與版本；可由學習者用大學圖書館取得正式第 2 版。
- 新增可用來源：C:/Users/User/Documents/ChatGPT/Geant4/William R. Leo - Techniques for Nuclear and Particle Physics Experiments_ A How-to Approach (1994, Springer) - libgen.li.pdf。2026-10-06 核對共 384 個 PDF 頁面，書名頁標示 Second Revised Edition；抽查 PDF 第 1、2、6、21、81 頁有文字層，無須先整本 OCR。公式擷取可能有錯字，使用時核對對應頁面影像。
- 用途：從粒子與物質作用連到 detector response。
- 先備：粒子種類、能量及長度單位；解釋前先確認 incident energy 與 deposited energy 的差別。
- 適用概念：能量損失、散射、輻射長度、粒子作用機制、閃爍及電子學。
- 選讀：第 2 章 Passage of Radiation Through Matter（出版社第 2 版 pp.17–68）；閃爍或 threshold 再查 Scintillation Detectors、Pulse Height Selection and Coincidence Technique。

### Wigmans — Calorimetry: Energy Measurement in Particle Physics
- 來源：Richard Wigmans，[第 2 版（2017）出版社](https://academic.oup.com/book/26593)。
- 位置：出版社連結；尚未取得可公開下載的完整書籍。
- 取得識別：Richard Wigmans 著，Oxford University Press，2017，第 2 版；ISBN 9780198786351。可由學習者透過大學圖書館取得。
- 已提供檔案核對：C:/Users/User/Documents/ChatGPT/Geant4/Calorimetry – energy measurements in particle physics, 2nd edition, by R. Wigmans (Vogel, Manuel) (z-library.sk, 1lib.sk, z-lib.sk).epub 是兩頁掃描式 EPUB；第二頁標示 BOOK REVIEW，作者 Manuel Vogel（2018），DOI 10.1080/00107514.2018.1450300。這是書評，不是 Wigmans 專書全文，不可替代上述理論來源。
- 用途：深化強子能量量測及設計取捨。
- 先備：電磁／強子 shower、active／absorber 分層、sampling fraction；e/h 前先建立電磁成分與不可見能量。
- 適用概念：sampling fluctuation、e/h、compensation、non-linearity、解析度、校正。
- 選讀：第 2 章 shower；第 3 章 response；第 4 章 fluctuations；第 6 章 calibration；第 9 章 test-beam interpretation。一次只取當前問題所需段落。

### Fabjan & Gianotti — Calorimetry for particle physics
- 來源：[Rev. Mod. Phys. 75, 1243–1286 (2003)](https://doi.org/10.1103/RevModPhys.75.1243)。
- 位置：notes/refs/Fabjan-Gianotti-2003.pdf；[CERN 全文](https://cds.cern.ch/record/692252/files/RevModPhys.75.1243.pdf)下載回傳驗證頁，改用 [KEK 公開副本](https://research.kek.jp/people/koma/work/work_kaon/e391/seminar/pdf/RMPv75p1287.pdf)。
- 用途：先建立 calorimetry 全貌，再按需進 Wigmans。
- 先備：能量沉積與讀出訊號分層、平均值／波動的意義。
- 適用概念：電磁與強子 calorimetry、sampling、response、resolution。
- 選讀：電磁 calorimetry 的 Section II；強子主題按全文目錄定位，只讀相關段落。不要用此篇替代特定 SiPM／threshold 電子學規格。

### PDG — Passage of Particles Through Matter
- 來源：[2025 PDF](https://pdg.lbl.gov/2025/reviews/rpp2025-rev-passage-particles-matter.pdf)。本次找到的版本，未宣稱為 2026 最新版。
- 位置：notes/refs/PDG-2025-passage-particles-matter.pdf。
- 用途：定義、公式、尺度與材料參數速查。
- 先備：單位、密度、能量損失；使用公式前確認變數與適用粒子／能量範圍。
- 適用概念：stopping power、radiation length、critical energy、電磁 shower、multiple scattering、interaction length 的相關尺度。
- 選讀：按關鍵字定位，讀定義與限制，不從頭通讀。

## B. 實驗主線（依序精讀，按先備拆小段）

### 已新增的 calorimetry 入門書：Livan & Wigmans（2019）
- 書名：Calorimetry for Collider Physics, an Introduction；Michele Livan、Richard Wigmans，Springer，2019；DOI 10.1007/978-3-030-23653-3。
- 位置：C:/Users/User/Documents/ChatGPT/Geant4/[UNITEXT for Physics ] Michele Livan, Richard Wigmans - Calorimetry for Collider Physics, an Introduction (2019, Springer) [10.1007_978-3-030-23653-3] - libgen.li.pdf。
- 核對：270 個 PDF 頁面；書名頁確認作者及書名，抽查 PDF 第 1、2、6、21、81 頁可擷取文字，無須先整本 OCR。
- 用途：可作目前 calorimetry 入門教學來源；與 Wigmans 的 2017 Oxford 專書分別列記，不混用書名與章節。
- 先備：incident energy／edep／readout 的差別；shower 前先建立粒子作用與 active／absorber 分層。
- 適用概念：shower development、sampling calorimeter、response、resolution、calibration、dual readout。
- 選讀：以當前概念查目錄與單一小節。PDF 第 81 頁可見第 3 章 Shower Development；其餘章節編號按需核對，不套用 Oxford 書的章節編號。

### arXiv:2603.14167 — Beam Test of a SiPM-on-Tile ZDC Prototype with 5.3 GeV Positrons at Jefferson Laboratory
- 來源：[arXiv，v2](https://arxiv.org/abs/2603.14167v2)。
- 位置：notes/refs/2603.14167.pdf。
- 用途：15 層原型機 beam test 與模擬比較的主線；此項是 positron 測試，不直接當作強子性能驗證。
- 先備：raw hit 累積（目前已有理解證據）；精讀 response 比較前補 sampling、訊號校正、能量分布及解析度。
- 適用概念：sampling calorimeter、SiPM-on-tile、能量響應、shower shape、simulation/data comparison。
- 選讀：先 detector／beam-test setup，再依當前問題查 response 或 simulation；使用具體層數、cut 與校正數值前核對正文。

### arXiv:2512.20852 — Calibration of an Irradiated Prototype for the EIC Zero-Degree Calorimeter
- 來源：[arXiv，v4](https://arxiv.org/abs/2512.20852v4)。
- 位置：notes/refs/2512.20852.pdf。
- 用途：把量測訊號、通道校正與輻照後性能連起來。
- 先備：訊號與 edep 差別、SiPM gain／noise、校正係數、pedestal；先確認輻照改變的是哪個響應環節。
- 適用概念：irradiation、calibration、channel response、SiPM noise、性能比較。
- 選讀：校正方法及一個對應結果；不把某原型機的參數直接套進目前 hodoscope。

### EIC Yellow Report — arXiv:2103.05419
- 來源：[Science Requirements and Detector Concepts for the Electron-Ion Collider](https://arxiv.org/abs/2103.05419)。
- 位置：notes/refs/2103.05419.pdf。
- 用途：解釋 far-forward／ZDC 量測對物理問題的用途與需求。
- 先備：beam direction、角度與接受度、neutral／charged 粒子；相關物理通道按需補，不先要求整套 EIC 理論。
- 適用概念：far-forward acceptance、ZDC、forward neutrons、energy／position resolution requirements。
- 選讀：搜尋 far-forward、zero-degree、ZDC，僅讀相應章節。物理需求與現行工程設計分開核對。

### ePIC Preliminary Technical Design Report — Version 3.1
- 來源：[合作團隊更新存檔／DOI 10.5281/zenodo.19496158](https://zenodo.org/records/19496158)，發布日期 2026-04-10，Version 3.1 加行號版。原始 2026-01-16 存檔為 DOI 10.5281/zenodo.18271602。
- 位置：notes/refs/ePIC-preTDR-3.1.pdf。
- 狀態：2026-10-06 查詢 Zenodo 原始記錄的 versions/latest 所得公開版本；不是已確認的最終 TDR，也不保證涵蓋所有後續設計審查。
- 用途：將 Yellow Report 需求對應到具體 detector 設計。
- 先備：Yellow Report 的相應需求、sampling calorimeter、geometry acceptance、讀出與校正分層。
- 適用概念：far-forward layout、ZDC geometry／materials／readout、design requirements。
- 選讀：按目錄找 far-forward／ZDC；採用尺寸或參數前核對版本及後續設計審查。若要用作現行規格，先告知版本不確定性並請學習者確認。

## C. Geant4 官方（配合實作）

### Book for Application Developers
- 來源：[官方 PDF](https://geant4.web.cern.ch/documentation/dev/bfad_pdf/BookForApplicationDevelopers.pdf)。
- 位置：notes/refs/Geant4-ApplicationDeveloperGuide.pdf。
- 先備：目前真實 exercise 的 class／callback 資料流、必要 C++。
- 適用概念：Sensitive Detector、hits、digitization、analysis、geometry、materials。
- 用途與選讀：只讀目前 API／lifecycle 對應章節；下載的是官方 dev 文件，引用前核對文件版本與專案 Geant4 11.4.2。

### Physics Reference Manual
- 來源：[官方 PDF](https://geant4.web.cern.ch/documentation/dev/prm_pdf/PhysicsReferenceManual.pdf)。
- 位置：notes/refs/Geant4-PhysicsReferenceManual.pdf。
- 先備：對應物理作用、能量範圍、process／model 區別。
- 適用概念：electromagnetic／hadronic shower、能量損失、Birks／G4EmSaturation。
- 用途與選讀：核對模型假設及適用範圍；FTFP_BERT 的組合另查同版本 Physics List Guide，不從名稱推測 shower 品質。

### B4 — calorimeter examples
- 來源：[官方原碼](https://github.com/Geant4/geant4/tree/v11.4.2/examples/basic/B4)。
- 位置：線上 source；不是 PDF，本次未另複製程式。
- 先備：step／event、raw edep 累積、geometry 的 logical／physical volume。
- 適用概念：absorber／active 分層、event energy sum、不同 scoring 實作、analysis。
- 用途與選讀：下一個 calorimeter 實作入口；一次選一個 B4 variant，只讀當前資料流涉及的檔案。

### B5 — detector／hodoscope example
- 來源：[官方原碼](https://github.com/Geant4/geant4/tree/v11.4.2/examples/basic/B5)。
- 位置：目前課程改編程式 HandsOn03/HandsOn3；以實際本地程式為教學依據。
- 先備：step／track、hit collection、event callbacks。
- 適用概念：hodoscope、Sensitive Detector、per-channel hits、event-level access。
- 用途與選讀：對照 framework 設計；官方 B5 與課程版本有差異，不能將官方行為當成本地已實作行為。

## D. 概念 → 最小來源路徑

| 待補概念 | 優先來源 | 使用前先備 |
|---|---|---|
| radiation length／nuclear interaction length | Leo／PDG | 粒子作用種類、長度與密度單位 |
| sampling fraction | B4／Fabjan & Gianotti | active 與 absorber、edep 與 incident energy |
| stochastic／constant resolution terms | Fabjan & Gianotti／Wigmans | 平均值、標準差、sigma/E、能量單位 |
| sampling fluctuation | Wigmans | sampling fraction、event-to-event 波動 |
| e/h／compensation | Wigmans | EM／hadronic shower 成分及不可見能量 |
| Birks saturation／G4EmSaturation | Leo／Geant4 PRM | dE/dx、edep 與 visible response 的差別 |
| SiPM response | beam-test／irradiation 論文 | photons、gain、noise、photoelectron 與 ADC 分層 |
| FTFP_BERT 與 shower shape | 同版本官方物理文件／beam-test 論文 | hadronic models、縱向／橫向 shower 分布與比較條件 |

目前接續點仍是 raw hit → readout threshold；尚無真實 threshold、integration window、gain 或 noise 規格。此索引不改動當前熟練度或將文獻參數自動採用為 detector 規格。
