---
title: "CLD 17 個單元詳細規格與中英對照總整理"
created: 2026-06-18 20:45:18
tags:
  - LabVIEW
  - CLD
  - 認證考試
  - 筆記整理
  - 中英對照
---

# CLD 17 個單元詳細規格與中英對照總整理

本篇筆記詳細整理了 **NI Certified LabVIEW Developer (CLD) 成功練習套件** 之中所有 17 個練習單元的目標、初始化設定、運作邏輯及後續思考問題，並提供完整的中英對照，作為 CLD 認證考試複習的隨身手冊。

---

## 🧭 快速目錄導覽 (WikiLinks)
* [[#CLD 1 Elapsed Time Express VI Timer (經過時間 Express VI 計時器)]]
* [[#CLD 2 Elapsed Time FGV (經過時間功能性全域變數)]]
* [[#CLD 3 Action Engine Timer (動作引擎計時器)]]
* [[#CLD 4 Event Structure Time Out (事件結構超時處理)]]
* [[#CLD 5 Reading/Writing Config File (讀寫設定檔資料)]]
* [[#CLD 6 Comma Separated File Utility (CSV 檔案工具)]]
* [[#CLD 7 Date Stamp Parsing (日期戳記解析)]]
* [[#CLD 8 CSV File Commands Utility (CSV 指令工具)]]
* [[#CLD 9 Step Sequencer with Express Timer (搭配 Express 計時器的步驟順序器)]]
* [[#CLD 10 Step Sequencer Based on CSV Data (基於 CSV 資料的步驟順序器)]]
* [[#CLD 11 Producer Consumer Step Sequencer (生產者/消費者步驟順序器)]]
* [[#CLD 12 Sequencer State Machine (順序器狀態機)]]
* [[#CLD 13 Flow Rates (流量計算與累積)]]
* [[#CLD 14 Timer Application With File Time Targets (具檔案時間目標的計時器應用)]]
* [[#CLD 15 CSV File Text String Parsing (CSV 檔案文字字串解析)]]
* [[#CLD 16 State Machine with Enables and Disables (帶有啟用與停用控制的狀態機)]]
* [[#CLD 17 GUI Keypad Simulation (圖形化鍵盤模擬)]]

---

## CLD 1: Elapsed Time Express VI Timer (經過時間 Express VI 計時器)

### 🎯 目標 (Objective)
* **EN**: Develop a simple timer application using the Elapsed Time Express VI and the given application front panel.
* **ZH**: 使用經過時間 Express VI 與給定的人機介面開發一個簡單的計時器應用程式。

### ⚙️ 初始化狀態 (Initialization)
* **Time Target (目標時間)**: 2 seconds
* **Auto Reset (自動重設)**: ON
* **Reset (重設)**: OFF
* **Time Has Elapsed (時間已到 LED)**: OFF
* **Elapsed Time (經過時間指示器)**: 0

### 🔄 運作邏輯 (Operation)
* **EN**: The application must count up from zero to the Time Target. When elapsed time has expired, the Time Has Elapsed LED turns ON.
* **ZH**: 應用程式必須從零開始累計至目標時間。當計時時間屆滿時，「時間已到」LED 燈必須亮起。
* **EN**: If Auto Reset is ON: The timer immediately begins a new timing cycle on expiration. If Auto Reset is OFF: The timer continues to count elapsed time and keeps the Time Has Elapsed indicator ON.
* **ZH**: 若「自動重設」為 ON：當時間到時，計時器會立刻重設為零並重新開始計時。若「自動重設」為 OFF：計時器會繼續累計時間，並保持「時間已到」指示燈為亮起狀態。
* **EN**: When the Reset button is pressed, the timer must start timing at zero.
* **ZH**: 按下「重設」按鈕時，計時器必須立刻清零並從零開始重新計時。

### ❓ 思考問題 (Questions)
1. **EN**: For what types of timing is the Elapsed Time Express VI well suited?
   **ZH**: 經過時間 Express VI 最適合用於哪種類型的計時？
2. **EN**: What are the consequences of this Elapsed Time Express VI being re-entrant?
   **ZH**: 此經過時間 Express VI 被設定為重入 (Re-entrant) 的後果是什麼？

---

## CLD 2: Elapsed Time FGV (經過時間功能性全域變數)

### 🎯 目標 (Objective)
* **EN**: Develop a simple Functional Global Variable (FGV) Timer based on the express VI. Use the provided Enum with three states: Reset, Set Auto Reset, and Read Status.
* **ZH**: 基於 Express VI 開發一個簡單的功能性全域變數 (FGV) 計時器。使用提供的三個狀態列舉：Reset、Set Auto Reset 與 Read Status。

### ⚙️ 初始化狀態 (Initialization)
* **Time Target**: 4 seconds | **Auto Reset**: ON | **Time Has Elapsed**: OFF | **Timer Mode**: Reset

### 🔄 運作邏輯 (Operation)
* **EN**: Reset Mode: Saves Time Target to the FGV, resets the timer, and sets Auto Reset to FALSE.
* **ZH**: Reset 模式：將目標時間儲存至 FGV、重設計時器，並將自動重設初始化為 FALSE。
* **EN**: Read Status Mode: Continuously reads the status. If Auto Reset is ON, the timer restarts on expiration. If Auto Reset is OFF, it continues counting up.
* **ZH**: Read Status 模式：持續讀取狀態。若自動重設為 ON，時間到時重啟新計時週期；若為 OFF，時間到後繼續累計。
* **EN**: Set Auto Reset Mode: Passes the Auto Reset control value to the FGV shift register.
* **ZH**: Set Auto Reset 模式：將人機介面的自動重設值傳入並儲存於 FGV 的位移暫存器 (Shift Register) 中。

### ➕ 挑戰練習 (Challenge Exercise)
* **EN**: Develop a simple timer application that can pause timing. Upon releasing the Pause, the timer must continue from the point of the previous elapsed time.
* **ZH**: 開發一個支援暫停功能的計時器。當釋放暫停時，計時器必須從先前暫停的時間點繼續累計。

---

## CLD 3: Action Engine Timer (動作引擎計時器)

### 🎯 目標 (Objective)
* **EN**: Develop a Functional Global Variable (FGV) timer using LabVIEW timing VIs (e.g., 'Get Date/Time in Seconds' or 'Tick Count (ms)').
* **ZH**: 使用底層時間 VI（例如「取得秒計日期/時間」或「計數器滴答值」）開發一個功能性全域變數 (FGV) / 動作引擎 (Action Engine) 計時器。

### 🔄 運作邏輯 (Operation)
* **EN**: Timer Mode Enum has four values:
  1. **Start Timer**: Initiates timing using the Time Target.
  2. **Read Time**: Calculates current Elapsed Time and Has Time Elapsed status.
  3. **Pause**: Pauses timing, maintaining the current state and stops incrementing.
  4. **Resume**: Resumes timing starting from the point of the previous elapsed time.
* **ZH**: 計時器模式列舉包含四個值：
  1. **Start Timer**：使用目標時間初始化並啟動計時。
  2. **Read Time**：計算並輸出當前的經過時間與時間是否已到狀態。
  3. **Pause**：暫停計時，鎖定當前時間且時間不再累加。
  4. **Resume**：恢復計時，從先前暫停的時間點繼續向後累計。

### ❓ 思考問題 (Questions)
1. **EN**: What is a method that can resolve the bit timer “turnover” (overflow) event?
   **ZH**: 有什麼方法可以解決計時器溢位（Turnover/Overflow）問題？
2. **EN**: Does the day and year matter when using a time stamp?
   **ZH**: 使用時間戳記時，日期和年份會有影響嗎？

---

## CLD 4: Event Structure Time Out (事件結構超時處理)

### 🎯 目標 (Objective)
* **EN**: Develop a simple state machine with an event structure. The application maintains an unsigned count. If there is inactivity on the front panel longer than the Time Target, the count resets to zero and Time Has Elapsed turns ON.
* **ZH**: 開發一個以事件結構為核心的簡單狀態機。程式維護一個無符號計數值，若人機介面閒置時間超過目標時間，則將計數歸零，並點亮「時間已到」指示燈。

### 🔄 運作邏輯 (Operation)
* **EN**: UI activity (pressing Increment/Decrement) resets the timeout period. When decrementing below zero, the count rolls over to the highest integer value.
* **ZH**: 任何 UI 活動（如按增/減按鈕）都會重新重設計時週期。當減到小於 0 時，無符號計數值會溢位 (Roll-over) 至最大值並繼續遞減。

### ➕ 挑戰練習 (Challenge Exercise)
* **EN**: Develop an Event Structure Timer and 4-Bit Binary Counter. The Time Target is divided into 16 steps, and 4 LEDs represent the binary count.
* **ZH**: 開發一個事件結構計時器與 4 位元二進位計數器。將目標時間均分為 16 等分，以 4 顆 LED 燈顯示二進位步驟計數（例如目標 4 秒，每 0.25 秒二進位加 1，從 `0000` 到 `1111`）。

---

## CLD 5: Reading/Writing Config File (讀寫設定檔資料)

### 🎯 目標 (Objective)
* **EN**: Develop a VI that reads and writes configuration file (.ini) data to and from a UI data structure (2x4 cluster array).
* **ZH**: 開發一個能夠在人機介面資料結構（一個 2 列 4 行的叢集陣列）與本地配置檔案 (`.ini`) 之間讀寫資料的 VI。

### 🔄 運作邏輯 (Operation)
* **EN**: Get action reads the file and populates the array based on row/column indices (Index1 and Index2). Set action writes the positions and cluster data (Numeric, Boolean, String) into the file.
* **ZH**: Get 動作：讀取設定檔並依據行列索引（Index1 與 Index2）將資料填入人機介面陣列。Set 動作：讀取輸入陣列，並將陣列索引值及叢集內的三個欄位（數值、布林、字串）寫入設定檔。

### ❓ 思考問題 (Questions)
1. **EN**: What are the complications from using zero-based indexing?
   **ZH**: 使用以零為起始 (Zero-based) 的索引會帶來什麼複雜性？
2. **EN**: How important is the data type to the Configuration File VIs?
   **ZH**: 資料類型對於配置檔案讀寫 VI 的重要性有多高？

---

## CLD 6: Comma Separated File Utility (CSV 檔案工具)

### 🎯 目標 (Objective)
* **EN**: Develop a VI that reads and writes comma separated variable (.csv) data to and from a UI cluster array.
* **ZH**: 開發一個能在人機介面的叢集陣列與本地逗號分隔檔案 (`.csv`) 之間讀寫資料的工具。

### 🔄 運作邏輯 (Operation)
* **EN**: Read (Set) parses CSV rows sequentially into the cluster array. Write (Get) takes the array elements and writes them sequentially as rows of CSV data.
* **ZH**: Read 動作：讀取 CSV 檔案並按順序將各列資料轉換為叢集放入陣列。Write 動作：讀取輸入陣列並將每個叢集依序寫入為 CSV 檔案的各列。

---

## CLD 7: Date Stamp Parsing (日期戳記解析)

### 🎯 目標 (Objective)
* **EN**: Reformat a timestamp into a coded space-separated string of 12 values starting with `0` and ending with `lvinit`.
* **ZH**: 將輸入的時間戳記轉換並重新格式化為由空白分隔的 12 個特製編碼欄位，且必須以 `0` 開頭、以 `lvinit` 結尾。

### 📊 編碼格式規範 (Data Formats)
1. 開頭為 `0`
2. 百分之一秒 (0-99)
3. 秒 (0-59)
4. 分 (0-59)
5. 時（12小時制, 1-12）
6. 日期 (1-31)
7. 星期幾（0-6，0 代表星期日）
8. 月份 (1-12)
9. 年份（世紀內年份, 0-99）
10. 世紀（0 代表 2000年代，1 代表 1900年代或 2100年代）
11. AM/PM 模式（0=AM, 1=PM）
12. 結尾字串 `lvinit`

*例如：“01:04:13 PM Friday, April 12, 2013” 轉換後為 `0 0 13 04 01 12 5 4 13 0 1 lvinit`。*

---

## CLD 8: CSV File Commands Utility (CSV 指令工具)

### 🎯 目標 (Objective)
* **EN**: Develop a VI that reads a CSV file containing: Command (string), Time (numeric), and three Boolean values, and places them into an array of clusters.
* **ZH**: 開發一個讀取 CSV 指令檔的工具。將每行包含的：指令（字串）、時間（數值）以及三個布林值，解析並依序存入一個叢集陣列中。此工具將於後續的步驟順序器練習中被呼叫。

---

## CLD 9: Step Sequencer with Express Timer (搭配 Express 計時器的步驟順序器)

### 🎯 目標 (Objective)
* **EN**: Develop a step sequencer that sequences 3 steps with predefined times (5s, 4s, 3s) using the Elapsed Time Express VI.
* **ZH**: 使用經過時間 Express VI 開發一個步驟順序器，依序執行三個預設時間（5秒、4秒、3秒）的步驟，並點亮對應步驟的 LED 燈。

### 🔄 運作邏輯 (Operation)
* **EN**: If Time Target control is positive, it overrides the predefined step times.
* **ZH**: 若人機介面的「目標時間」控制元件為正數，則會覆蓋預設的步驟時間，改用該數值進行計時。
* **EN**: Advances to next step only if Auto Reset is ON and time has elapsed. If Auto Reset is OFF, it pauses at current step and keeps counting.
* **ZH**: 只有在「自動重設」為 ON 且時間屆滿時，順序器才會跳至下一步並重設計時。若為 OFF，時間屆滿時會留在原步驟、保持時間已到燈亮，且計時器持續累計。

---

## CLD 10: Step Sequencer Based on CSV Data (基於 CSV 資料的步驟順序器)

### 🎯 目標 (Objective)
* **EN**: Modify CLD 9 to load the step times and LED Boolean states dynamically from a CSV file (using CLD 6 utility), replacing hard-coded values.
* **ZH**: 修改 CLD 9 順序器，將原本寫死的步驟時間與 LED 狀態，改為使用 CSV 檔案工具動態從 `CLD 10 CSV File.csv` 中載入。

---

## CLD 11: Producer Consumer Step Sequencer (生產者/消費者步驟順序器)

### 🎯 目標 (Objective)
* **EN**: Implement the step sequencer of CLD 10 using the Producer/Consumer design pattern.
* **ZH**: 採用 **生產者/消費者 (Producer/Consumer)** 設計模式重構 CLD 10 的步驟順序器。此模式是 CLD 考試中用於隔離 UI 事件與背景定時處理的核心架構。

---

## CLD 12: Sequencer State Machine (順序器狀態機)

### 🎯 目標 (Objective)
* **EN**: Develop a state machine to sequence steps based on commands loaded from a file (SetTime, RunState1, RunState2).
* **ZH**: 開發一個狀態機，依據從檔案讀取的指令序列（例如 SetTime、RunState1、RunState2）來執行狀態的轉移。

### 🔄 運作邏輯 (Operation)
* **EN**: SetTime command sets the timer target. RunState commands display Boolean states on Switch LEDs and run until the timer expires, then advance to next step.
* **ZH**: SetTime 指令：設定計時器目標並重新啟動計時。RunState 指令：將對應的布林狀態輸出至 Switch LED，並持續保持此狀態直到計時結束，隨後進到下一指令。若無 SetTime 指令，計時目標預設為 0。

---

## CLD 13: Flow Rates (流量計算與累積)

### 🎯 目標 (Objective)
* **EN**: Develop a state machine that simulates flow rates (+/- 20 limit) and flow rate change.
* **ZH**: 開發一個狀態機，用於模擬流量變動與當前流量（限制在 +/-20 範圍內）。

### 🔄 運作邏輯 (Operation)
* **EN**: Calculate flow rate every 0.25 seconds based on Flow Rate Change control. Elapsed Time counts up when flow is non-zero.
* **ZH**: 每 0.25 秒依據「流量變動」滑桿計算並更新一次流量。當流量不為零時，經過時間持續累計。
* **EN**: Elapsed Time resets to zero when flow reaches zero, or when flow direction changes (crosses zero). Stop Flow decreases/increases flow rate by step of 1 towards zero.
* **ZH**: 當流量變為零、或流量方向改變（穿過零點）時，「經過時間」必須歸零。按下「停止流量」時，流量會以每步 +/-1 的速度逐步遞減至零。

---

## CLD 14: Timer Application With File Time Targets (具檔案時間目標的計時器應用)

### 🎯 目標 (Objective)
* **EN**: Develop a state machine that loads time targets from a CSV file, runs a timer for each step, and supports pause/resume and cancel.
* **ZH**: 開發一個狀態機，讀取 CSV 檔案中的時間序列，對每個單元執行計時，並提供暫停/恢復以及取消當前步驟的功能。

### 🔄 運作邏輯 (Operation)
* **EN**: Pause freezes the elapsed time. Cancel button immediately stops the current timing step and advances to the next step (even if paused).
* **ZH**: 暫停：凍結目前經過的時間。取消：立刻結束當前步驟並前進到下一個步驟（即使在暫停狀態下按取消，也必須立刻解除暫停並跳至下一步驟）。

---

## CLD 15: CSV File Text String Parsing (CSV 檔案文字字串解析)

### 🎯 目標 (Objective)
* **EN**: Parse a CSV file with customer order strings (e.g. `091,TX78701Travis+02`), calculate total tubes, reformat addresses, and output to a new CSV file.
* **ZH**: 讀取包含客戶訂單代碼的 CSV 檔案（例如 `091,TX78701Travis+02`），解析數量與地址，計算價格加成，並將結果輸出為新的 CSV 格式。

### 📊 資料解析規則 (Parsing Rules)
* **前三碼數量 (Quantity)**：例如 `091` 代表 9 支管子與 1 箱（一箱 = 50 支，總計 59 支）。
* **後方地址與價格加成 (Customer)**：例如 `TX78701Travis+02` 代表 州名為 `TX`、郵區為 `78701`、郡縣為 `Travis`、價格調整為 `+2%` (乘數為 1.02)。
* **大額訂單判定**：總價（單價 $10 × 總支數 × 價格乘數）若大於 **$1000**，則大額訂單標記為 `TRUE`。

---

## CLD 16: State Machine with Enables and Disables (帶有啟用與停用控制的狀態機)

### 🎯 目標 (Objective)
* **EN**: Simulate peanut hoppers with UI requirements to enable/disable buttons based on hopper weight knob values (0-10).
* **ZH**: 模擬花生加工漏斗。依據漏斗重量旋鈕（0 到 10 噸）的數值，動態啟用或停用 Fill（加料）或 Use（出料）按鈕。

### 🔄 運作邏輯 (Operation)
* **EN**: If weight is 0: Disable "Use Peanuts". If weight is 10: Disable "Fill Peanuts". Else: Enable both.
* **ZH**: 重量為 0 時：停用 Use Peanuts。重量為 10 時：停用 Fill Peanuts。重量在 1 至 9 時：同時啟用兩者。
* **EN**: Pressing Use Peanuts generates a random Process Value (0 to 1) and compares it against limits (0.25 and 0.75). The button is disabled for 250 ms during processing.
* **ZH**: 按下 Use Peanuts 時：按鈕會先被停用 250 ms（模擬處理時間）。隨機產生 0 到 1 的品質數值，與上限 0.75 及下限 0.25 比較，輸出是否超限，且重量減 1。

---

## CLD 17: GUI Keypad Simulation (圖形化鍵盤模擬)

### 🎯 目標 (Objective)
* **EN**: Develop a VI that simulates a GUI keypad (0-9, C, E) and displays the input string, converting to numeric on Enter ('E').
* **ZH**: 開發一個虛擬鍵盤 (0-9、清除 C、確認 E) 的模擬程式。將按下的按鍵累加顯示為字串，按下 E 時轉換為數值輸出，按下 C 時清零。

### 🔄 運作邏輯 (Operation)
* **EN**: Loop runs continuously until 'E' is pressed. Keypad inputs append to the string indicator. Pressing 'C' clears string to "0".
* **ZH**: 程式持續循環直到按下 E 為止。按鍵輸入會向字串後方追加。按下 C 時清除為 "0"。

