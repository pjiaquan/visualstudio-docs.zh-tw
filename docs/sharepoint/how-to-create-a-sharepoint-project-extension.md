---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  如果您要將功能加入至 Visual Studio 中開啟的任何 SharePoint 專案，請建立專案擴充功能。  如需詳細資訊，請參閱[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
### 若要建立專案擴充功能  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面的類別。  
  
4.  將 <xref:System.ComponentModel.Composition.ExportAttribute> 加入至類別。  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 型別傳遞至屬性建構函式。  
  
5.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法實作中，使用 *projectService* 參數的成員來定義擴充功能的行為。  這個參數是 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件，可用來存取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 介面中定義的事件。  
  
## 範例  
 下列程式碼範例示範如何建立簡單的專案擴充功能，以處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 介面所定義的大部分 SharePoint 專案事件。  若要測試程式碼，請在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立 SharePoint 專案，然後將其他專案加入方案，變更專案屬性值，或者刪除或排除專案。  擴充功能會提供將訊息寫入 \[**輸出**\] 視窗或 \[**錯誤清單**\] 視窗，來通知您發生事件。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 此範例會使用 SharePoint 專案服務，將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  如需詳細資訊，請參閱 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 如需示範如何處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件的範例，請參閱 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)和 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  