---
title: "如何：建立事件接收器 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "事件接收器 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 事件接收器"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：建立事件接收器
  藉由建立 *事件接收器*，您可以在使用者與 SharePoint 項目 \(例如清單或清單項目時\) 互動時給予回應。  例如，當有人變更行事曆或從連絡人清單刪除姓名時，就會觸發事件接收器中的程式碼。  遵循這個主題，您可以學習如何將事件接收器加入至清單執行個體。  
  
 若要完成這些步驟，您必須安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 以及 Windows 和 SharePoint 的支援的版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  由於這個範例需要 SharePoint 專案，您也必須完成主題 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 的程序。  
  
## 加入事件接收器  
 您在 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 中建立的專案包含自訂網站欄、自訂清單和一個內容類型。  在下列程序中，您可以將簡單的事件處理常式 \(事件接收器\) 加入至清單執行個體，展開專案，並且顯示如何處理在 SharePoint 項目發生 \(例如清單\) 的事件。  
  
#### 若要將事件接收器加入至清單執行個體  
  
1.  開啟您在[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)中建立的專案。  
  
2.  在 \[**方案總管**\] 中，選取名為 \[**診斷所**\] 的 SharePoint 專案節點。  
  
3.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
4.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開的 \[**SharePoint**\] 節點，然後按一下 \[**2010**\] 項目。  
  
5.  在 \[**範本**\] 窗格中，選取 \[**事件接收器**\]，將其命名為 TestEventReceiver1，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
6.  在 \[**您要何種類型的事件接收器?**\] 清單中，選取 \[**清單項目事件**\]。  
  
7.  在 \[**哪些項目應為事件來源?**\] 清單中，選取 \[**患者 \(診斷所\\患者\)**\]。  
  
8.  在 \[**處理下列事件**\] 清單中，選取 \[**已加入一個項目**\] 旁的核取方塊，然後選擇 \[**結束**\] 按鈕。  
  
     新的事件接收器程式碼檔包含一個名為 `ItemAdded` 的方法。  在下一個步驟中，您會將程式碼加入至這個方法，根據預設，讓每個連絡人將名為 Scott Brown。  
  
9. 使用下列程式碼取代現有的 `ItemAdded` 方法，然後按 F5 鍵：  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     程式碼執行，然後 SharePoint 網站會出現在 Web 瀏覽器。  
  
10. 在快速啟動列，請選擇 \[**患者**\] 連結，然後選擇 \[**加入新項目**\] 連結。  
  
     新項目的資料表單開啟。  
  
11. 在欄位中輸入資料，然後選擇 \[**儲存**\] 按鈕。  
  
     選擇 \[**儲存**\] 按鈕後，\[**病患名稱**\] 資料行自動更新為 Scott Brown 名稱。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  