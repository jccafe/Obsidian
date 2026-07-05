---
title: "CLD Exercise 12"
created: 2026-06-30 15:13:51
tags:
  - CLD
  - Exercise
  - State_Machine
  - Command
---

# 🛠️ CLD Exercise 12: Sequencer State Machine

## 🎯 重要概念 (Core Concepts)
指令驅動的狀態機 (Command-driven State Machine)。透過讀取 Exercise 8 的格式，以「SetTime」或「RunState」字串動態決定狀態機進入哪個 Case 執行。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 字串比對時大小寫的容錯 (Case insensitive)。必須確保第一步強制為 SetTime，否則計時器預設為 0。

---

## 🔗 關聯練習 (Related Exercises)
* 依賴 [[CLD Exercise 8]] 提供的資料。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
