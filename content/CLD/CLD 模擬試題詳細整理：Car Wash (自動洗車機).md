---
title: "CLD 模擬試題詳細整理：Car Wash (自動洗車機)"
created: 2026-06-18 20:52:34
tags:
  - LabVIEW
  - CLD
  - 模擬試題
  - 中英對照
  - Car_Wash
---

# CLD 模擬試題詳細整理：Car Wash (自動洗車機)

本篇筆記針對模擬試題 `Car Wash (100929B-01).pdf` 之規格書進行詳細的系統化中英對照與邏輯拆解。

---

## 🎯 一、設計目標 (Objective)

| 英文規格 (English) | 中文對照 (Chinese) |
| :--- | :--- |
| Design a car wash controller using LabVIEW. | 使用 LabVIEW 設計一個自動洗車控制器。 |
| The controller simulates options selection and vehicle travel in the car wash. | 此控制器模擬洗車方案選擇，以及車輛在洗車機內的位置移動與狀態。 |

---

## 🔄 二、運作順序要求 (Sequence of Operation)

| 階段 (Stage) | 英文規範 (English) | 中文規範 (Chinese) |
| :--- | :--- | :--- |
| **啟動 (Start)** | Entry Console is enabled. Wash Entry LED is green and displays "Wash Vacant". All indicators are OFF and Elapsed Time is 0.00. Car Position Slider is at "Entry". | 啟動時，控制面板為啟用狀態。門口 LED 顯示綠色並呈現 Wash Vacant (無車)。所有洗車指示 LED 均熄滅，經過時間為 0.00。車輛位置滑桿在 Entry 處。 |
| **選擇方案 (Options)** | Click the Wash Options buttons to select steps. Buttons remain clicked until wash completes. | 點選選單按鈕（如 Under Body Wash 等）選擇要執行的洗車流程。按鈕點下後應保持下陷，直到整個洗車程序結束。 |
| **預設高壓清洗** | High Pressure Wash is the default. If no options are selected, it must be added programmatically after clicking Start. | 高壓清洗 (High Pressure Wash) 是預設步驟。若使用者沒有選取任何項目，點擊 Start 後系統必須自動補上該步驟。 |
| **啟動清洗 (Start)** | Click Start. Disable Wash Options. Change Wash Entry LED to red and display "Wash In Progress". Check vehicle position. | 點選 Start 按鈕。停用所有選單按鈕。門口 LED 變為紅色並顯示 Wash In Progress (洗車中)。開始監控車輛位置是否在第一步驟要求的 Station。 |
| **洗車中 (Washing)** | If vehicle is at correct station, the step LED turns ON and Elapsed Time counts up from zero. If not, turn ON "Vehicle Out of Position" LED and do not begin timing. | 若車輛在該步驟的正確工作站：該步驟 LED 亮起，時間開始累計。若不在正確工作站：點亮 Vehicle Out of Position (車輛偏離) LED 燈，且**暫停計時**。 |
| **偏離定位 (Out of Pos)**| If vehicle moves away during a step, elapsed time pauses, step LED turns OFF, and "Vehicle Out of Position" LED turns ON. Resume timing when restored. | 執行中若車子被拉走（滑桿移開）：時間暫停，步驟 LED 熄滅，Vehicle Out of Position 亮起。當車子拉回正確工作站時，警報 LED 熄滅，繼續累計時間。 |
| **步驟切換 (Next Step)**| Reset Elapsed Time to zero upon step completion. Proceed to next selected step if vehicle is in appropriate station. | 每完成一個步驟，計時器歸零。若車子在下一個步驟對應的工作站，則自動啟動下個步驟的計時。 |
| **洗車結束 (Exit)** | When complete, "Vehicle Out of Position" LED turns ON (prompting exit). Move slider to "Exit" to reset indicators, reset slider to Entry, and change LED to green. | 所有步驟結束後，Vehicle Out of Position 燈亮以提示駛離。當滑桿移到 Exit ➡️ 所有指示器熄滅，滑桿回彈至 Entry，門口 LED 變綠色 (Vacant)，重新啟用選單。 |

---

## ⏱️ 三、洗車步驟、時間與工作站對照表

| 洗車步驟 (Wash Steps) | 步驟時間 (Step Time) | 對應工作站 (Station) |
| :--- | :---: | :--- |
| **Under Body Wash** (底盤清洗) | 5 seconds | **Station 1** (工作站 1) |
| **Bug Remover** (除蟲清洗) | 5 seconds | **Station 1** (工作站 1) |
| **Pre-Soak** (預先浸泡) | 5 seconds | **Station 2** (工作站 2) |
| **High Pressure Wash** (高壓清洗 - 預設) | 5 seconds | **Station 2** (工作站 2) |
| **Low Pressure Wax** (低壓上蠟) | 5 seconds | **Station 2** (工作站 2) |
| **Spot Free Rinse** (無痕沖洗) | 5 seconds | **Station 2** (工作站 2) |
| **Tire Shine Foam** (輪胎拋光泡沫) | 5 seconds | **Station 3** (工作站 3) |
| **Air Dry** (熱風烘乾) | 5 seconds | **Station 3** (工作站 3) |
