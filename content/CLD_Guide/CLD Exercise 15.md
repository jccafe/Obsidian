---
title: "CLD Exercise 15"
created: 2026-06-30 15:13:51
tags:
  - CLD
  - Exercise
  - CSV
  - String_Parsing
---

# 🛠️ CLD Exercise 15: CSV File Text String Parsing

## 🎯 重要概念 (Core Concepts)
高階 CSV 字串解析與商業邏輯運算。解析字串如 `091,TX78701Travis+02`，將其拆解為數量、州、郵遞區號、郡與價格折扣，並進行數值轉換（例如 $1000 以上為大訂單）後重新寫入檔案。

---

## ⚠️ 易錯內容 (Gotchas / Common Mistakes)
> [!WARNING]
> 正規表達式或字串分割的使用錯誤。價格折扣 (+/-) 的百分比轉換計算 (例如 `-3` 轉換為 `0.97` 乘數)。

---

## 🔗 關聯練習 (Related Exercises)
* 與 [[CLD Exercise 7]] 均為字串處理技巧，挑戰題要求將此改寫為 FGV。
* 上級指南：[[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]]
* 總入口：[[Notes/000_Index 索引：Obsidian 自動化專案]]
