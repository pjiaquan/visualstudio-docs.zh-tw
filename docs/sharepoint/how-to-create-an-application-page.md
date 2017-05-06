---
title: "如何：建立應用程式頁面"
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
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發], 加入"
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發], 建立"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：建立應用程式頁面
  您可以為一個或多個 SharePoint 網站建立 ASP.NET 網頁。  在 SharePoint 中，這些網頁稱為應用程式頁面，  與網站頁面不同之處在於，應用程式頁面中包含在頁面背後執行的程式碼。  如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
### 若要建立應用程式頁面  
  
1.  在Visual Studio中，開啟或建立 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 \[**方案總管**\] 中選擇專案節點。  
  
3.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
4.  在 \[**加入新項目**\] 對話方框中展開 \[**SharePoint**\] 節點，接著選取 \[**2010**\] 項目。  
  
5.  在 SharePoint 範本清單中，選取 \[**應用程式頁面**\]。  
  
6.  在 \[**名稱**\] 方塊中指定應用程式頁面的名稱，然後選擇 \[**加入**\] 按鈕。  
  
     Visual Studio 會將數個資料夾和檔案加入至您的專案。  如需這些檔案的詳細資訊，請參閱 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
     在 Visual Web 發展設計工具的 \[**來源**\] 檢視中，會顯示 ASP.NET 頁面檔案。  您可以從 \[**工具箱**\] 加入控制項，並將它們放置在內容預留位置上，來設計頁面。  如需詳細資訊，請參閱[網頁設計工具、原始碼檢視](http://msdn.microsoft.com/zh-tw/5911396b-fe51-4150-9ff1-b085f812862f)。  
  
7.  若要處理控制項事件，請將程式碼加入至應用程式頁面的程式碼檔案。  
  
     程式碼檔案會根據專案的語言，出現並展開 ASP.NET 網頁檔案的節點，其副檔名為 .cs 或 .vb。  如需建立應用程式頁面的詳細範例，請參閱 [逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)。  
  
## 請參閱  
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  