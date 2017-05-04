---
title: "逐步解說：建立自訂站台工作流程活動 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "自訂工作流程活動 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 自訂工作流程活動"
  - "Visual Studio 中的 SharePoint 開發, 網站工作流程"
  - "網站工作流程 [Visual Studio 中的 SharePoint 程式開發]"
  - "工作流程活動 [Visual Studio 中的 SharePoint 程式開發]"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 逐步解說：建立自訂站台工作流程活動
  本逐步解說示範如何使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為網站層級工作流程建立自訂活動 \(網站層級工作流程適用於整個網站，而不只是網站上的清單\)。此自訂活動會建立備份「公告」清單，然後將「公告」清單的內容複製到該清單。  
  
 本逐步解說將示範下列工作：  
  
-   建立網站層級工作流程。  
  
-   建立自訂工作流程活動。  
  
-   建立和刪除 SharePoint 清單。  
  
-   將項目從一個清單複製到另一個清單。  
  
-   在快速啟動列上顯示清單。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 建立網站工作流程自訂活動專案  
 首先，建立專案來存放和測試自訂工作流程活動。  
  
#### 若要建立網站工作流程自訂活動專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  在 \[**範本**\] 窗格中，選取 \[**SharePoint 2010 專案**\] 範本。  
  
4.  在 \[**名稱**\] 文字方塊中，輸入 AnnouncementBackup，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
5.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕，以接受信任層級和預設網頁。  
  
     此步驟會將方案的信任層級設定為陣列方案，這是工作流程專案唯一可用的選項。  
  
6.  在 \[**方案總管**\] 中，選擇專案節點，然後在功能表列上選擇 \[**專案**\]、\[**加入新項目**\]。  
  
7.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
8.  在 \[**範本**\] 窗格中，選取 \[**循序工作流程 \(僅限陣列方案\)**\] 範本，然後選擇 \[**加入**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
9. 在 \[**指定工作流程名稱進行偵錯**\] 頁面中，接受預設名稱 \(AnnouncementBackup \- Workflow1\)。  將工作流程範本類型變更為 \[**網站工作流程**\]，然後選擇 \[**下一步**\] 按鈕。  
  
10. 選擇 \[**完成**\] 按鈕，接受其餘的預設設定。  
  
## 加入自訂工作流程活動類別  
 接下來，將類別加入至專案，以包含自訂工作流程活動的程式碼。  
  
#### 若要加入自訂工作流程活動類別  
  
1.  在功能列表上選擇 \[**專案**\]、\[**加入新項目**\]，顯示 \[**加入新項目**\] 對話方塊。  
  
2.  在 \[**已安裝的範本**\] 樹狀檢視中，選擇\[**程式碼**\] 節點，然後選擇專案項目範本清單中的 \[**類別**\] 範本。  請使用預設名稱 Class1。  選擇 \[**加入**\] 按鈕。  
  
3.  將 Class1 中的所有程式碼取代成下列程式碼：  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  儲存專案，然後在功能表上選擇 \[**建置**\]、\[**建置方案**\]。  
  
     Class1 會顯示為 \[**工具箱**\] 的自訂動作 \(在 \[**AnnouncementBackup 元件**\] 索引標籤上\)。  
  
## 將自訂活動加入至網站工作流程  
 接下來，將活動加入至工作流程，以包含自訂程式碼。  
  
#### 若要將自訂活動加入至網站工作流程  
  
1.  在工作流程設計工具的設計檢視中開啟 Workflow1。  
  
2.  從 \[**工具箱**\] 拖曳 Class1，使它顯示在 `onWorkflowActivated1` 活動下，或開啟 Class1 的捷徑功能表，選擇 \[**複製**\]，開啟在 `onWorkflowActivated1` 活動下一行的捷徑功能表，然後選取 \[**貼上**\]。  
  
3.  儲存專案。  
  
## 測試網站工作流程的自訂活動  
 接下來，執行專案並啟動網站工作流程。  此自訂活動會建立備份「公告」清單，然後將目前「公告」清單的內容複製到該清單。  程式碼也會在建立備份清單之前檢查它是否已存在。  如果備份清單已存在，則會被刪除。  程式碼也會將新清單的連結加入至 SharePoint 網站的快速啟動列。  
  
#### 若要測試網站工作流程的自訂活動  
  
1.  按 F5 鍵執行專案並將它部署至 SharePoint。  
  
2.  在快速啟動列上，選擇 \[**清單**\] 以顯示 SharePoint 網站中可用的所有清單。  請注意，公告只有一個清單，名為 \[**公告**\]。  
  
3.  在 SharePoint 網頁的頂端，請選擇 \[**網站工作流程**\] 連結。  
  
4.  在 \[開始新工作流程\] 區段底下，選擇 \[**AnnouncementBackup \- Workflow1**\] 連結。  這會啟動網站工作流程，並執行自訂動作中的程式碼。  
  
5.  在快速啟動列，請選擇 \[**Announcements Backup**\] 連結。  請注意，\[**公告**\] 清單中包含的所有公告都已複製到這個新清單。  
  
## 請參閱  
 [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  