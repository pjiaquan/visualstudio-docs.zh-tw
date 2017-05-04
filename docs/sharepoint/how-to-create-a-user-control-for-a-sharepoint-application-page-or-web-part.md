---
title: "如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項 | Microsoft Docs"
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
  - "使用者控制項 [Visual Studio 中的 SharePoint 開發], 加入"
  - "使用者控制項 [Visual Studio 中的 SharePoint 開發], 建立"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項
  您可以建立提供針對 SharePoint 方案自訂功能的自訂使用者控制項，然後您可以重複使用在專案內的該功能。  您可以將 Web 組件或應用程式網頁加入使用者控制項，或加入其他 ASP.NET 控制項和 SharePoint 控制項或定義屬性和控制的方法。  如需使用者控制項的詳細資訊，請參閱 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) 和 [使用者控制項和伺服器控制項在 SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx)。  
  
### 若要建立 SharePoint 的使用者控制項  
  
1.  在Visual Studio中，開啟或建立 SharePoint 專案。  
  
     請參閱 [SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 \[**方案總管**\] 中選擇專案節點。  
  
3.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即開啟。  
  
4.  在 \[**安裝**\] 窗格中，選取 \[**Office SharePoint\/**\] 節點。  
  
5.  在 SharePoint 範本清單中，選取 \[**使用者控制項 \(僅限陣列方案\)**\]。  
  
    > [!NOTE]  
    >  使用者控制項在陣列方案才有作用。  
  
6.  在 \[**名稱**\] 方塊中指定使用者控制項的名稱，然後選擇 \[**加入**\] 按鈕。  
  
     Visual Studio 會將數個資料夾和檔案加入至您的專案。  如需這些檔案的詳細資訊，請參閱 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
     根據預設，使用者控制項檔案會出現在 Visual Web Developer 設計工具的 \[**原始碼**\] 檢視中。  在這個視窗中，您可以編輯控制項中的 XML 標記。  如果您想要從 \[**工具箱**\] 中拖曳控制項，以便以視覺化的方式設計控制項，您可以切換為 \[**設計**\] 檢視。  請參閱 [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/zh-tw/d8f2270a-357d-40a4-9b39-1a3f2366216d)。  
  
7.  如果您想要處理在控制項中發生的事件，對使用者控制項程式碼檔案中加入程式碼。  
  
     這個檔案會出現在 \[**方案總管**\] 的使用者控制項檔案下並擁有 .cs 或 .vb 副檔名，視專案的語言而定。  
  
## 請參閱  
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  