# 資料權責、接手與紀錄規範

更新：2026-10-08，依使用者明確更正恢復 GitHub／Notion 分工。此版取代本機舊的 Notion-authority/cache 規範；使用者最新指示優先。

## 唯一位置與用途

| 事項 | 權威／用途 |
|---|---|
| 當前概念、待答題、下一步 | GitHub LEARNING_STATE.md，唯一目前狀態 |
| session 答題原文、提示程度、學習範圍 | GitHub LEARNING_LOG.md，供 Codex/GPT 閱讀 |
| 實作與驗證的時間序列 | GitHub LEARNING_PROGRESS.md，附發布邊界 |
| 程式行為 | actual source／runtime；與紀錄不同時核對並修正 |
| 概念解釋與來源 | notes/、REFERENCES.md；不維護第二套下一步 |
| 學生閱讀／複習與排程 | Notion；當前狀態頁為 Git state 的閱讀投影 |
| 本機未發布修改 | 工作稿；不能冒充遠端已保存或 source 已發布 |

## 接手

按 AGENTS → LEARNER_PROFILE → LEARNING_STATE → 當前必要 note/source。需歷史才看 LOG／PROGRESS。STATE 落後於最新對話或證據就修正後接續，不重教已回答的概念。SESSION_HANDOFF 是摘要入口，不能覆蓋較新的 STATE。Notion 不必每次重讀；連線失敗時照已核對的 Git state 接續並記待投影項。

## 記錄與發布

單元結束或使用者要求時集中保存，不每題更新所有頁面。先保留歷史與證據，再更新唯一 STATE；Notion 只投影學生需要的概念、案例、限制與複習提示。只更新受影響文件／頁面。

GitHub API 寫入或 git commit/push 都可能發布文件；逐一確認遠端內容後才宣稱成功。明確區分文件發布與 simulator source／outputs 發布。本機 checkout 的 HEAD 可能落後於 API 提交，不為同步而覆寫學習者的未提交 source。記錄原文、題目、提示、來源與未做事項；build/run 不等於 mastery。正式 mastery 依 GEANT4_LEARNING_PROTOCOL，保留歷史標籤、不自動升級。

## 證據標籤

- LEARNER-VERIFIED：學習者的回答／預測／解釋；註明是否先教、提示或提供數字。
- CODEX-VERIFIED：實際檢查程式／輸出／build/run；未重跑就標既有證據。
- SOURCE-VERIFIED：實際讀過的官方文件／教材章節；不編版本、頁碼或全文閱讀。
- UNVERIFIED：未知／推論／待查，不補造。

## 本次分工修正

歷史 Notion Learning Log 完整移植到 notes/archive/Notion-Learning-Log-2026-10-08.md，機器日誌用 LEARNING_LOG.md。只有遠端保存已確認才依使用者指示把 Notion 同名頁移到可恢復垃圾桶；不清空垃圾桶。學生筆記頁保留。
