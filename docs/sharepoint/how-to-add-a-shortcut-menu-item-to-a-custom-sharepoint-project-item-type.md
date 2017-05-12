---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  當您定義自訂 SharePoint 專案項目類型時，您可以將捷徑功能表項目加入至專案項目。  使用者在 \[**方案總管**\] 中以滑鼠右鍵按一下專案項目時，功能表項目就會出現。  
  
 下列步驟假設您已經定義自己的 SharePoint 專案項目型別。  如需詳細資訊，請參閱[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
### 若要將捷徑功能表項目加入至自訂專案項目類型  
  
1.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 實作之 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法中，請處理 *projectItemTypeDefinition* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件的事件處理常式中，將新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件加入至事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合。  
  
3.  在新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件處理常式中，執行您要執行的工作，當使用者選取的捷徑功能表項目時。  
  
## 範例  
 下列程式碼範例示範如何將內容功能表項目加入至自訂專案項目型別。  當使用者從開啟專案項目的捷徑功能表上 \[**方案總管**\] 並選取 \[**寫入訊息至輸出視窗**\] 功能表項目時， Visual Studio 會在 \[**輸出**\] 視窗的訊息。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 此範例使用 SharePoint 專案服務來將訊息寫入 \[**輸出**\] 視窗。  如需詳細資訊，請參閱[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 編譯程式碼  
 這個範例需要類別庫專案並參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署專案項目  
 若要讓其他開發人員使用您的專案項目，請建立專案範本或專案項目範本。  如需詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署專案項目，請針對組件、範本以及要與專案項目一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  