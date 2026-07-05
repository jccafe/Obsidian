---
title: "CLD Exercise 3"
created: 2026-06-30 15:13:50
tags:
  - CLD
  - Exercise
  - Action_Engine
  - Timer
---

# 🛠️ CLD Exercise 3: Action Engine Timer

## 🎯 重要概念 (Core Concepts)
不使用 Express VI，改以純 LabVIEW 函數 (Get Date/Time in Seconds 或 Tick Count) 實作包含暫停、繼續、讀取時間的 FGV 計時器。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 使用 Tick Count (ms) 時會遇到毫秒計時器「歸零/溢位 (turnover)」的問題，必須在設計時考慮如何解決這個邊界條件。此外，暫停時的數值保留邏輯容易出錯。

---

## 🔗 關聯練習 (Related Exercises)
* 進階版計時器，核心概念將應用於 [[CLD Exercise 14]]。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
