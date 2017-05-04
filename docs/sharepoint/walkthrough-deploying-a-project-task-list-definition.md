---
title: "逐步解說：部署專案工作清單定義 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 開發, 部署"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 逐步解說：部署專案工作清單定義
  以下示範如何使用 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 建立、自訂、偵錯和部署 SharePoint 清單定義，以便追蹤專案工作。  
  
 這個逐步解說將說明下列工作：  
  
-   [建立 SharePoint 清單](#CreatingListDef)。  
  
-   [建立 SharePoint 清單](#CreatingListDef)。  
  
-   [加入事件接收器](#AddEventRcvr)。  
  
-   [自訂專案工作清單功能](#CustomizeFeature)。  
  
-   [建置和測試專案工作清單](#BuildTest)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] 或某個 Visual Studio Application Lifecycle Management \(ALM\) 版本。  
  
##  <a name="CreatingListDef"></a> 建立 SharePoint 清單  
 建立 SharePoint 清單專案，並將清單定義與工作產生關聯。  
  
#### 若要建立 SharePoint 清單專案  
  
1.  開啟 \[**新增專案**\] 對話方塊，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
2.  在 \[**範本**\] 窗格中，選擇 \[**SharePoint 2010 專案**\] 範本，命名為 ProjectTaskList 然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
3.  指定您用於偵錯的本機 SharePoint 網站，選取 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**結束**\] 按鈕。  
  
4.  開啟這個專案的捷徑功能表，然後選擇 \[**加入**\]、\[**新項目**\]。  
  
5.  在 \[**範本**\] 窗格中，選擇 \[**清單**\] 範本，然後選擇 \[**加入**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
6.  在 \[**清單的顯示名稱?**\] 方塊中，輸入 Project Task List。  
  
7.  選取 \[**以現有清單類型建立非自訂的清單**\] 選項按鈕，然後在它的清單中選取 \[**工作**\]，然後選擇 \[**結束**\] 按鈕。  
  
     清單、功能和套件隨即出現在 \[**方案總管**\]。  
  
##  <a name="AddEventRcvr"></a> 加入事件接收器  
 在工作清單中，您可以加入事件接收器，以便自動設定工作的到期日和描述。  在下列程序中，會將簡單的事件處理常式加入至清單執行個體做為事件接收器。  
  
#### 若要加入事件接收器  
  
1.  開啟專案節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[**新項目**\]。  
  
2.  在 SharePoint 範本清單中，選取 \[**事件接收器**\] 範本，將它命名為 **ProjectTaskListEventReceiver**。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
3.  在 \[**選取事件接收器設定**\] 頁面上，選取 \[**清單項目事件**\] 做為 \[**選擇哪種類型的事件接收器**\] 清單的事件接收器類型。  
  
4.  在 \[**哪些項目應為事件來源?**\] 清單中，選取 \[**工作**\]。  
  
5.  在要處理的事件清單中，選取 \[**已加入一個項目**\] 旁的核取方塊，然後按一下 \[**完成**\] 按鈕。  
  
     如此隨即將新的事件接收器節點加入至專案，其中包含名為 **ProjectTaskListEventReceiver** 的程式碼檔。  
  
6.  將程式碼加入至 **ProjectTaskListEventReceiver** 程式碼檔中的 `ItemAdded` 方法。  每當加入新工作時，預設到期日和描述便會加入至該工作。  預設到期日為 2009 年 7 月 1 日。  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> 自訂專案工作清單功能  
 當您建立 SharePoint 方案時，Visual Studio 會自動為預設專案項目建立功能。  您可以使用「功能設計工具」自訂 SharePoint 網站的專案工作清單設定。  
  
#### 若要自訂專案工作清單功能  
  
1.  在 \[**方案總管**\] 中，展開 \[**功能**\]。  
  
2.  開啟 \[**Feature1**\] 的捷徑功能表，然後選擇 \[**檢視設計工具**\]。  
  
3.  在 \[**標題**\] 方塊中，輸入**專案工作清單功能**。  
  
4.  在 \[**範圍**\] 清單中，選擇 \[**網頁**\]。  
  
5.  在 \[**屬性**\] 視窗中，輸入 **1.0.0.0** 做為 \[**版本**\] 屬性的值。  
  
##  <a name="CustomizePackage"></a> 自訂專案工作清單套件  
 建立 SharePoint 專案時，Visual Studio 會自動將包含預設專案項目的功能加入至套件。  您可以使用封裝設計工具自訂 SharePoint 網站的專案工作清單設定。  
  
#### 若要自訂專案工作清單套件  
  
1.  在 \[**方案總管**\] 中，開啟 \[**封裝**\] 的捷徑功能表，然後選擇 \[**檢視設計工具**\]。  
  
2.  在 \[**名稱**\] 文字方塊中，輸入 **ProjectTaskListPackage**。  
  
3.  選取 \[**重設網頁伺服器**\] 核取方塊。  
  
##  <a name="BuildTest"></a> 建置和測試專案工作清單  
 執行專案時，SharePoint 網站會開啟。  不過，您必須手動巡覽至工作清單的位置。  
  
#### 若要測試專案工作清單  
  
1.  按 F5 鍵建置和部署專案工作清單。  
  
     SharePoint 網站隨即開啟。  
  
2.  選擇 \[**首頁**\] 索引標籤。  
  
3.  在左欄位，請選擇 \[**專案工作清單**\] 連結。  
  
     \[專案工作清單\] 頁面隨即出現。  
  
4.  在 \[**清單工具**\] 索引標籤上，選取 \[**項目**\] 選項。  
  
5.  在 \[**項目**\] 群組中，選擇 \[**新的項目**\] 按鈕。  
  
6.  在 \[**標題**\] 文字方塊中，輸入 Task1。  
  
7.  選取 \[**儲存**\] 按鈕。  
  
     重新整理網站之後，\[**Task1**\] 工作隨即出現，到期日為 2009 年 7 月 1 日。  
  
8.  選擇 **Task1**。  
  
     工作的詳細檢視隨即出現，說明顯示「這是要徑任務」。  
  
##  <a name="Deploy"></a> 部署專案工作清單  
 建置及測試專案工作清單後，您可以將它部署到「*本機系統*」\(Local System\) 或「*遠端系統*」\(Remote System\)。  本機系統是方案部署所在的同一部電腦，而遠端系統是另一部電腦。  
  
#### 若要將專案工作清單部署到本機系統  
  
1.  在 Visual Studio 功能表列上，選擇 \[**建置**\]、\[**部署方案**\]。  
  
     Visual Studio 會回收 IIS 應用程式集區、撤銷任何現有的方案版本、將方案套件 \(.wsp\) 檔複製到 SharePoint，然後啟動其功能。  現在您可以在 SharePoint 中使用方案。  如需部署組態的詳細資訊，請參閱 [如何：編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
#### 若要將專案工作清單部署到遠端系統  
  
1.  在 Visual Studio 功能表列上，選擇 \[**建置**\]、\[**發行**\]。  
  
2.  在 \[**發行**\] 對話方塊中，選取 \[**對檔案系統的發行**\] 選項按鈕。  
  
     您可以選擇省略按鈕 ![省略符號圖示](../sharepoint/media/ellipsisicon.png "省略符號圖示") 來變更 \[**發行**\] 對話方塊中的目標位置，然後巡覽至另一個位置。  
  
3.  選擇 \[**發行**\] 按鈕。  
  
     .wsp 檔案已為方案建立。  
  
4.  將這個 .wsp 檔複製到遠端系統。  
  
5.  使用 PowerShell `Add-SPUserSolution` 命令將套件安裝到遠端 SharePoint 安裝 \(若為陣列方案，請使用 `Add-SPSolution` 命令\)。  
  
     例如，`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`。  
  
6.  使用 PowerShell `Install-SPUserSolution` 命令部署方案 \(若為陣列方案，請使用 `Install-SPSolution` 命令\)。  
  
     例如，`Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`。  
  
     如需遠端部署的詳細資訊，請參閱 [使用方案](http://go.microsoft.com/fwlink/?LinkId=217680) 和 [在 SharePoint 2010 與 PowerShell 加入和部署方案](http://go.microsoft.com/fwlink/?LinkId=217682)。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解如何自訂和部署 SharePoint 方案：  
  
-   [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [SharePoint Server 2010 的 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  