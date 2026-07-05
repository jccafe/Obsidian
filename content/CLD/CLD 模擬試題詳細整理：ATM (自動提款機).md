---
title: "CLD 模擬試題詳細整理：ATM (自動提款機)"
created: 2026-06-18 20:52:34
tags:
  - LabVIEW
  - CLD
  - 模擬試題
  - 中英對照
  - ATM
---

# CLD 模擬試題詳細整理：ATM (自動提款機)

本篇筆記針對模擬試題 `ATM (100928C-01).pdf` 之規格書進行詳細的系統化中英對照與邏輯拆解。

---

## 🎯 一、設計目標 (Objective)

| 英文規格 (English) | 中文對照 (Chinese) |
| :--- | :--- |
| Design an Automated Teller Machine (ATM) controller using LabVIEW. | 使用 LabVIEW 設計一個自動提款機 (ATM) 控制器。 |
| The ATM controller simulates the control system of an Automated Teller Machine. | 此 ATM 控制器用來模擬自動提款機的控制系統。 |
| The user performs common ATM functions such as deposit funds, withdraw funds, and inquire about the balance. | 使用者可執行常見的 ATM 功能，如存款、提款以及查詢餘額。 |

---

## 📂 二、帳戶檔案格式 (ATM Accounts File Specification)

* **檔案名稱**：`Accounts.txt` (CSV 格式，須與主 VI 放在同一目錄下)。
* **資料欄位**：`Account Number (5 digits), First Name, Last Name, Balance`（帳號(5位數), 名字, 姓氏, 餘額）。
* **測試帳戶資料**：
  * `12345,John,Doe,550`
  * `23456,Jennifer,Rodriguez,1000`
  * `34567,Bryan,Smith,750`
  * `45678,Julie,Ramirez,900`

---

## 🔄 三、運作順序要求 (Sequence of Operation)

| 階段 (Stage) | 英文規範 (English) | 中文規範 (Chinese) |
| :--- | :--- | :--- |
| **啟動 (Start)** | When the application starts, User Input, Enter (E), Menus, and Menu Buttons should be disabled. The Card Simulator should be enabled and display the Welcome Message. | 當程式啟動時，使用者輸入、Enter (E) 鍵、選單以及按鈕皆須停用。僅「插卡模擬器」為啟用狀態，且訊息欄顯示 Welcome Message (歡迎訊息)。 |
| **插卡 (Insert Card)** | Click the Card Simulator button. This action enables the Enter (E) button and User Input control, focuses the cursor, and waits for the account number. | 點選 Card Simulator 按鈕。此動作會啟用 Enter (E) 鍵與使用者輸入框，並將游標聚焦於輸入框，等待輸入帳號。 |
| **閒置超時 (Timeout)** | If the ATM controller does not detect use of front panel controls for 10 seconds, the card should be released and the session terminated by stopping the application. | 插卡後，若系統偵測到 10 秒內沒有任何 UI 操作，必須釋放插卡按鈕退卡，顯示 Session Terminate 訊息，並結束程式。 |
| **帳號驗證 (Verify)** | Access the ATM Accounts file to verify the account. If it doesn't exist, display Account Verification Failed Message and prompt retry. If it exists, enable menus and display Main Menu. | 讀取 Accounts.txt 驗證帳號。若帳號不存在，顯示驗證失敗訊息並提示重新輸入；若驗證成功，則啟用所有選單按鈕，並顯示主選單與客戶姓名。 |
| **存款 (Deposit)** | Click Deposit button. Display Deposit Message. Allow user to enter amount and press Enter (E). Update the accounts file and display Deposit Complete. | 點選 Deposit 按鈕。顯示存款提示。引導使用者輸入金額並按 Enter (E)。更新檔案中的帳戶餘額，並顯示 Deposit Complete 訊息。 |
| **提款 (Withdraw)** | Click Withdraw. Display Withdrawal Message. Check if the account has sufficient funds. If yes, deduct amount, update file, and display Withdrawal Complete. If no, display Withdrawal Failed. | 點選 Withdraw 按鈕。顯示提款提示並輸入金額。比對餘額是否足夠：若足夠則扣款、更新檔案並顯示 Withdrawal Complete ；若不足則顯示 Withdrawal Failed。 |
| **快速提款 (Fast Cash)**| Click Fast Cash $50. Deduct $50 if funds are sufficient, update file, and display Withdrawal Complete. Otherwise, display Withdrawal Failed. | 點選 Fast Cash $50。若餘額大於等於 $50 則直接扣除 $50、更新檔案並顯示提款成功；否則顯示提款失敗。 |
| **餘額查詢 (Balance)** | Click Balance Inquiry to get the current balance from the file, and display the Balance Inquiry Message. | 點選 Balance Inquiry，從帳戶檔案讀取目前餘額並在畫面中顯示。 |
| **退卡結束 (Return)** | Click Return Card and Terminate. Release the Card Simulator button, disable User Input, and terminate the application. | 點選 Return Card and Terminate。退卡（釋放 Card Simulator 按鈕）、停用輸入框，並終止程式。 |

---

## 💬 四、訊息類型與格式化 (ATM Message Types)

顯示於 **ATM Messages** 指示器，文字設定必須為 **14 point 且 Bold (粗體)**，內容必須**居中對齊 (Centered)**。

* **歡迎訊息 (Welcome Message)**：
  ```text
  Welcome to Acme Bank.
  Please insert your card
  and enter your account
  number in the User Input.
  Press Enter (E) when done.
  ```
* **主選單訊息 (Main Menu Message)**：
  ```text
  Welcome to Acme Bank
  [First Name], [Last Name]
  Please select transaction
  by using the buttons.
  ```
* **驗證失敗 (Account Verification Failed)**：
  ```text
  Account Information Incorrect
  Please Re-Enter Account Number.
  Press Enter (E) when done.
  ```
* **工作超時/退卡 (Session Terminate)**：
  ```text
  Your session has been terminated
  due to inactivity or menu selection.
  Please take your card
  Goodbye!
  ```
