# **CH10-Lab：從專案孤島到企業協作**

## **1\. 情境設定 (Scenario)**

**公司名稱：** 全球科技解決方案 (Global-Tech Solutions)

**背景：** 公司的「前端開發團隊」開發了一個非常棒的 UI 組件庫 Global-UI。目前這個專案只有該團隊的成員可以查看與修改。由於其他團隊（如後端團隊、行動端團隊）也開始需要這些組件，公司決定將 Global-UI轉型為 **InnerSource** 專案，讓全公司的工程師都能貢獻代碼、修復 Bug 並共同演進這個工具。

**你的角色：** 專案維護者 (Maintainer)，負責建立 InnerSource 的基礎設施。

## **2\. 學習目標**

完成此 Lab 後，你將學會：

1. 建立並優化專案的 **可發現性 (Discoverability)**。  
2. 撰寫清晰的 **貢獻指南 (CONTRIBUTING.md)** 與 **行為準則 (CODE\_OF\_CONDUCT.md)**。  
3. 透過 **Issue/PR 範本** 標準化協作流程。  
4. 設定 **CODEOWNERS** 確保審核品質。

## **3\. 準備工作 (Prerequisites)**

* 一個 GitHub 帳號。

## **4\. 實作步驟 (Lab Steps)**

### **任務一：提升專案的可發現性 (Discoverability)**

InnerSource 的核心 is 「透明」。如果別人找不到你的專案，就無法貢獻。首先，我們必須建立實作的基礎環境。

1. **建立專案儲存庫 (Create Repository)**：  
   * 在 GitHub 首頁點擊 **New** 建立新的儲存庫。  
   * **Repository name**: inner-source-lab (或 global-ui)。  
   * **Description**: Global-Tech Solutions 內部的通用 UI 組件庫，實踐 InnerSource 的範例專案。  
   * **Choose visibility (重要)**：  
     * 如果你是使用**個人帳號**練習，請選擇 Public（公開）。  
     * *註：在企業環境中，通常會選擇 Internal（內部），這僅限企業成員可見，但個人版不會出現此選項。*  
   * 勾選 **Add a README file**。  
   * 點擊 **Create repository**。  
2. **優化 README.md**：  
   * 點擊 README.md 的編輯按鈕 (鉛筆圖示)。  
   * **內容參考範例**： (完成後按下 Commit changes...)
  ```
     # Global-UI 組件庫

     ## 🚀 專案簡介  
     Global-UI 是 Global-Tech Solutions 的官方 UI 框架，旨在統一公司內所有產品的視覺風格與交互經驗，減少重複開發。

     ## 🛠 快速上手  
     1. 安裝套件：`npm install global-ui`  
     2. 啟動開發伺服器：`npm start`

     ## 🤝 InnerSource 聲明  
     本專案是 Global-Tech 的 **InnerSource 專案**。我們相信集體智慧！不論你是哪個部門的成員，只要你有好想法、發現 Bug 或想優化組件，我們都熱烈歡迎你提交 Pull Request 參與貢獻。
```
3. **新增專案標籤 (Topics)**：  
   * 在 GitHub 儲存庫首頁右側的 "About" 區塊點擊齒輪圖示。  
   * 在 Topics 欄位分別輸入 innersource, ui-library, internal-tools (每輸入一個字詞後按 Enter)，完成後點擊 Save 儲存。這能幫助其他同仁透過關鍵字搜尋到此專案。

### **任務二：建立協作標準 (Contribution Standards)**

為了讓外部團隊知道「如何」參與，你需要建立明確的文件。

1. **建立 CONTRIBUTING.md**：  
   * 在根目錄建立 CONTRIBUTING.md，並貼入以下內容：
     ``` 
     ## 如何貢獻  
     1. 尋找現有的 Issue 或建立新 Issue 討論你的想法。  
     2. Fork 本專案並建立功能分支。  
     3. 確保你的程式碼通過所有 Lint 檢查。  
     4. 提交 PR 並等待維護者審核。

   * **定義內容**：  
     * 如何報告 Bug。  
     * 如何提交新功能需求。  
     * 代碼風格 (Linting) 要求。  
     * 測試要求 (必須通過所有單元測試)。
  ```
2. **建立 CODE\_OF\_CONDUCT.md**：  
   * 在 GitHub 點擊 Add file \-\> Create new file。  
   * 輸入檔案名 CODE\_OF\_CONDUCT.md。  
   * 點擊 Choose a Code of Conduct template 按鈕，選擇 **Contributor Covenant** 並填寫你的聯絡 Email。

### **任務三：流程自動化與標準化 (Templates)**

使用範本可以大幅減少溝通成本，確保資訊完整。

1. **Issue 範本**：  
   * 進入儲存庫的 Settings \-\> General。  
   * 捲動到 Features 區塊，找到 Issues，點擊 Set up templates。  
   * 建立一個 "Bug report" 範本。  
2. **Pull Request 範本**：  
   * 點擊 **Add file** \-\> **Create new file**，在檔名欄位輸入 .github/ 接著輸入 PULL\_REQUEST\_TEMPLATE.md (輸入斜線會自動轉換為資料夾)。  
   * 在該檔案內建立 PULL\_REQUEST\_TEMPLATE.md。  
   * **加入以下 Checklist**：  
     - [ ] 我已經閱讀了 CONTRIBUTING 指南。  
     - [ ] 我的代碼符合公司的 Lint 規範。  
     - [ ] 我已經手動測試過此功能。  
     - [ ] 相關的 Issue 編號：\#

### **任務四：治理與產權管理 (Governance)**

誰該對代碼負責？使用 CODEOWNERS 自動分派審核者。

1. **建立 CODEOWNERS 檔案**：  
   * 在 .github/ 資料夾下建立 CODEOWNERS。  
   * **內容參考範例**： (請將 @your-username 替換為你的 GitHub ID 後 Commit)
```
     # 這是一個註解：將所有 JS 檔案交由你（前端負責人）審核  
     *.js @your-username

     # 將所有文件夾 docs 下的內容交由你審核  
     docs @your-username
```
   * **設定規則解釋**：  
     * 將所有 JavaScript 檔案的審核權交給前端團隊。CODEOWNERS 規則會在 Pull Request 發起時自動指派審核者，這在 InnerSource 中是確保「治理」與代碼品質的重要機制。  
     * 範例：\*.js @your-username (請填寫你的 GitHub 使用者帳號)。

## **5\. 模擬實戰測試 (The Final Test)**

請嘗試以一個「貢獻者」的角度模擬以下行為：

1. **Fork** 這個專案。  
   *註：GitHub 不允許自己 Fork 自己的專案。如果是自己練習，可以請朋友 Fork，或自己建立一個測試用帳號來操作。此外，Fork 是 InnerSource 跨團隊協作最常見的模式，允許貢獻者在獨立空間進行開發後再回饋給主專案。*  
2. 建立一個新分支 feature/new-button。  
3. 修改 README.md（模擬代碼改動）。  
4. **提交並發起一個 Pull Request**：  
   * 進入你的 Fork 儲存庫頁面，點擊上方出現的綠色按鈕 **Compare & pull request**。  
   * 檢查頁面上方的對比設定：base repository 應為原專案，head repository 應為你的 Fork 分支。  
   * 填寫 PR 標題（例如：docs: 增加按鈕組件說明）。  
   * **關鍵觀察**：確認描述欄位中是否已自動填入你在任務三建立的 **Pull Request 範本**。  
   * 完成範本中的 Checklist，最後點擊 **Create pull request**。  
5. **觀察結果**：  
   * 是否自動跳出了你設定的 PR 範本內容？  
   * 在 PR 右側的 **Reviewers** 區塊中，是否看到系統根據 CODEOWNERS 自動指派了審核者？

## **6\. 結業檢查清單**

* README.md 是否有 InnerSource 歡迎標語？  
* 是否有 CONTRIBUTING.md 引導他人提交代碼？  
* 是否有 CODE\_OF\_CONDUCT.md 維護社群氛圍？  
* 是否透過 .github/ 資料夾管理 Issue/PR 範本與 CODEOWNERS？

**恭喜！你已經成功建立了一個具備 InnerSource 基礎設施的專案。這不僅僅是技術設定，更是一種開放協作文化的開始。**

