---
title: "CLD Exercise 2"
created: 2026-06-30 15:13:50
tags:
  - CLD
  - Exercise
  - FGV
  - Timer
---

# 🛠️ CLD Exercise 2: Elapsed Time Express VI FGV

## 🎯 重要概念 (Core Concepts)
將 Exercise 1 的 Express VI 封裝進功能性全域變數 (FGV / Action Engine) 中。使用 Enum 控制「Reset」、「Set Auto Reset」、「Read Status」三種狀態。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 挑戰題要求加入「暫停 (Pause)」功能，這需要使用未初始化的移位暫存器 (Uninitialized Shift Register) 來儲存先前的經過時間，若未正確儲存會導致暫停後時間遺失。

---

## 🔗 關聯練習 (Related Exercises)
* 延伸自 [[CLD Exercise 1]]，其架構邏輯連接至 [[CLD Exercise 3]]。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
