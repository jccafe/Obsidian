---
title: "CLD Exercise 16"
created: 2026-06-30 15:13:51
tags:
  - CLD
  - Exercise
  - UI_Control
  - Property_Node
---

# 🛠️ CLD Exercise 16: State Machine with Enables and Disables

## 🎯 重要概念 (Core Concepts)
UI 控制項的動態啟用/停用 (Enable/Disable)。基於當前系統數值動態改變 UI 狀態（0 時禁用 Use、10 時禁用 Fill）。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 使用按鈕後需要讓按鈕 Disable 250毫秒的邏輯，若使用 Wait 函數可能會阻塞 UI 事件迴圈，需考量非阻塞寫法。Property Node 大量使用時可能造成的延遲。

---

## 🔗 關聯練習 (Related Exercises)
* 專注於 CLD 考試中常出現的 UI 控制流。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
