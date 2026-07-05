---
title: "000_Index 索引：Obsidian 自動化專案"
created: 2026-06-18 20:34:18
tags:
  - 索引
  - 地圖
  - obsidian
  - 導覽
---

# Index 索引：Obsidian 自動化專案

歡迎使用 Obsidian 自動化專案！本頁是您 Vault 的導覽地圖 (MOC)，整理了本專案的所有關聯筆記、目錄結構以及常用指令。

---

## 🗺️ 筆記地圖 (Map of Content)

### 📂 一、淡水國中 (TSJH) 原創教學與資優課程庫
* **[[TSJH/淡水國中理化與資優教學資源總庫 MOC|淡水國中理化與資優教學資源總庫 MOC]]** —— TSJH 教學資源庫總入口。
  * ↳ [[TSJH/淡水國中理化教學講義與專題彙整|淡水國中理化教學講義與專題彙整]] —— 核心理化講義、LaTeX 公式與知識整理。
  * ↳ [[TSJH/淡水國中特教與資優班課程規劃|淡水國中特教與資優班課程規劃]] —— 生物資優 PBL 設計、科學營教案講義。
  * ↳ [[TSJH/淡水國中理化會考分析與模擬考試題研究|淡水國中理化會考分析與模擬考試題研究]] —— 會考自然科準備策略與變因分析。
  * ↳ [[TSJH/淡水國中教師專業成長與跨校共備紀錄|淡水國中教師專業成長與跨校共備紀錄]] —— 跨校共備精華與素養評量趨勢。
  * ↳ [[TSJH/實驗專題：食鹽水溶液的濃度與密度關係|實驗專題：食鹽水溶液的濃度與密度關係]] —— 濃度與密度探究實驗。
  * ↳ [[TSJH/科學探究：浮沉子與氣體壓力|科學探究：浮沉子與氣體壓力]] —— 浮力與氣體壓力探究。
  * ↳ [[TSJH/科學史話：2016諾貝爾化學獎與分子機器|科學史話：2016諾貝爾化學獎與分子機器]] —— 拓樸化學科普文章。

### 📂 二、國高中理化核心公式與定律 (Science)
* **[[Science/國高中理化核心公式與定律總整理|國高中理化核心公式與定律總整理]]** —— 理化公式與專題知識網絡地圖。
  * ↳ [[Science/理化專題：力學與靜力平衡 (Mechanics & Statics)|理化專題：力學與靜力平衡]]
  * ↳ [[Science/理化專題：運動學 (Kinematics)|理化專題：運動學]]
  * ↳ [[Science/理化專題：流體力學與壓力 (Fluid Mechanics)|理化專題：流體力學與壓力]]
  * ↳ [[Science/理化專題：熱學與熱量 (Thermodynamics)|理化專題：熱學與熱量]]
  * ↳ [[Science/理化專題：功、能與功率 (Work, Energy & Power)|理化專題：功、能與功率]]
  * ↳ [[Science/理化專題：電學 (Electricity)|理化專題：電學]]

### 📂 三、CLD 認證與實戰筆記 (CLD)
* **[[💡 CLD 實戰筆記（自我檢討）|💡 CLD 實戰筆記（自我檢討）]]** —— 實戰技巧、架構與細節提示。
  * ↳ [[CLD_Guide/LabVIEW CLD 認證實戰練習與架構指南|LabVIEW CLD 認證實戰練習與架構指南]] —— 17 個練習的重點概念與 Gotchas 總整理。
  * ↳ [[CLD_sample_exams_english/ATM Exam|CLD 英文模擬考題知識庫 (ATM, Boiler, Car Wash, Sprinkler)]] —— 四大經典考題與練習單元雙向連結網絡。
  * ↳ [[CLD 1 Elapsed Time Express VI.pdf|CLD 1 Elapsed Time Express VI.pdf.md]] | [[Elapsed Time Express VI 邏輯拆解|Elapsed Time Express VI 邏輯拆解]] | [[CLD/Elapsed Time Express VI 流程圖]]
  * ↳ [[CLD 2 Elapsed Time FGV.pdf|CLD 2 Elapsed Time FGV.pdf.md]]
  * ↳ [[⚙️ 核心邏輯 (Core Logic)]] | [[📥 輸入控制 (Inputs)]] | [[📊 輸出顯示 (Outputs)]]

### 📂 四、自動化專案行政與技術
* **[[Obsidian 自動化工具核心邏輯]]** —— 程式碼設計、雙模寫入、智慧金鑰過濾與降級機制說明。
  * ↳ [[專案計劃]] —— 專案初始的實施計劃與選擇。
  * ↳ [[API連線成功筆記]] —— 首次成功使用 REST API 即時建立的測試筆記。

---

## 📁 專案目錄結構

* 📂 `TSJH/`：存放淡水國中理化與資優教學資源的整理筆記。
* 📂 `Science/`：存放國高中理化核心公式與學科專題筆記。
* 📂 `CLD/`：存放 CLD 認證考試與 Express VI、FGV 相關實作筆記。
* 📂 `Notes/`：存放一般知識、專案與技術核心筆記。
* 📂 `Daily/`：存放依日期命名的每日隨筆與待辦事項 (`YYYY-MM-DD.md`)。
* 📂 `Templates/`：預留存放日記與常用筆記格式的範本目錄。
* 📂 `Resources/`：預留存放圖片、錄音與其他附件的媒體資料夾。

---

## 💻 常用命令速查表

在目錄 `k:\Antigravity_folio\obsidian` 下執行：

| 目的 | 命令範例 |
| :--- | :--- |
| **測試 API 連線** | `python obsidian_tool.py test-api` |
| **建立新筆記** | `python obsidian_tool.py create --title "筆記名稱" --tags "標籤1,標籤2" --content "內容"` |
| **建立並自動開啟** | 在建立命令最後加上 `-o` 或 `--open` 參數 |
| **追加今日日記** | `python obsidian_tool.py daily --content "追加的紀錄"` |
| **在軟體中開啟此 Vault** | `python obsidian_tool.py open` |
