---
title: "CLD 模擬試題詳細整理：Sprinkler Controller (灑水控制器)"
created: 2026-06-18 20:52:34
tags:
  - LabVIEW
  - CLD
  - 模擬試題
  - 中英對照
  - Sprinkler
---

# CLD 模擬試題詳細整理：Sprinkler Controller (灑水控制器)

本篇筆記針對模擬試題 `Sprinkler Controller (100927F-01).pdf` 之規格書進行詳細的系統化中英對照與邏輯拆解。

---

## 🎯 一、設計目標 (Objective)

| 英文規格 (English) | 中文對照 (Chinese) |
| :--- | :--- |
| Design a four zone sprinkler controller using LabVIEW. | 使用 LabVIEW 設計一個包含四個分區的草坪灑水控制器。 |
| The sprinkler controller services four zones: North, South, East, and West. | 控制器依序為北、南、東、西四個灑水區域提供服務。 |

---

## 🔄 二、運作順序要求 (Sequence of Operation)

| 階段 (Stage) | 英文規範 (English) | 中文規範 (Chinese) |
| :--- | :--- | :--- |
| **啟動 (VI Load/Start)**| Load the Zone Setup Array data from a CSV file. Zone Setup Array is dimmed. Indicators are OFF, Timing is 0, Status shows "Controller Initialized". | 程式執行時，自設定檔讀取灑水配置，並載入至 Zone Setup 陣列中。該控制陣列隨後轉為灰色停用。LED 熄滅，時間顯示 0，Status 顯示 Controller Initialized。 |
| **設定模式 (Setup)** | Click Setup. Enable Zone Setup array to allow changing Zone Selector and Timing. Controller Status displays "Setup Mode". Clicking Setup during run stops controller. | 點擊 Setup 按鈕。啟用陣列設定以容許手動更改分區順序與秒數。狀態變為 Setup Mode。運行中點擊 Setup 會立即中斷執行並進入設定狀態。 |
| **單次運行 (Single)** | Services each zone in the array for the set Timing sequentially. After one pass, wait for user action. Status continues to display "Running". | 選擇 Single 運行模式 ➡️ 點擊 Start ➡️ 依序對陣列中各區進行一次灑水，完成後保持 Running 狀態並靜止待命。 |
| **連續運行 (Continuous)**| Continually cycle through the Zone Setup array by restarting with the first zone after servicing the last zone. | 選擇 Continuous 運行模式 ➡️ 點擊 Start ➡️ 循環執行。完成最後一個分區的灑水後，自動重設並從第一個分區重頭開始。 |
| **模式切換** | If Run Selector is moved from Continuous to Single during a run, stop after servicing the last zone. | 運行中若將模式選擇器從 Continuous 切換為 Single，系統必須在跑完目前的完整週期（最後一個分區結束）後停止。 |
| **水壓限制 (Pressure)** | Before start, check Water Pressure Sensor. If < 50%, display "Low Water Pressure". Restore to > 50% to start. If pressure drops during run, stop and display error, start from zone 1 when restored. | 啟動時與執行中，水壓低於 50% ➡️ 暫停灑水，狀態顯示 Low Water Pressure。水壓恢復（大於 50%）後，**從第一區重新開始計時計畫**。 |
| **下雨中斷 (Rain)** | If it begins to rain (Rain Sensor switch), stop servicing zones and display "Rain". If rain stops, Single mode does one pass, Continuous starts from zone 1. | 執行中若 Rain Sensor 偵測到下雨 ➡️ 立即中斷灑水並顯示 Rain。雨停後，Single 模式會重新執行一次完整 pass；Continuous 模式則**從第一區重頭開始**。 |
| **停止 (Stop)** | Click Stop. Stop servicing zones, display "Stopped" in status, and stop the application. | 點選 Stop 按鈕。立即停止灑水，狀態顯示 Stopped，隨後終止程式。 |

---

## 📂 三、灑水配置檔案規範 (Sprinkler Configuration File)

* **檔案格式**：Comma Separated Value (.csv)。
* **讀取規則**：啟動時由程式背景讀取，並直接初始化 Zone Setup 陣列。若區塊的 Timing（時間）被設定為 `0`，則執行時**跳過該區塊**，直接前進到下一區。
