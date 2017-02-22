---
title: "選項對話方塊、環境、工作清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.Task_List"
  - "VS.ToolsOptionsPag.Environment.Task_List"
  - "VS.ToolsOptionsPages.Environment.TaskList"
  - "VS.Environment.Task List"
helpviewer_keywords: 
  - "語彙基元清單"
  - "語彙基元"
  - "圖示, [工作清單] 中"
  - "工作清單, 自訂環境"
  - "[選項] 對話方塊, [工作清單] 環境"
  - "驚嘆號"
  - "註解, [工作清單] 中的註解工作"
  - "語彙基元, 和 [工作清單]"
  - "工作清單, 註解工作"
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 選項對話方塊、環境、工作清單
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個 \[選項\] 頁面可讓您加入、刪除和變更產生 \[工作清單\] 提醒的註解語彙基元。  若要顯示這些設定，請從 \[工具\] 功能表選取 \[選項\]，然後展開 \[環境\] 資料夾，再選擇 \[工作清單\]。  
  
## 工作清單選項  
 確認刪除工作  
 選取時，每當從 \[工作清單\] 刪除使用者工作時都會顯示訊息方塊，以讓您確認刪除。  預設已選取這個選項。  
  
> [!NOTE]
>  若要刪除工作註解，請使用連結尋找註解，然後從程式碼加以移除。  
  
 只顯示檔名  
 選取時，\[工作清單\] 的 \[檔案\] 欄只會顯示要編輯的檔案名稱，而不會顯示其完整路徑。  
  
## 語彙基元  
 如果您在程式碼中將註解插入以 \[工作清單\] 中語彙基元開頭的文字，則每當開啟要編輯的檔案時，\[工作清單\] 都會將註解顯示為新項目。  您可以按一下這個 \[工作清單\] 項目，直接跳到程式碼中的註解行。  如需詳細資訊，請參閱[使用工作清單](../../ide/using-the-task-list.md)。  
  
 語彙基元清單  
 顯示語彙基元清單，並讓您加入或移除自訂語彙基元。  註解語彙基元在 Visual C\# 和 Visual C\+\+ 中是區分大小寫的，但在 Visual Basic 中則不區分。  
  
> [!NOTE]
>  如果您輸入的語彙基元未與 \[工作清單\] 中所顯示的語彙基元完全符合，註解工作將不會顯示在 \[工作清單\] 中。  
  
 優先順序  
 設定使用所選取語彙基元的工作優先權。  以這個語彙基元開頭的工作註解會在 \[工作清單\] 中自動取得指定的優先權。  
  
 名稱  
 輸入語彙基元字串。  這會啟用 \[加入\] 按鈕。  按下 \[加入\] 時，這個字串會包含在 \[語彙基元清單\] 中，而且以這個名稱開頭的註解將會顯示在 \[工作清單\] 中。  
  
 Add  
 當您輸入新的 \[名稱\] 時就會啟用。  按一下可使用在 \[名稱\] 和 \[優先權\] 欄位中輸入的值，來加入新的語彙基元字串。  
  
 刪除  
 按一下可從 \[語彙基元清單\] 刪除所選取的語彙基元。  您無法刪除預設的註解語彙基元。  
  
 變更  
 按一下可使用在 \[名稱\] 和 \[優先權\] 欄位中輸入的值，來變更現有的語彙基元。  
  
> [!NOTE]
>  您無法重新命名或刪除預設的註解語彙基元，但可以變更其優先權層級。  
  
## 請參閱  
 [使用工作清單](../../ide/using-the-task-list.md)   
 [在程式碼中設定書籤](../../ide/setting-bookmarks-in-code.md)   
 [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)