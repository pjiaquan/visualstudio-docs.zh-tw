---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  如果您要將功能加入至 Visual Studio 中已安裝的 SharePoint 專案項目時，請建立專案項目擴充功能。  如需詳細資訊，請參閱[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
### 若要建立專案項目擴充功能  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面的類別。  
  
4.  將下列屬性加入到類別：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 型別傳遞至屬性建構函式。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  在專案項目擴充功能中，此屬性會識別您要擴充的專案項目。  請將專案項目的 ID 傳遞至屬性建構函式。  專案項目所包含的Visual StudioId 的清單，請參閱[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法的實作中，使用 *projectItemType* 參數的成員來定義擴充功能的行為。  這個參數是 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 物件，可用來存取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 介面中定義的事件。  若要存取您要擴充的特定專案項目類型執行個體，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件，例如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## 範例  
 下列程式碼範例示範如何為 \[事件接收器\] 專案項目建立簡單的擴充功能。  每當使用者將 \[事件接收器\] 專案項目加入至 SharePoint 專案時，此擴充功能都會將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 此範例會使用 SharePoint 專案服務，將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  如需詳細資訊，請參閱 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  