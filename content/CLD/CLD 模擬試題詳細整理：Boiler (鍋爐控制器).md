---
title: "CLD 模擬試題詳細整理：Boiler (鍋爐控制器)"
created: 2026-06-18 20:52:34
tags:
  - LabVIEW
  - CLD
  - 模擬試題
  - 中英對照
  - Boiler
---

# CLD 模擬試題詳細整理：Boiler (鍋爐控制器)

本篇筆記針對模擬試題 `Boiler (100926F-01).pdf` 之規格書進行詳細的系統化中英對照與邏輯拆解。

---

## 🎯 一、設計目標 (Objective)

| 英文規格 (English) | 中文對照 (Chinese) |
| :--- | :--- |
| Design a boiler startup controller using LabVIEW. | 使用 LabVIEW 設計一個鍋爐啟動與關閉的監控系統。 |
| The controller displays status and logs events as they occur during the process. | 控制器顯示當前狀態與步驟，並在過程中即時將事件記錄到記錄檔。 |

---

## 📊 二、事件日誌檔案規範 (Event Log File Specification)

* **檔案名稱**：`Boiler Log.txt` (CSV 格式，須與主 VI 放在同一目錄下)。
* **檔案標頭 (Header)**：`Timestamp, Event, Event Data`
* **資料欄位格式**：`絕對日期與時間字串, 事件字串, 事件數據字串`
* **修改原則**：若檔案不存在則新建並寫入標頭與首筆日誌；若已存在則以追加 (Append) 模式寫入。

---

## 🔄 三、運作順序與日誌記錄要求 (Sequence of Operation)

| 步驟 (Step) | 系統動作與狀態 (Actions & Status) | 日誌記錄欄位與數值 (Logged Event / Data) |
| :--- | :--- | :--- |
| **啟動 (Start)** | 程式啟動時，Status 顯示 `Lockout`，所有指示燈熄滅。 | **Event**: `Boiler Initialized`<br>**Event data**: `0` |
| **解鎖 (Reset Lockout)** | 將 Run Interlock 開關切至閉合，並點擊 Boiler Reset 按鈕。Status 變為 `Ready`。 | **Event**: `Boiler Ready`<br>**Event data**: `0` |
| **預洗滌 (Pre-Purge)** | 點擊 Start Sequence 按鈕。啟動 Primary Fan (LED亮)。計時 10 秒。Status 顯示 `Pre-Purge`。時間指示器累加秒數。 | **Event**: `Start Pre-Purge`<br>**Event data**: 預洗滌經過時間 (秒) |
| **預洗滌完成** | 10 秒計時結束。Primary Fan LED 熄滅，時間清零。Status 顯示 `Pre-Purge Complete`。**Pilot 按鈕開始閃爍**。 | **Event**: `Pre-Purge Complete`<br>**Event data**: 預洗滌經過時間 (秒) |
| **點火 (Ignition)** | 點擊閃爍的 Pilot 按鈕。停止閃爍。開啟 Natural Gas Valve LED 與 Pilot LED。Status 顯示 `Pilot On`。 | **Event**: `Pilot ON`<br>**Event data**: `True` |
| **驗證點火 (Prove Pilot)**| 手動將 Flame Sensor Value 滑桿往上拉。當數值大於 30% 時，Status 顯示 `Boiler Ready`。 | **Event**: `Pilot Proved`<br>**Event data**: 該滑桿目前的數值百分比 |
| **啟動運行 - Step 1** | 開啟 Forced Draft Fan 開關，FD Fan LED 亮起。 | **Event**: `Forced Draft Fan ON`<br>**Event data**: `True` |
| **啟動運行 - Step 2** | 調整 Fuel Control Valve Position 旋鈕大於 10%。Fuel Valve LED 亮起，Gas Valve & Pilot LED 熄滅。Status 顯示 `Boiler Running`。正常範圍為 10% ~ 75%。 | **Event**: `Boiler Running`<br>**Event data**: 閥門位置數值百分比 |
| **安全關閉與洗滌** | 運行中若遇到：按 Shutdown、閥門數值不在 10-75%、Run Interlock 斷開、FD Fan 關閉 ➡️ 進入 10 秒 Purge 狀態：關閉 Fuel Valve，開啟 Primary Fan，Status 顯示 `Purge`。 | **Event**: `Start Shutdown Purge`<br>**Event data**: 關閉洗滌經過時間 |
| **關閉完成** | 10 秒洗滌計時完畢。Status 回到 `Lockout`，所有 LED 熄滅。 | **Event**: `Shutdown Purge Complete`<br>**Event data**: 關閉洗滌經過時間 |

---

## ⚠️ 四、非正常關閉條件 (Shutdown Trigger Conditions)
在運作狀態 (`Boiler Running`) 下，滿足下列任一條件會**立即中斷**並強制轉入 10 秒的 **Shutdown & Purge** 洗滌安全程序：
1. 按下 `Boiler Shutdown` 切換開關。
2. 燃料控制閥 `Fuel Control Valve Position` 小於 10% 或大於 75%。
3. 外部連鎖開關 `Run Interlock` 斷開 (Open)。
4. 強制排風扇 `Forced Draft Fan` 開關被關閉 (OFF)。
