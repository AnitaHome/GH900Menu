# **Ch07 GitHub Projects 實戰練習：寵物認養平台 (PetAdopt) 開發案**

本練習參考 Microsoft Learn 課程，旨在引導你從零開始建立、組織並自動化一個 GitHub 專案看板，模擬真實的開發工作流。

## **🏗️ 情境描述**

你是一家新創公司「PetAdopt」的專案經理。公司正在開發「寵物認養平台」的 **社群分享功能**。你需要建立一個 GitHub Project 來管理開發任務、追蹤進度，並確保開發團隊能高效溝通。

## **🚀 步驟一：建立專案與初始設定 (參考單元 3\)**

在這個階段，你將決定專案的結構並連結相關儲存庫。

1. **進入 GitHub Projects**：  
   * 登入 GitHub，點擊右上角頭像，選擇 **Your projects**。  
   * 點擊 **New project**。  
2. **選擇模板**：  
   * 選擇 **Table** 或 **Board**（建議選擇 Board 以利可視化）。  
   * 將專案命名為：PetAdopt: Social Sharing Feature。  
3. **連結儲存庫 (Repository)**：  
   * 在專案設定中，將你的練習儲存庫（例如 pet-adopt-app）連結至此專案，以便直接拉取 Issues。  
4. **建立練習議題 (Issues)**：  
   * 在專案中手動新增以下幾個任務：  
     * 設計社群分享 UI 介面  
     * 整合 Facebook API  
     * 開發 LINE 分享功能  
     * 撰寫測試案例

## **🗂️ 步驟二：組織專案與自定義視圖 (參考單元 4\)**

為了讓團隊能從不同維度看進度，你需要自定義欄位與視圖。

1. **新增自定義欄位**：  
   * 點擊 \+ 號新增欄位。  
   * 建立 **Priority (優先級)**：選項包含 High, Medium, Low。  
   * 建立 **Target Date (目標日期)**：格式為 Date。  
2. **建立多樣視圖**：  
   * **視圖 1 (預設看板)**：命名為 Roadmap，按 Status 分組。  
   * **視圖 2 (高優先級任務)**：  
     * 點擊 \+ 新增一個 Table 視圖。  
     * 命名為 Urgent Tasks。  
     * **設定篩選器 (Filter)**：找到視圖上方中央的搜尋框（標示為 Filter by keyword or field），直接輸入 priority:High。  
     * *提示：點擊框框右側的箭頭也可以透過選單選擇 Priority \-\> High。*  
   * **視圖 3 (進度甘特圖)**：  
     * 新增視圖並選擇 **Roadmap** 類型（需確保有設定 Target Date 欄位）。

## **🤖 步驟三：設定自動化工作流 (參考單元 5\)**

利用 GitHub Projects 內建的自動化功能，減少手動更新看板的時間。

1. **開啟自動化面板**：  
   * 點擊專案右上角的 **Workflows**。  
2. **設定「自動加入專案」 (Auto-add to project)**：  
   * **重要預備動作**：請先回到你的 GitHub **儲存庫 (Repository)**，在 `Issues` \-\> `Labels` 頁面中手動建立一個名為 `social-share` 的標籤。  
   * **設定流程**：  
     * 在 Workflows 選擇 `Auto-add to project`。  
     * 在 `Filters` 框輸入：`is:issue label:social-share`。  
     * 如果出現 **"Invalid value... for label"** 錯誤：這代表標籤尚未在儲存庫中建立。請完成上述預備動作後重試。  
   * 點擊 **Save and turn on workflow**。  
3. **設定「狀態自動變更」 (Item added/reopened)**：  
   * 在 Workflows 側欄找到並點擊 **Item added to project**。  
   * 在右側面板中，確保 **Set value** 已開啟。  
   * **Field** 選擇 `Status`，**Value** 選擇 `Todo`。  
   * 點擊 **Save and turn on**。  
4. **設定「自動關閉/完工更新」 (Item closed)**：  
   * 在 Workflows 側欄找到並點擊 **Item closed**。  
   * 在右側面板中，確保 **Set value** 選項已勾選（或開啟）。  
   * 在 **Field** 下拉選單中選擇 `Status`。  
   * 在 **Value** 下拉選單中選擇 `Done`。  
   * 點擊右上角的 **Save and turn on**。  
   * *註：這樣當你在 Repo 關閉 Issue 時，專案卡片會自動跳到「已完成」欄位，無需手動拖拽。*

## **🛠️ 步驟四：實際操作練習（透過 Issue 觸發自動化）**

現在，請離開專案頁面，回到你的 **GitHub 儲存庫 (Repository)** 進行以下操作，觀察專案看板的自動變化：

### **1\. 觸發「自動加入」與「初始狀態」**

* **動作**：建立一個新的 Issue，標題為 `[功能] 臉書分享按鈕`。  
* **關鍵操作**：在右側 **Labels** 選擇 `social-share`（若無此標籤請先建立）。  
* **預期結果**：回到專案看板，你會發現這張卡片自動出現在 `Todo` 欄位。

  ### **2\. 觸發「開發中」狀態切換**

* **動作**：建立一個新的 Pull Request (PR)。  
* **關鍵操作**：在 PR 的說明欄位（Description）輸入關鍵字 `Fixes #1` (假設編號是 1)。  
* **預期結果**：專案看板上的該 Issue 卡片會自動從 `Todo` 移至 `In Progress`。

  ### **3\. 觸發「自動完工」**

* **動作**：進入該 Issue 頁面，點擊底部的 **Close issue** 按鈕。  
* **預期結果**：專案看板上的卡片會自動跳到 `Done` 欄位。

  ### **4\. 觸發「重新開啟」**

* **動作**：在剛才關閉的 Issue 頁面，點擊 **Reopen issue**。  
* **預期結果**：卡片會自動從 `Done` 跳回 `Todo`（或是你設定的狀態）。


## **🔍 疑難排解：為什麼出現「Invalid value for label」？**

這是新手最常遇到的問題，原因如下：

* **標籤尚未建立**：GitHub Projects 的自動化過濾器會檢查連結的儲存庫。如果該標籤（如 `social-share`）還不存在，系統會判定為無效值。  
* **解決方法**：  
  * 點擊你的儲存庫 `Hello`。  
  * 找到 **Issues** 分頁，點擊右邊的 **Labels**。  
  * 建立一個名為 `social-share` 的新標籤。

## **✅ 練習檢查清單**

完成練習後，請確認你是否達成以下目標：

* \[ \] 成功建立了專案並連結到正確的 Repo。  
* \[ \] 建立了至少 2 個自定義欄位 (Priority, Date)。  
* \[ \] 擁有至少 3 個不同目的的視圖 (Board, Table with Filter, Roadmap)。  
* \[ \] 當 Issue 被關閉時，專案中的卡片會自動跳轉至 Done。

## **💡 進階挑戰**

嘗試邀請一位同學或同事加入你的專案，並在 Issue 中標註 (Assign) 給他，看看他在他的專案視圖中會如何看到這些資訊。
