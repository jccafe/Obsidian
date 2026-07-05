graph TD
A[開始計時] --> B{Elapsed >= Target?}
B -- No --> A
B -- Yes --> C{Auto Reset?}
C -- Yes --> D[觸發 Reset 端子]
D --> A
C -- No --> E[保持 LED 恆亮]