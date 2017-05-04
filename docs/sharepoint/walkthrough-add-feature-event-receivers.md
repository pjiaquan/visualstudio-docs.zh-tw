---
title: "逐步解說：新增功能事件接收器 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 開發, 進階封裝工具"
  - "Visual Studio 中的 SharePoint 開發, 事件接收器"
  - "Visual Studio 中的 SharePoint 開發, 功能事件接收器"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 逐步解說：新增功能事件接收器
  功能事件接收器是在 SharePoint 中發生下列其中一個與功能的相關事件時執行的方法：  
  
-   安裝功能。  
  
-   啟動功能。  
  
-   停用功能。  
  
-   移除功能。  
  
 本逐步解說示範如何將事件接收器加入至 SharePoint 專案中的功能。  其中將示範下列工作：  
  
-   建立具有功能事件接收器的空專案。  
  
-   處理 **FeatureDeactivating** 方法。  
  
-   使用 SharePoint 專案物件模型將公告加入至公告清單。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 建立功能事件接收器專案  
 首先，建立專案來包含功能事件接收器。  
  
#### 若要建立具有功能事件接收器的專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  在 \[**範本**\] 窗格中，選取 \[**SharePoint 2010 專案**\] 範本。  
  
     請為功能事件接收器使用此專案類型，因為它們沒有專案範本。  
  
4.  在 \[**名稱**\] 方塊中輸入 FeatureEvtTest，然後選擇 \[**確定**\] 按鈕以顯示 \[**SharePoint 自訂精靈**\]。  
  
5.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，輸入您想要加入新自訂欄位項目之 SharePoint 伺服器網站的 URL，或使用預設位置 \(http:\/\/\<*system name*\>\/\)。  
  
6.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，選擇 \[**部署為陣列方案**\] 選項按鈕。  
  
     如需沙箱化方案與陣列方案的比較的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  選擇 \[**結束**\] 按鈕，並注意名為 Feature1 的功能會出現在 \[**功能**\] 節點下。  
  
## 將事件接收器加入至功能  
 接下來，將事件接收器加入至功能，然後加入停用功能時執行的程式碼。  
  
#### 若要將事件接收器加入至功能  
  
1.  開啟功能節點的捷徑功能表，然後選取 \[**新增功能**\] 來建立功能。  
  
2.  在 \[**功能**\] 節點底下，開啟 \[**Feature1**\] 的捷徑功能表，然後選擇 \[**加入事件接收器**\] 將事件接收器加入至功能。  
  
     這會在 Feature1 底下加入程式碼檔。  在此範例中，檔案名稱會是 Feature1.EventReceiver.cs 或 Feature1.EventReceiver.vb，視專案的開發語言而定。  
  
3.  如果您的專案是以 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 撰寫，請將下列程式碼加入至事件接收器頂端 \(如果沒有的話\)：  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  事件接收器類別包含幾個設成註解的方法，其行為如同事件。  以下列程式碼取代 **FeatureDeactivating** 方法：  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## 測試功能事件接收器  
 接下來停用功能，以測試 **FeatureDeactivating** 方法是否會將公告輸出至 SharePoint 公告清單。  
  
#### 若要測試功能事件接收器  
  
1.  將專案的 \[**現用部署組態**\] 屬性值設定為 \[**不啟動**\]。  
  
     設定此屬性可防止功能在 SharePoint 中啟動，並讓您對功能事件接收器偵錯。  如需詳細資訊，請參閱[對 SharePoint 方案進行偵錯](../sharepoint/debugging-sharepoint-solutions.md)。  
  
2.  按 \[**F5**\] 鍵執行專案並將它部署至 SharePoint。  
  
3.  在 SharePoint 網頁的頂端，開啟 \[**網站動作**\] 功能表，然後選擇 \[**網站設定**\]。  
  
4.  在 \[**網站設定**\] 頁面的 \[**網站動作**\] 區段底下，選擇 \[**管理網站功能**\] 連結。  
  
5.  在 \[**網站功能**\] 頁面上，選擇 \[**FeatureEvtTest Feature1**\] 功能旁的 \[**啟動**\] 按鈕。  
  
6.  在 \[**功能**\] 頁面上，選擇 \[**FeatureEvtTest Feature1**\] 功能旁的 \[**停止**\] 按鈕，然後選擇 \[**停用這個功能**\] 確認連結停用功能。  
  
7.  選擇 \[**首頁**\] 按鈕。  
  
     請注意，在停用功能之後，一項公告會出現在 \[**公告**\] 清單中。  
  
## 請參閱  
 [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  