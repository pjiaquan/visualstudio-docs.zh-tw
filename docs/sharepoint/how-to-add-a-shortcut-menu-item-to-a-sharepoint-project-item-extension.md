---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  您可以使用專案項目擴充功能，將捷徑功能表項目加入至現有的 SharePoint 專案項目。  使用者在 \[**方案總管**\] 中以滑鼠右鍵按一下專案項目時，功能表項目就會出現。  
  
 下列步驟假設您已經建立專案項目擴充功能。  如需詳細資訊，請參閱 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### 若要在專案項目擴充功中加入捷徑功能表項目  
  
1.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法中，請處理 *projectItemType* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件的事件處理常式中，將新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件加入至事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合。  
  
3.  在新 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件處理常式中，執行在使用者按一下捷徑功能表項目時要執行的工作。  
  
## 範例  
 下列程式碼範例示範如何將捷徑功能表項目加入至 \[事件接收器\] 專案項目。  當使用者以滑鼠右鍵按一下 \[**方案總管**\] 中的專案項目，並且按一下 \[**將訊息寫入輸出視窗**\] 功能表項目時，Visual Studio 會在 \[**輸出**\] 視窗中顯示訊息。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 此範例使用 SharePoint 專案服務來將訊息寫入 \[**輸出**\] 視窗。  如需詳細資訊，請參閱 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 編譯程式碼  
 這個範例需要類別庫專案並參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  