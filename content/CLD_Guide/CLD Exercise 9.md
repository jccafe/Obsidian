---
title: "CLD Exercise 9"
created: 2026-06-30 15:13:50
tags:
  - CLD
  - Exercise
  - Sequencer
  - Timer
---

# 🛠️ CLD Exercise 9: Step Sequencer with Elapsed Time Express VI Timer

## 🎯 重要概念 (Core Concepts)
硬編碼的步驟循序器 (Step Sequencer)。使用三個寫死的目標時間常數與布林狀態，利用計時器完成時發出 Time Has Elapsed 與 Auto Reset 訊號來推動下一步。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 強制覆寫機制（當 Time Target 輸入大於 0 時，必須無條件蓋過常數時間），以及在自動重置關閉時停止進入下一步的狀態流動控制。

---

## 🔗 關聯練習 (Related Exercises)
* 進階版本的基礎，將被 [[CLD Exercise 10]] 取代。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
