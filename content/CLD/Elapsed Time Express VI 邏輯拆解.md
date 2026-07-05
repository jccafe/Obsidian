# 📔 CLD 練習 01：Elapsed Time Express VI 邏輯拆解

> [!abstract] 練習目標 使用 `Elapsed Time Express VI` 實作具備手動與自動重設功能的計時器，這是 CLD 考試中所有「超時處理 (Timeout)」邏輯的基礎。

## 📥 輸入控制 (Inputs)

- [ ] **Time Target (目標時間)**：設定計時器範圍（Double/Numeric）。
    
- [ ] **Reset (手動重設)**：Boolean (Latch)，連線至 Express VI 的 `Reset` 輸入。
    
- [ ] **Auto Reset (自動重設)**：Boolean (Switch)，決定循環邏輯。
    

## ⚙️ 核心邏輯 (Core Logic)

> **使用組件**：`Express -> Execution Control -> Elapsed Time`

### 關鍵機制

當 `Elapsed Time >= Time Target` ➔ `Time Has Elapsed` = **TRUE**。

### Auto Reset 邏輯判定

利用一個 `Select` 函數或 `Case Structure` 來處理 `Reset` 端子的訊號源：

- **ON (自動循環)**：
    
    - 觸發條件：`(Time Has Elapsed AND Auto Reset) OR Manual Reset`
        
    - 結果：時間到即歸零並重啟，燈號閃爍（亮一個 iteration 後熄滅）。
        
- **OFF (單次計時)**：
    
    - 觸發條件：`Manual Reset`
        
    - 結果：時間到後計時器繼續累加，`Time Has Elapsed` 保持恆亮。
        

## 📊 輸出顯示 (Outputs)

- **Elapsed Time (經過時間)**：顯示目前秒數（Indicator）。
    
- **Time Has Elapsed (時間已到)**：亮燈指示（LED）。
    

---

## 💡 CLD 實戰筆記（自我檢討）

- **注意點**：Express VI 是具備「狀態」的（Re-entrant），在同一個 Block Diagram 多次使用時，彼此的計時是獨立的。
    
- **考試陷阱**：若題目要求「精準」計時，Express VI 可能因 CPU 負載產生微小誤差，但在 CLD 基礎題中通常可接受。