**使用組件**：`Express -> Execution Control -> Elapsed Time`

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
