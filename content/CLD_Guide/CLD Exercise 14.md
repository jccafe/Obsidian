---
title: "CLD Exercise 14"
created: 2026-06-30 15:13:51
tags:
  - CLD
  - Exercise
  - State_Machine
  - Timer
---

# 🛠️ CLD Exercise 14: Timer Application With File Time Targets

## 🎯 重要概念 (Core Concepts)
進階計時狀態機，具備「暫停 (Pause)」與「取消 (Cancel) 目前步驟」跳至下一步的功能。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 在暫停狀態下按下 Cancel 時，必須同時解除暫停並直接跳入下一個目標時間，狀態切換間極易遺失計時資料。

---

## 🔗 關聯練習 (Related Exercises)
* 使用 [[CLD Exercise 3]] 概念的應用實例。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
